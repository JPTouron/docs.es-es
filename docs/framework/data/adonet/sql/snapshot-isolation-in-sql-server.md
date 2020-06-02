---
title: Aislamiento de instantáneas en SQL Server
description: Lea información general sobre el aislamiento de instantáneas y las versiones de fila en SQL Server y aprenda a administrar la simultaneidad con niveles de aislamiento.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
ms.openlocfilehash: 7fa769448dd922925a5eccf4c85bd1840155df68
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286254"
---
# <a name="snapshot-isolation-in-sql-server"></a>Aislamiento de instantáneas en SQL Server
El aislamiento de instantánea mejora la simultaneidad de las aplicaciones OLTP.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Descripción del aislamiento de instantáneas y la versión de fila  
 Una vez habilitado el aislamiento de instantánea, se deben mantener las versiones de fila actualizadas para cada transacción.  Antes de SQL Server 2019, estas versiones se almacenaban en **tempdb**. SQL Server 2019 presenta una nueva característica, una recuperación de base de datos acelerada (ADR) que requiere su propio conjunto de versiones de fila.  Por tanto, a partir de SQL Server 2019, si ADR no está habilitado, las versiones de fila se mantienen en **tempdb** como siempre.  Si el ADR está habilitado, todas las versiones de fila, relacionadas con el aislamiento de instantáneas y la ADR, se mantienen en el almacén de versiones persistente (PVS) de ADR, que se encuentra en la base de datos de usuario de un grupo de archivos que el usuario especifica. Un número de secuencia de transacción único identifica cada transacción, y estos números únicos se registran para cada versión de fila. La transacción funciona con las versiones de fila más recientes que tienen un número de secuencia antes del número de secuencia de transacción. La transacción omite las versiones de fila más recientes creadas después de que se haya iniciado la transacción.  
  
 El término "instantánea" refleja el hecho de que todas las consultas de la transacción ven la misma versión, o instantánea, de la base de datos, en función del estado de la base de datos en el momento en que se inicia la transacción. En una transacción de instantánea no se adquieren bloqueos en las filas o las páginas de datos subyacentes, lo que permite que se ejecuten otras transacciones sin que una transacción anterior sin completarse las bloquee. Las transacciones que modifican datos no bloquean las transacciones que leen datos, y las transacciones que leen datos no bloquean las transacciones que escriben datos, como ocurre normalmente en el nivel de aislamiento READ COMMITTED predeterminado de SQL Server. Este comportamiento de no bloqueo también reduce notablemente la probabilidad de que se produzcan interbloqueos en las transacciones complejas.  
  
 El aislamiento de instantánea utiliza un modelo de simultaneidad optimista. Si una transacción de instantánea intenta confirmar modificaciones en los datos que han cambiado desde que se inició la transacción, esta se revertirá y se producirá un error. Puede evitarlo usando sugerencias UPDLOCK para las instrucciones SELECT que tienen acceso a los datos que se van a modificar. Visite el artículo "Sugerencias de bloqueo" de Libros en pantalla de SQL Server para obtener más información.  
  
 El aislamiento de instantánea se debe habilitar estableciendo la opción ALLOW_SNAPSHOT_ISOLATION en ON en la base de datos antes de que se utilice en las transacciones. Con esto se activa el mecanismo para almacenar versiones de fila en la base de datos temporal (**tempdb**). Debe habilitar el aislamiento de instantánea en cada base de datos en que se utilice con la instrucción ALTER DATABASE de Transact-SQL. En este sentido, el aislamiento de instantánea difiere de los niveles de aislamiento tradicionales de READ COMMITTED, REPEATABLE READ, SERIALIZABLE y READ UNCOMMITTED, que no requieren ninguna configuración. Las siguientes instrucciones activan el aislamiento de instantánea y reemplazan el comportamiento READ COMMITTED predeterminado por SNAPSHOT:  
  
```sql  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
 Al establecer la opción READ_COMMITTED_SNAPSHOT ON, se permite el acceso a las filas con versión en el nivel de aislamiento READ COMMITTED predeterminado. Si la opción READ_COMMITTED_SNAPSHOT está establecida en OFF, debe establecer explícitamente el nivel de aislamiento de instantánea en cada sesión con el fin de acceder a las filas con versiones.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Administración de simultaneidad con niveles de aislamiento  
 El nivel de aislamiento en el que se ejecuta una instrucción Transact-SQL determina su bloqueo y el comportamiento de las versiones de fila. Un nivel de aislamiento tiene definido el ámbito en toda la conexión y, una vez que se establece en una conexión con la instrucción SET TRANSACTION ISOLATION LEVEL, continúa activo hasta que se cierra la conexión o se establece otro nivel de aislamiento. Cuando se cierra una conexión y se devuelve al grupo, se conserva el nivel de aislamiento de la última instrucción SET TRANSACTION ISOLATION LEVEL. Las conexiones posteriores que reutilizan una conexión agrupada usan el nivel de aislamiento que estaba activo en el momento en que se agrupó la conexión.  
  
 Las consultas individuales emitidas en una conexión pueden contener sugerencias de bloqueo que modifiquen el aislamiento de una única instrucción o transacción, pero no afectan al nivel de aislamiento de la conexión. Los niveles de aislamiento o las sugerencias de bloqueo que se establecen en procedimientos almacenados o funciones no cambian el nivel de aislamiento de la conexión que los llama y solo están activos mientras dure el procedimiento almacenado o la llamada a la función.  
  
 En las versiones anteriores de SQL Server se admitían cuatro niveles de aislamiento definidos en el estándar SQL-92:  
  
- READ UNCOMMITTED es el nivel de aislamiento menos restrictivo porque omite los bloqueos colocados por otras transacciones. Las transacciones que se ejecutan en READ UNCOMMITTED pueden leer valores de datos modificados que aún no han confirmado otras transacciones; estas se denominan lecturas de datos "sucios".  
  
- READ COMMITTED es el nivel de aislamiento predeterminado de SQL Server. Impide las lecturas de datos sucios especificando que las instrucciones no pueden leer valores de datos modificados, pero aún no confirmados por otras transacciones. Otras transacciones pueden seguir modificando, insertando o eliminando datos entre ejecuciones de instrucciones específicas dentro de la transacción actual, lo que da lugar a lecturas no repetibles o datos "fantasma".  
  
- REPEATABLE READ es un nivel de aislamiento más restrictivo que READ COMMITTED. Engloba READ COMMITTED y especifica, además, que ninguna otra transacción puede modificar o eliminar los datos leídos por la transacción actual hasta que esta se confirme. La simultaneidad es menor que en READ COMMITTED porque los bloqueos compartidos en los datos de lectura se mantienen mientras dure la transacción, en lugar de liberarse al final de cada instrucción.  
  
- SERIALIZABLE es el nivel de aislamiento más restrictivo, porque bloquea intervalos de claves completos y mantiene esos bloqueos hasta que la transacción finaliza. Engloba REPEATABLE READ y agrega la restricción de que otras transacciones no pueden insertar nuevas filas en intervalos leídos por la transacción hasta que se complete la transacción.  
  
 Para obtener más información, vea la [Guía de versiones de fila y bloqueo de transacciones](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide).  
  
### <a name="snapshot-isolation-level-extensions"></a>Extensiones del nivel de aislamiento de instantáneas  
 SQL Server ha incorporado extensiones a los niveles de aislamiento SQL-92 con la presentación del nivel de aislamiento SNAPSHOT y una implementación adicional de READ COMMITTED. El nivel de aislamiento READ_COMMITTED_SNAPSHOT puede sustituir de forma transparente a READ COMMITTED en todas las transacciones.  
  
- El aislamiento SNAPSHOT especifica que los datos leídos en una transacción nunca reflejarán los cambios realizados por otras transacciones simultáneas. La transacción utiliza las versiones de fila de datos que existen cuando se inicia la transacción. No se aplican bloqueos a los datos cuando se leen, por lo que las transacciones SNAPSHOT no impiden que otras transacciones escriban datos. Las transacciones que escriben datos no bloquean la lectura de datos de las transacciones de tipo SNAPSHOT. Debe habilitar el aislamiento de instantánea estableciendo la opción de base de datos ALLOW_SNAPSHOT_ISOLATION para poder usarlo.  
  
- La opción de base de datos READ_COMMITTED_SNAPSHOT determina el comportamiento del nivel de aislamiento READ COMMITTED predeterminado cuando el aislamiento de instantánea está habilitado en una base de datos. Si no especifica explícitamente READ_COMMITTED_SNAPSHOT en ON, READ COMMITTED se aplica a todas las transacciones implícitas. Esto produce el mismo comportamiento que si se establece READ_COMMITTED_SNAPSHOT en OFF (el valor predeterminado). Cuando READ_COMMITTED_SNAPSHOT OFF está en vigor, el Motor de base de datos utiliza bloqueos compartidos para aplicar el nivel de aislamiento predeterminado. Si establece la opción de base de datos READ_COMMITTED_SNAPSHOT en ON, el Motor de base de datos utilizará las versiones de fila y el aislamiento de instantánea de forma predeterminada, en lugar de usar bloqueos para proteger los datos.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Cómo funcionan el aislamiento de instantáneas y la versión de fila  
 Cuando se habilita el nivel de aislamiento SNAPSHOT, cada vez que se actualiza una fila, el motor de base de datos de SQL Server almacena una copia de la fila original en **tempdb** y agrega un número de secuencia de transacción a la fila. A continuación se presenta la secuencia de eventos que se produce:  
  
- Se inicia una nueva transacción y se le asigna un número de secuencia de transacción.  
  
- El motor de base de datos lee una fila de la transacción y recupera la versión de fila de **tempdb** cuyo número de secuencia se aproxima más a, y es inferior a, el número de la secuencia de transacción.  
  
- El Motor de base de datos comprueba si el número de secuencia de transacción no está en la lista de números de secuencia de transacción de las transacciones no confirmadas activas cuando se inició la transacción de instantánea.  
  
- La transacción lee la versión de la fila de **tempdb** que era la actual al inicio de la transacción. Esta no verá las nuevas filas insertadas una vez iniciada la transacción porque esos valores de número de secuencia serán mayores que el valor del número de secuencia de transacción.  
  
- La transacción actual ve las filas que se han eliminado tras su inicio, porque hay una versión de fila en **tempdb** con un valor de número de secuencia inferior.  
  
 El efecto real del aislamiento de instantánea es que la transacción ve todos los datos tal como se encontraban en el inicio de la transacción, sin tener en cuenta ni colocar los bloqueos en las tablas subyacentes. Esta acción mejorar el rendimiento en situaciones en las que hay contención.  
  
 Una transacción de instantánea siempre utiliza el control de simultaneidad optimista, que retiene los bloqueos que impiden que otras transacciones actualicen las filas. Si una transacción de instantánea intenta confirmar una actualización en una fila que se cambió una vez iniciada la transacción, la transacción se revierte y se produce un error.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>Trabajo con aislamiento de instantáneas en ADO.NET  
 La clase <xref:System.Data.SqlClient.SqlTransaction> admite el aislamiento de instantánea en ADO.NET. Si se ha habilitado en una base de datos el aislamiento de instantánea pero no se ha configurado como READ_COMMITTED_SNAPSHOT ON, debe iniciar una <xref:System.Data.SqlClient.SqlTransaction> mediante el valor de enumeración **IsolationLevel.Snapshot** cuando llame al método <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A>. En este fragmento de código se da por hecho que la conexión es un objeto <xref:System.Data.SqlClient.SqlConnection> abierto.  
  
```vb  
Dim sqlTran As SqlTransaction = _  
  connection.BeginTransaction(IsolationLevel.Snapshot)  
```  
  
```csharp  
SqlTransaction sqlTran =
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo se comportan los distintos niveles de aislamiento intentando acceder a los datos bloqueados; no está diseñado para usarse en el código de producción.  
  
 El código conecta a la base de datos de ejemplo **AdventureWorks** de SQL Server, crea una tabla denominada **TestSnapshot** e inserta una fila de datos. El código usa la instrucción ALTER DATABASE de Transact-SQL para activar el aislamiento de instantánea en la base de datos, pero no establece la opción READ_COMMITTED_SNAPSHOT, lo que deja activo el comportamiento del nivel de aislamiento READ COMMITTED predeterminado. El código realiza las siguientes acciones:  
  
- Inicia sqlTransaction1 sin completarla, que usa el nivel de aislamiento SERIALIZABLE para iniciar una transacción de actualización. Con esto, se bloquea la tabla.  
  
- Se abre una segunda conexión y se inicia una segunda transacción con el nivel de aislamiento SNAPSHOT para leer los datos de la tabla **TestSnapshot**. Dado que el aislamiento de instantánea está habilitado, esta transacción puede leer los datos que existían antes de que se iniciara sqlTransaction1.  
  
- Se abre una tercera conexión y se inicia una transacción con el nivel de aislamiento READ COMMITTED para intentar leer los datos de la tabla. En este caso, el código no puede leer los datos porque no puede leer más allá de los bloqueos colocados en la tabla en la primera transacción y se agota el tiempo de espera. Se produciría el mismo resultado si se utilizaran los niveles de aislamiento REPEATable READ y SERIALIZABLE, ya que estos niveles de aislamiento tampoco pueden leer más allá de los bloqueos colocados en la primera transacción.  
  
- Se abre una cuarta conexión y se inicia una transacción con el nivel de aislamiento READ UNCOMMITTED, que realiza una lectura de datos sucios del valor sin confirmar en sqlTransaction1. Este valor nunca puede existir realmente en la base de datos si la primera transacción no se confirma.  
  
- Se revierte la primera transacción y se procede a una limpieza con la eliminación de la tabla **TestSnapshot** y la desactivación del aislamiento de instantánea en la base de datos **AdventureWorks**.  
  
> [!NOTE]
> En los ejemplos siguientes se usa la misma cadena de conexión con la agrupación de conexiones desactivada. Si una conexión se agrupa, al restablecer su nivel de aislamiento no se restablece el nivel de aislamiento en el servidor. Como resultado, las conexiones posteriores que usan la misma conexión interna agrupada se inician con sus niveles de aislamiento establecidos en el de la conexión agrupada. Una alternativa a desactivar la agrupación de conexiones es establecer el nivel de aislamiento explícitamente en cada conexión.  
  
 [!code-csharp[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/VB/source.vb#1)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el comportamiento del aislamiento de instantánea cuando se modifican los datos. El código realiza las siguientes acciones:  
  
- Conecta a la base de datos de ejemplo **AdventureWorks** y habilita el aislamiento SNAPSHOT.  
  
- Crea una tabla denominada **TestSnapshotUpdate** e inserta tres filas de datos de ejemplo.  
  
- Inicia sqlTransaction1 sin completarla, mediante el aislamiento SNAPSHOT. En la transacción se seleccionan tres filas de datos.  
  
- Crea una segunda **SqlConnection** a **AdventureWorks** y crea una segunda transacción con el nivel de aislamiento READ COMMITTED que actualiza un valor de una de las filas seleccionadas en sqlTransaction1.  
  
- Confirma sqlTransaction2.  
  
- Vuelve a sqlTransaction1 e intenta actualizar la misma fila que sqlTransaction1 ya confirmó. Se produce el error 3960 y sqlTransaction1 se revierte automáticamente. **SqlException.Number** y **SqlException.Message** se muestran en la ventana Consola.  
  
- Ejecuta el código de limpieza para desactivar el aislamiento de instantánea en **AdventureWorks** y eliminar la tabla **TestSnapshotUpdate**.  
  
 [!code-csharp[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/VB/source.vb#1)]  
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Uso de sugerencias de bloqueo con aislamiento de instantáneas  
 En el ejemplo anterior, la primera transacción selecciona los datos, y una segunda transacción actualiza los datos antes de que se pueda completar la primera, lo que provoca un conflicto de actualización cuando la primera transacción intenta actualizar la misma fila. Puede reducir la posibilidad de conflictos de actualización en transacciones de instantánea de ejecución prolongada proporcionando sugerencias de bloqueo al inicio de la transacción. La siguiente instrucción SELECT usa la sugerencia UPDLOCK para bloquear las filas seleccionadas:  
  
```sql  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
 Al usar la sugerencia de bloqueo UPDLOCK, se bloquean las filas que intentan actualizar las filas antes de que se complete la primera transacción. Esto garantiza que las filas seleccionadas no tengan conflictos cuando se actualicen posteriormente en la transacción. Consulte el artículo "Sugerencias de bloqueo" en Libros en pantalla de SQL Server.  
  
 Si la aplicación tiene muchos conflictos, es posible que el aislamiento de instantánea no sea la mejor opción. Las sugerencias solo deben usarse cuando realmente se necesite. La aplicación no debe estar diseñada para que funcionen dependiendo constantemente de las sugerencias de bloqueo.  
  
## <a name="see-also"></a>Consulte también

- [SQL Server y ADO.NET](index.md)
- [Información general de ADO.NET](../ado-net-overview.md)
- [Guía de versiones de fila y bloqueo de transacciones](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide)

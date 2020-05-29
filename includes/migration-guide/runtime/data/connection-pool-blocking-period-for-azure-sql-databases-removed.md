---
ms.openlocfilehash: 4a60f4b135d5710ad0cc4900337e2970ffb8dd58
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2020
ms.locfileid: "83435410"
---
### <a name="connection-pool-blocking-period-for-azure-sql-databases-is-removed"></a>Se ha quitado el período de bloqueo del grupo de conexiones para Azure SQL Database

|   |   |
|---|---|
|Detalles|A partir de .NET Framework 4.6.2, para las solicitudes de apertura de conexión a instancias de Azure SQL Database conocidas (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), se ha quitado el período de bloqueo del grupo de conexiones y los errores de apertura de conexiones no se almacenan en caché. Se llevarán a cabo intentos por recuperar solicitudes abiertas de conexión casi inmediatamente después de los errores de conexión transitorios. Este cambio permite que el intento de apertura de conexión a instancias de Azure SQL Database se reintente de inmediato, lo que mejora el rendimiento de las aplicaciones habilitadas para la nube. Para todos los otros intentos de conexión, se sigue aplicando el período de bloqueo del grupo de conexiones.<p/>En .NET Framework 4.6.1 y versiones anteriores, cuando una aplicación encuentra un error de conexión transitorio al conectarse a una base de datos, no es posible reintentar rápidamente la conexión, porque el grupo de conexiones almacena el error en caché y vuelve a generarlo entre cinco segundos y un minuto. Para obtener más información, vea [Agrupación de conexiones de SQL Server (ADO.NET)](~/docs/framework/data/adonet/sql-server-connection-pooling.md). Este comportamiento causa problemas en las conexiones a bases de datos SQL de Azure, las que habitualmente presentan errores transitorios de los que se recuperan dentro de unos pocos segundos. La característica de bloqueo del grupo de conexiones significa que la aplicación no se puede conectar a la base de datos durante un período prolongado, incluso si la base de datos está disponible y la aplicación tiene que representarse en cuestión de segundos.|
|Sugerencia|Si no quiere este comportamiento, se puede configurar el período de bloqueo del grupo de conexiones si se establece la propiedad <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> introducida en .NET Framework 4.6.2. El valor de la propiedad es un miembro de la enumeración <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=name> que puede tener cualquiera de los tres valores:<ul><li><xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.Auto></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock></li></ul>El comportamiento anterior se puede restaurar al establecer la propiedad <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> en <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>.|
|Ámbito|Secundaria|
|Versión|4.6.2|
|Tipo|Tiempo de ejecución|
|API afectadas|<ul><li><xref:System.Data.Common.DbConnection.OpenAsync?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|

---
title: Colecciones de esquemas de SQL Server
ms.date: 03/30/2017
ms.assetid: c6403cc3-d78b-4f85-bab1-ada7a3446ec5
ms.openlocfilehash: ebb0cea20aede3d04e37536c7c615678e109337a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197669"
---
# <a name="sql-server-schema-collections"></a>Colecciones de esquemas de SQL Server

El proveedor de datos .NET Framework para SQL Server de Microsoft admite colecciones de esquemas adicionales, además de las colecciones de esquemas comunes. Las colecciones de esquemas varían ligeramente respecto de la versión de SQL Server que está utilizando. Para determinar la lista de colecciones de esquemas admitidas, llame al método **GetSchema** sin argumentos o con el nombre de la colección de esquemas "MetaDataCollections". Esto devolverá una <xref:System.Data.DataTable> con una lista de colecciones de esquemas admitidas, el número de restricciones que admite cada una y el número de partes de identificador que emplean.  
  
## <a name="databases"></a>Bases de datos  
  
|ColumnName|DataType|Descripción|  
|----------------|--------------|-----------------|  
|database_name|String|Nombre de la base de datos.|  
|dbid|Int16|Id. de la base de datos.|  
|create_date|DateTime|Fecha de creación de la base de datos.|  
  
## <a name="foreign-keys"></a>Claves externas  
  
|ColumnName|DataType|Descripción|  
|----------------|--------------|-----------------|  
|CONSTRAINT_CATALOG|String|Catálogo al que pertenece la restricción.|  
|CONSTRAINT_SCHEMA|String|Esquema que contiene la restricción.|  
|CONSTRAINT_NAME|String|Name (Nombre).|  
|TABLE_CATALOG|String|Nombre de la tabla de la que forma parte la restricción.|  
|TABLE_SCHEMA|String|Esquema que contiene la tabla.|  
|TABLE_NAME|String|Nombre de la tabla|  
|CONSTRAINT_TYPE|String|Tipo de restricción. Sólo se permite "FOREIGN KEY".|  
|IS_DEFERRABLE|String|Especifica si la restricción es aplazable. Devuelve NO.|  
|INITIALLY_DEFERRED|String|Especifica si la restricción es inicialmente aplazable. Devuelve NO.|  
  
## <a name="indexes"></a>Índices  
  
|ColumnName|DataType|Descripción|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|Catálogo al que pertenece el índice.|  
|constraint_schema|String|Esquema que contiene el índice.|  
|constraint_name|String|Nombre del índice.|  
|table_catalog|String|Nombre de la tabla con la que está asociado el índice.|  
|table_schema|String|Esquema que contiene la tabla con la que está asociado el índice.|  
|table_name|String|Nombre de la tabla.|  
|index_name|String|Nombre del índice.|  
  
### <a name="indexes-sql-server-2008"></a>Índices (SQL Server 2008)  

 Desde .NET Framework 3.5 Service Pack 1 y SQL Server 2008, se han agregado las columnas siguientes a la colección de esquemas Indexes para admitir nuevas columnas de tipos espaciales, de secuencia de archivos y dispersas. Estas columnas no se admiten en versiones anteriores de .NET Framework y SQL Server.  
  
|ColumnName|DataType|Descripción|  
|----------------|--------------|-----------------|  
|type_desc|String|El tipo de índice debe ser uno de los valores siguientes:<br /><br /> -MONTÓN<br />-AGRUPAdo<br />-Nonclustered<br />-XML<br />-ESPACIAL|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|ColumnName|DataType|Descripción|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|Catálogo al que pertenece el índice.|  
|constraint_schema|String|Esquema que contiene el índice.|  
|constraint_name|String|Nombre del índice.|  
|table_catalog|String|Nombre de la tabla con la que está asociado el índice.|  
|table_schema|String|Esquema que contiene la tabla con la que está asociado el índice.|  
|table_name|String|Nombre de la tabla.|  
|column_name|String|Nombre de la columna con la que está asociado el índice.|  
|ordinal_position|Int32|Posición ordinal de la columna.|  
|KeyType|Byte|Tipo del objeto.|  
|index_name|String|Nombre del índice.|  
  
## <a name="procedures"></a>Procedimientos  
  
|ColumnName|DataType|Descripción|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|Nombre específico del catálogo.|  
|SPECIFIC_SCHEMA|String|Nombre específico del esquema.|  
|SPECIFIC_NAME|String|Nombre específico del catálogo.|  
|ROUTINE_CATALOG|String|Catálogo al que pertenece el procedimiento almacenado.|  
|ROUTINE_SCHEMA|String|Esquema que contiene el procedimiento almacenado.|  
|ROUTINE_NAME|String|Nombre del procedimiento almacenado.|  
|ROUTINE_TYPE|String|Devuelve PROCEDURE en el caso de los procedimientos almacenados y FUNCTION en el caso de las funciones.|  
|CREATED|DateTime|Hora a la que se creó el procedimiento.|  
|LAST_ALTERED|DateTime|La última vez que se modificó el procedimiento.|  
  
## <a name="procedure-parameters"></a>Parámetros de procedimiento  
  
|ColumnName|DataType|Descripción|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|Nombre de catálogo del procedimiento del que forma parte este parámetro.|  
|SPECIFIC_SCHEMA|String|Esquema que contiene el procedimiento del que forma parte este parámetro.|  
|SPECIFIC_NAME|String|Nombre del procedimiento del que forma parte este parámetro.|  
|ORDINAL_POSITION|Int32|Posición ordinal del parámetro que empieza en 1. Para el valor devuelto de un procedimiento, es un 0.|  
|PARAMETER_MODE|String|Devuelve IN si es un parámetro de entrada, OUT si es un parámetro de salida e INOUT si es un parámetro de entrada/salida.|  
|IS_RESULT|String|Devuelve YES si indica que el resultado del procedimiento es una función. De lo contrario, devuelve NO.|  
|AS_LOCATOR|String|Devuelve YES si se ha declarado como localizador. De lo contrario, devuelve NO.|  
|PARAMETER_NAME|String|Nombre del parámetro. NULL si corresponde al valor devuelto de una función.|  
|DATA_TYPE|String|Tipo de datos proporcionado por el sistema.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Longitud máxima en caracteres de los tipos de datos binarios o de caracteres. De lo contrario, devuelve NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Longitud máxima, en bytes, de los tipos de datos binarios o de caracteres. De lo contrario, devuelve NULL.|  
|COLLATION_CATALOG|String|Nombre de catálogo de la intercalación del parámetro. Si no es de uno de los tipos de carácter, devuelve NULL.|  
|COLLATION_SCHEMA|String|Siempre devuelve NULL.|  
|COLLATION_NAME|String|Nombre de la intercalación del parámetro. Si no es de uno de los tipos de carácter, devuelve NULL.|  
|CHARACTER_SET_CATALOG|String|Nombre del catálogo del juego de caracteres del parámetro. Si no es de uno de los tipos de carácter, devuelve NULL.|  
|CHARACTER_SET_SCHEMA|String|Siempre devuelve NULL.|  
|CHARACTER_SET_NAME|String|Nombre del juego de caracteres del parámetro. Si no es de uno de los tipos de carácter, devuelve NULL.|  
|NUMERIC_PRECISION|Byte|Precisión de los datos numéricos aproximados, datos numéricos exactos, datos enteros o datos monetarios. De lo contrario, devuelve NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Base de la precisión de datos numéricos aproximados, datos numéricos exactos, datos enteros o datos monetarios. De lo contrario, devuelve NULL.|  
|NUMERIC_SCALE|Int32|Escala de datos numéricos aproximados, datos numéricos exactos, datos enteros o datos monetarios. De lo contrario, devuelve NULL.|  
|DATETIME_PRECISION|Int16|Precisión en segundos decimales si el tipo de parámetro es datetime o smalldatetime. De lo contrario, devuelve NULL.|  
|INTERVAL_TYPE|String|NULL. Reservado por SQL Server para uso futuro.|  
|INTERVAL_PRECISION|Int16|NULL. Reservado por SQL Server para uso futuro.|  
  
## <a name="tables"></a>Tablas  
  
|ColumnName|DataType|Descripción|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Catálogo de la tabla.|  
|TABLE_SCHEMA|String|Esquema que contiene la tabla.|  
|TABLE_NAME|String|Nombre de la tabla.|  
|TABLE_TYPE|String|Tipo de tabla. Puede ser VIEW o BASE TABLE.|  
  
## <a name="columns"></a>Columnas  
  
|ColumnName|DataType|Descripción|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Catálogo de la tabla.|  
|TABLE_SCHEMA|String|Esquema que contiene la tabla.|  
|TABLE_NAME|String|Nombre de la tabla.|  
|COLUMN_NAME|String|Nombre de la columna.|  
|ORDINAL_POSITION|Int32|Número de identificación de la columna.|  
|COLUMN_DEFAULT|String|Valor predeterminado de la columna.|  
|IS_NULLABLE|String|Nulabilidad de la columna. Si esta columna permite NULL, devuelve YES. De lo contrario, devuelve NO.|  
|DATA_TYPE|String|Tipo de datos proporcionado por el sistema.|  
|CHARACTER_MAXIMUM_LENGTH|Int32 – Sql8, Int16 – Sql7|Longitud máxima, en caracteres, de los datos binarios, de caracteres, o de texto e imagen. En caso contrario se devuelve NULL.|  
|CHARACTER_OCTET_LENGTH|Int32 – SQL8, Int16 – Sql7|Longitud máxima, en bytes, para datos binarios, datos de caracteres o datos de texto e imagen. En caso contrario se devuelve NULL.|  
|NUMERIC_PRECISION|Byte sin signo|Precisión de los datos numéricos aproximados, datos numéricos exactos, datos enteros o datos monetarios. En caso contrario se devuelve NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Base de la precisión de datos numéricos aproximados, datos numéricos exactos, datos enteros o datos monetarios. En caso contrario se devuelve NULL.|  
|NUMERIC_SCALE|Int32|Escala de datos numéricos aproximados, datos numéricos exactos, datos enteros o datos monetarios. En caso contrario se devuelve NULL.|  
|DATETIME_PRECISION|Int16|Código de subtipo para los tipos de datos interval de SQL-92 y datetime. Para los demás tipos de datos, se devuelve NULL.|  
|CHARACTER_SET_CATALOG|String|Devuelve Master, para indicar la base de datos en la que se encuentra el juego de caracteres, si la columna es del tipo de datos de caracteres o de texto. En caso contrario se devuelve NULL.|  
|CHARACTER_SET_SCHEMA|String|Siempre devuelve NULL.|  
|CHARACTER_SET_NAME|String|Devuelve el nombre único del juego de caracteres si esta columna es del tipo de datos de caracteres o de texto. En caso contrario se devuelve NULL.|  
|COLLATION_CATALOG|String|Devuelve Master, para indicar la base de datos en la que se define la intercalación, si la columna es del tipo de datos de caracteres o de texto. De lo contrario, esta columna es NULL.|  
  
### <a name="columns-sql-server-2008"></a>Columns (SQL Server 2008)  

 A partir de .NET Framework versión 3.5 Service Pack 1 y SQL Server 2008, se han agregado las columnas siguientes a la colección de esquemas Columns para admitir nuevas columnas de tipos espaciales, de secuencias de archivos y dispersas. Estas columnas no se admiten en versiones anteriores de .NET Framework y SQL Server.  
  
|ColumnName|DataType|Descripción|  
|----------------|--------------|-----------------|  
|IS_FILESTREAM|String|YES si la columna tiene el atributo FILESTREAM.<br /><br /> NO si la columna no tiene el atributo FILESTREAM.|  
|IS_SPARSE|String|YES si la columna es una columna dispersa.<br /><br /> NO si la columna no es una columna dispersa.|  
|IS_COLUMN_SET|String|YES si la columna es de conjunto de columnas.<br /><br /> NO si la columna no es de conjunto de columnas.|  
  
### <a name="allcolumns-sql-server-2008"></a>AllColumns (SQL Server 2008)  

 A partir de .NET Framework versión 3.5 Service Pack 1 y SQL Server 2008, se ha agregado la colección de esquemas AllColumns para admitir columnas dispersas. AllColumns no se admite en versiones anteriores de .NET Framework y SQL Server.  
  
 AllColumns tiene las mismas restricciones y el mismo esquema DataTable resultante que la colección de esquemas Columns. La única diferencia es que AllColumns contiene columnas de conjunto de columnas que no se incluyen en la colección de esquemas Columns. Estas columnas se describen en la siguiente tabla.  
  
|ColumnName|DataType|Descripción|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Catálogo de la tabla.|  
|TABLE_SCHEMA|String|Esquema que contiene la tabla.|  
|TABLE_NAME|String|Nombre de la tabla.|  
|COLUMN_NAME|String|Nombre de la columna.|  
|ORDINAL_POSITION|Int32|Número de identificación de la columna.|  
|COLUMN_DEFAULT|String|Valor predeterminado de la columna.|  
|IS_NULLABLE|String|Nulabilidad de la columna. Si esta columna permite NULL, devuelve YES. En caso contrario devuelve NO.|  
|DATA_TYPE|String|Tipo de datos proporcionado por el sistema.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Longitud máxima, en caracteres, de los datos binarios, de caracteres, o de texto e imagen. En caso contrario se devuelve NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Longitud máxima, en bytes, para datos binarios, datos de caracteres o datos de texto e imagen. En caso contrario se devuelve NULL.|  
|NUMERIC_PRECISION|Byte sin signo|Precisión de los datos numéricos aproximados, datos numéricos exactos, datos enteros o datos monetarios. En caso contrario se devuelve NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Base de la precisión de datos numéricos aproximados, datos numéricos exactos, datos enteros o datos monetarios. En caso contrario se devuelve NULL.|  
|NUMERIC_SCALE|Int32|Escala de datos numéricos aproximados, datos numéricos exactos, datos enteros o datos monetarios. En caso contrario se devuelve NULL.|  
|DATETIME_PRECISION|Int16|Código de subtipo para los tipos de datos interval de SQL-92 y datetime. Para los demás tipos de datos, se devuelve NULL.|  
|CHARACTER_SET_CATALOG|String|Devuelve Master, para indicar la base de datos en la que se encuentra el juego de caracteres, si la columna es del tipo de datos de caracteres o de texto. En caso contrario se devuelve NULL.|  
|CHARACTER_SET_SCHEMA|String|Siempre devuelve NULL.|  
|CHARACTER_SET_NAME|String|Devuelve el nombre único del juego de caracteres si esta columna es del tipo de datos de caracteres o de texto. En caso contrario se devuelve NULL.|  
|COLLATION_CATALOG|String|Devuelve Master, para indicar la base de datos en la que se define la intercalación, si la columna es del tipo de datos de caracteres o de texto. De lo contrario, esta columna es NULL.|  
|IS_FILESTREAM|String|YES si la columna tiene el atributo FILESTREAM.<br /><br /> NO si la columna no tiene el atributo FILESTREAM.|  
|IS_SPARSE|String|YES si la columna es una columna dispersa.<br /><br /> NO si la columna no es una columna dispersa.|  
|IS_COLUMN_SET|String|YES si la columna es de conjunto de columnas.<br /><br /> NO si la columna no es de conjunto de columnas.|  
  
### <a name="columnsetcolumns-sql-server-2008"></a>ColumnSetColumns (SQL Server 2008)  

 A partir de .NET Framework versión 3.5 Service Pack 1 y SQL Server 2008, se ha agregado la colección de esquemas ColumnSetColumns para admitir columnas dispersas. ColumnSetColumns no se admite en versiones anteriores de .NET Framework y SQL Server. La colección de esquemas ColumnSetColumns devuelve el esquema de todas las columnas de un conjunto de columnas. Estas columnas se describen en la siguiente tabla.  
  
|ColumnName|DataType|Descripción|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Catálogo de la tabla.|  
|TABLE_SCHEMA|String|Esquema que contiene la tabla.|  
|TABLE_NAME|String|Nombre de la tabla.|  
|COLUMN_NAME|String|Nombre de la columna.|  
|ORDINAL_POSITION|Int32|Número de identificación de la columna.|  
|COLUMN_DEFAULT|String|Valor predeterminado de la columna.|  
|IS_NULLABLE|String|Nulabilidad de la columna. Si esta columna permite NULL, devuelve YES. En caso contrario devuelve NO.|  
|DATA_TYPE|String|Tipo de datos proporcionado por el sistema.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Longitud máxima, en caracteres, de los datos binarios, de caracteres, o de texto e imagen. En caso contrario se devuelve NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Longitud máxima, en bytes, para datos binarios, datos de caracteres o datos de texto e imagen. En caso contrario se devuelve NULL.|  
|NUMERIC_PRECISION|Byte sin signo|Precisión de los datos numéricos aproximados, datos numéricos exactos, datos enteros o datos monetarios. En caso contrario se devuelve NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Base de la precisión de datos numéricos aproximados, datos numéricos exactos, datos enteros o datos monetarios. En caso contrario se devuelve NULL.|  
|NUMERIC_SCALE|Int32|Escala de datos numéricos aproximados, datos numéricos exactos, datos enteros o datos monetarios. En caso contrario se devuelve NULL.|  
|DATETIME_PRECISION|Int16|Código de subtipo para los tipos de datos interval de SQL-92 y datetime. Para los demás tipos de datos, se devuelve NULL.|  
|CHARACTER_SET_CATALOG|String|Devuelve Master, para indicar la base de datos en la que se encuentra el juego de caracteres, si la columna es del tipo de datos de caracteres o de texto. En caso contrario se devuelve NULL.|  
|CHARACTER_SET_SCHEMA|String|Siempre devuelve NULL.|  
|CHARACTER_SET_NAME|String|Devuelve el nombre único del juego de caracteres si esta columna es del tipo de datos de caracteres o de texto. En caso contrario se devuelve NULL.|  
|COLLATION_CATALOG|String|Devuelve Master, para indicar la base de datos en la que se define la intercalación, si la columna es del tipo de datos de caracteres o de texto. De lo contrario, esta columna es NULL.|  
|IS_FILESTREAM|String|YES si la columna tiene el atributo FILESTREAM.<br /><br /> NO si la columna no tiene el atributo FILESTREAM.|  
|IS_SPARSE|String|YES si la columna es una columna dispersa.<br /><br /> NO si la columna no es una columna dispersa.|  
|IS_COLUMN_SET|String|YES si la columna es de conjunto de columnas.<br /><br /> NO si la columna no es de conjunto de columnas.|  
  
## <a name="users"></a>Usuarios  
  
|ColumnName|DataType|Descripción|  
|----------------|--------------|-----------------|  
|uid|Int16|Id. de usuario, único en esta base de datos. 1 es el propietario de la base de datos.|  
|nombre_de_usuario|String|Nombre de usuario o nombre del grupo, único en esta base de datos.|  
|createdate|DateTime|Fecha en que se agregó la cuenta.|  
|updatedate|DateTime|Fecha en que se cambió la cuenta por última vez.|  
  
## <a name="views"></a>Vistas  
  
|ColumnName|DataType|Descripción|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Catálogo de la vista.|  
|TABLE_SCHEMA|String|Esquema que contiene la vista.|  
|TABLE_NAME|String|Nombre de la vista.|  
|CHECK_OPTION|String|Tipo de WITH CHECK OPTION. Es CASCADE si la vista original se creó mediante WITH CHECK OPTION. En caso contrario se devuelve NONE.|  
|IS_UPDATABLE|String|Especifica si la vista se puede actualizar. Siempre devuelve NO.|  
  
## <a name="viewcolumns"></a>ViewColumns  
  
|ColumnName|DataType|Descripción|  
|----------------|--------------|-----------------|  
|VIEW_CATALOG|String|Catálogo de la vista.|  
|VIEW_SCHEMA|String|Esquema que contiene la vista.|  
|VIEW_NAME|String|Nombre de la vista.|  
|TABLE_CATALOG|String|Catálogo de la tabla asociada con esta vista.|  
|TABLE_SCHEMA|String|Esquema que contiene la tabla asociada con esta vista.|  
|TABLE_NAME|String|Nombre de la tabla asociada con esta vista. Tabla base.|  
|COLUMN_NAME|String|Nombre de la columna.|  
  
## <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|ColumnName|DataType|Descripción|  
|----------------|--------------|-----------------|  
|assembly_name|String|Nombre de archivo del ensamblado.|  
|udt_name|String|Nombre de clase del ensamblado.|  
|version_major|Objeto|Número de versión principal.|  
|version_minor|Objeto|Número de versión secundaria.|  
|version_build|Objeto|Número de compilación.|  
|version_revision|Objeto|Número de revisión.|  
|culture_info|Objeto|La referencia cultural asociada con este tipo definido por el usuario.|  
|public_key|Objeto|La clave pública que utiliza este ensamblado.|  
|is_fixed_length|Boolean|Especifica si la longitud del tipo es siempre igual que max_length.|  
|max_length|Int16|Longitud máxima del tipo en bytes.|  
|Create_Date|DateTime|Fecha en que se creó o registró el ensamblado.|  
|Permission_set_desc|String|Nombre descriptivo del conjunto de permisos y nivel de seguridad del ensamblado.|  
  
## <a name="see-also"></a>Consulte también

- [Recuperar información del esquema de la base de datos](retrieving-database-schema-information.md)
- [Información general de ADO.NET](ado-net-overview.md)

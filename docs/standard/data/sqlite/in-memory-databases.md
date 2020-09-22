---
title: Bases de datos en memoria
ms.date: 12/13/2019
description: Aprenda a usar las bases de datos SQLite en memoria.
ms.openlocfilehash: fbda5787d95a9ce462752b985f847af0b0551fa6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555372"
---
# <a name="in-memory-databases"></a>Bases de datos en memoria

Las bases de datos SQLite en memoria son bases de datos almacenadas por completo en la memoria, no en el disco. Use el nombre de archivo de origen de datos especial `:memory:` para crear una base de datos en memoria. Cuando se cierra la conexión, se elimina la base de datos. Al utilizar `:memory:`, cada conexión crea su propia base de datos.

```connectionstring
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Bases de datos en memoria que se pueden compartir

Las bases de datos en memoria se pueden compartir entre varias conexiones mediante el uso de `Mode=Memory` y `Cache=Shared` en la cadena de conexión. La palabra clave `Data Source` se usa para asignar un nombre a la base de datos en memoria. Las cadenas de conexión que usen el mismo nombre tendrán acceso a la misma base de datos en memoria. La base de datos se conserva siempre y cuando al menos una conexión con ella permanezca abierta. En GitHub se ofrece un [ejemplo](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) que lo muestra.

```connectionstring
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```

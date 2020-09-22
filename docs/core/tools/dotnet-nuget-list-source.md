---
title: Comando dotnet nuget list source
description: El comando dotnet nuget list source muestra todos los orígenes existentes de los archivos de configuración de NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 071061e32aa1bf888e197ec6bf97f4e4f6859f0b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537903"
---
# <a name="dotnet-nuget-list-source"></a>dotnet nuget list source

**Este artículo se aplica a:** ✔️ SDK de .NET Core 3.1.200 y versiones posteriores

## <a name="name"></a>NOMBRE

`dotnet nuget list source`: enumera todos los orígenes de NuGet configurados.

## <a name="synopsis"></a>Sinopsis

```dotnetcli
dotnet nuget list source [--format [Detailed|Short]] [--configfile <FILE>]

dotnet nuget list source -h|--help
```

## <a name="description"></a>Descripción

El comando `dotnet nuget list source` muestra todos los orígenes existentes de los archivos de configuración de NuGet.

## <a name="options"></a>Opciones

- **`--configfile <FILE>`**

  Archivo de configuración de NuGet. Si se especifica, solo se usará la configuración de este archivo. Si no se especifica, se utilizará la jerarquía de archivos de configuración del directorio actual. Para más información, consulte [Configuraciones comunes de NuGet](/nuget/consume-packages/configuring-nuget-behavior).

- **`--format [Detailed|Short]`**

  Formato de la salida del comando de lista: `Detailed` (valor predeterminado) y `Short`.

## <a name="examples"></a>Ejemplos

- Enumeración de los orígenes configurados del directorio actual:

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a>Vea también

- [Secciones de origen del paquete en archivos NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [Comando sources (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)

---
title: SourceLink y bibliotecas de .NET
description: Prácticas recomendadas para el uso de SourceLink para mejorar la depuración de las bibliotecas de .NET.
ms.date: 01/15/2019
ms.openlocfilehash: 5dee2a6b1f77daa641351e02c1dd3e0a38f66550
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201983"
---
# <a name="source-link"></a>SourceLink

SourceLink es una tecnología que permite a los desarrolladores depurar el código fuente de los ensamblados de .NET de NuGet. SourceLink se ejecuta al crear el paquete NuGet e inserta metadatos de control de código fuente dentro de los ensamblados y el paquete. Los desarrolladores que descarguen el paquete y tengan SourceLink habilitado en Visual Studio pueden entrar en su código fuente. SourceLink proporciona metadatos de control de origen para crear una excelente experiencia de depuración.

## <a name="source-link-demo"></a>Demostración de SourceLink

<!--markdownlint-disable MD034 -->
> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>Uso de SourceLink

Puede encontrar instrucciones para el uso de SourceLink en el repositorio de GitHub [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md).

Puede usar el [Explorador de paquetes NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) para confirmar que los metadatos de SourceLink se han insertado correctamente en el paquete. Compruebe que los metadatos de `Repository` están presentes con un identificador de la confirmación y que los archivos .pdb se encuentran con los .dll de cada destino.

![SourceLink en el explorador de paquetes NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink en el explorador de paquetes NuGet")

✔️ ES RECOMENDABLE usar SourceLink para agregar metadatos de control de código fuente a los ensamblados y los paquetes NuGet.

> [!TIP]
> Puede mejorar aún más la experiencia de depuración de los desarrolladores mediante la adición de atributos del depurador a los tipos.
>
> * <xref:System.Diagnostics.DebuggerDisplayAttribute> puede personalizar cómo se muestra una clase o un campo en las ventanas de variables del depurador.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute> indica al depurador que recorra el código en lugar de ejecutarlo paso a paso.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute> controla si se muestra un miembro en las ventanas de variables del depurador.

✔️ ES RECOMENDABLE publicar archivos de símbolos (`*.pdb`).

> Para obtener la mejor experiencia de depuración, la biblioteca debe publicar archivos de símbolos, además de usar SourceLink. Para más información sobre los archivos de símbolos y los paquetes de símbolos, consulte [Paquetes de símbolos](./nuget.md#symbol-packages).

✔️ CONSIDERE la posibilidad de habilitar compilaciones deterministas.

> Las compilaciones deterministas permiten comprobar que el binario resultante se compiló a partir del origen especificado y proporcionan trazabilidad. Para más información sobre las compilaciones deterministas y las instrucciones para habilitarlas, consulte [Compilaciones deterministas](https://github.com/clairernovotny/DeterministicBuilds).

>[!div class="step-by-step"]
>[Anterior](dependencies.md)
>[Siguiente](publish-nuget-package.md)

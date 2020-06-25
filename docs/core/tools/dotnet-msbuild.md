---
title: Comando dotnet msbuild
description: El comando dotnet msbuild proporciona acceso a la línea de comandos de MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 9739fe782e17db3955db087ca1781ad4280cd491
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803176"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="78505-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="78505-103">dotnet msbuild</span></span>

<span data-ttu-id="78505-104">**Este artículo se aplica a:** ✔️ SDK de .NET Core 2.x y versiones posteriores</span><span class="sxs-lookup"><span data-stu-id="78505-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="78505-105">NOMBRE</span><span class="sxs-lookup"><span data-stu-id="78505-105">Name</span></span>

<span data-ttu-id="78505-106">`dotnet msbuild`: compila un proyecto y todas sus dependencias.</span><span class="sxs-lookup"><span data-stu-id="78505-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span> <span data-ttu-id="78505-107">Nota: Si hay varios, es posible que sea necesario especificar una solución o un archivo de proyecto.</span><span class="sxs-lookup"><span data-stu-id="78505-107">Note: A solution or project file may need to be specified if there are multiple.</span></span>

## <a name="synopsis"></a><span data-ttu-id="78505-108">Sinopsis</span><span class="sxs-lookup"><span data-stu-id="78505-108">Synopsis</span></span>

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a><span data-ttu-id="78505-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="78505-109">Description</span></span>

<span data-ttu-id="78505-110">El comando `dotnet msbuild` permite el acceso a una instancia de MSBuild completamente funcional.</span><span class="sxs-lookup"><span data-stu-id="78505-110">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="78505-111">El comando tiene exactamente las mismas funcionalidades que el cliente de línea de comandos de MSBuild existente solo para proyectos de estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="78505-111">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="78505-112">Las opciones son las mismas.</span><span class="sxs-lookup"><span data-stu-id="78505-112">The options are all the same.</span></span> <span data-ttu-id="78505-113">Para obtener más información sobre las opciones disponibles, vea [Referencia de la línea de comandos de MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="78505-113">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="78505-114">El comando [dotnet build](dotnet-build.md) es equivalente al comando `dotnet msbuild -restore`.</span><span class="sxs-lookup"><span data-stu-id="78505-114">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore`.</span></span> <span data-ttu-id="78505-115">Si no quiere compilar el proyecto y hay un destino concreto que quiere ejecutar, use `dotnet build` o `dotnet msbuild` y especifique el destino.</span><span class="sxs-lookup"><span data-stu-id="78505-115">When you don't want to build the project and you have a specific target you want to run, use `dotnet build` or `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="78505-116">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="78505-116">Examples</span></span>

- <span data-ttu-id="78505-117">Creación de un proyecto y sus dependencias:</span><span class="sxs-lookup"><span data-stu-id="78505-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="78505-118">Creación de un proyecto y sus dependencias mediante la configuración de lanzamiento:</span><span class="sxs-lookup"><span data-stu-id="78505-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="78505-119">Ejecuta el destino de publicación y publica para el RID `osx.10.11-x64`:</span><span class="sxs-lookup"><span data-stu-id="78505-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="78505-120">Visualización del proyecto completo con todos los destinos incluidos en el SDK:</span><span class="sxs-lookup"><span data-stu-id="78505-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  dotnet msbuild -preprocess:<fileName>.xml
  ```

---
title: Herramienta de desinstalación
description: Información general de la herramienta de desinstalación de .NET Core, una herramienta guiada que permite limpiar de forma controlada los SDK y los entornos en tiempo de ejecución de .NET Core.
author: sfoslund
ms.date: 05/27/2020
ms.openlocfilehash: 4e70fd3438b582bd5a0d6a52d7e58ed5e07f8811
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446911"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="4fc99-103">Herramienta de desinstalación de .NET Core</span><span class="sxs-lookup"><span data-stu-id="4fc99-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="4fc99-104">La [herramienta de desinstalación de .NET Core](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) permite quitar los SDK y los entornos en tiempo de ejecución de .NET Core de un sistema.</span><span class="sxs-lookup"><span data-stu-id="4fc99-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="4fc99-105">Hay una colección de opciones disponible para especificar las versiones que desea desinstalar.</span><span class="sxs-lookup"><span data-stu-id="4fc99-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="4fc99-106">La herramienta es compatible con Windows y macOS.</span><span class="sxs-lookup"><span data-stu-id="4fc99-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="4fc99-107">Linux no se admite actualmente.</span><span class="sxs-lookup"><span data-stu-id="4fc99-107">Linux is currently not supported.</span></span>

<span data-ttu-id="4fc99-108">En Windows, la herramienta solo puede desinstalar los SDK y entornos en tiempo de ejecución que se instalaron mediante uno de los siguientes instaladores:</span><span class="sxs-lookup"><span data-stu-id="4fc99-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="4fc99-109">El instalador del SDK y del entorno en tiempo de ejecución de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fc99-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="4fc99-110">El instalador de Visual Studio en versiones anteriores a Visual Studio 2019, versión 16.3.</span><span class="sxs-lookup"><span data-stu-id="4fc99-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="4fc99-111">En macOS, la herramienta solo puede desinstalar los SDK y entornos en tiempo de ejecución ubicados en la carpeta */usr/local/share/dotnet*.</span><span class="sxs-lookup"><span data-stu-id="4fc99-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="4fc99-112">Debido a estas limitaciones, es posible que la herramienta no pueda desinstalar todos los SDK y los entornos en tiempo de ejecución de .NET Core de la máquina.</span><span class="sxs-lookup"><span data-stu-id="4fc99-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="4fc99-113">Puede usar el comando `dotnet --info` para buscar todos los SDK y los entornos en tiempo de ejecución de .NET Core instalados, incluidos los entornos en tiempo de ejecución y SDK que esta herramienta no puede quitar.</span><span class="sxs-lookup"><span data-stu-id="4fc99-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="4fc99-114">El comando `dotnet-core-uninstall list` muestra qué SDK se pueden desinstalar con la herramienta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="4fc99-115">Instalación de la herramienta</span><span class="sxs-lookup"><span data-stu-id="4fc99-115">Install the tool</span></span>

<span data-ttu-id="4fc99-116">[Aquí](https://aka.ms/dotnet-core-uninstall-tool) puede descargar la herramienta de desinstalación de .NET Core. En el repositorio de GitHub [dotnet/cli-lab](https://github.com/dotnet/cli-lab) encontrará el código fuente.</span><span class="sxs-lookup"><span data-stu-id="4fc99-116">You can download the .NET Core Uninstall Tool from [here](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="4fc99-117">La herramienta requiere elevación para desinstalar los SDK y los entornos en tiempo de ejecución de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fc99-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="4fc99-118">Por lo tanto, debe instalarse en un directorio protegido contra escritura, como *C:\Archivos de programa* en Windows o */usr/local/bin* en macOS.</span><span class="sxs-lookup"><span data-stu-id="4fc99-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="4fc99-119">Consulte también [Acceso con privilegios elevados para comandos de dotnet](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="4fc99-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="4fc99-120">Para obtener más información, vea las [instrucciones de instalación detalladas](https://aka.ms/dotnet-core-uninstall-tool).</span><span class="sxs-lookup"><span data-stu-id="4fc99-120">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="4fc99-121">Ejecución de la herramienta</span><span class="sxs-lookup"><span data-stu-id="4fc99-121">Run the tool</span></span>

<span data-ttu-id="4fc99-122">En los pasos siguientes se muestra el enfoque recomendado para ejecutar la herramienta de desinstalación:</span><span class="sxs-lookup"><span data-stu-id="4fc99-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="4fc99-123">Paso 1: Mostrar los SDK y los entornos en tiempo de ejecución de .NET Core instalados</span><span class="sxs-lookup"><span data-stu-id="4fc99-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="4fc99-124">Paso 2: Realizar un simulacro</span><span class="sxs-lookup"><span data-stu-id="4fc99-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="4fc99-125">Paso 3: Desinstalar los SDK y los entornos en tiempo de ejecución de .NET Core</span><span class="sxs-lookup"><span data-stu-id="4fc99-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="4fc99-126">Paso 4: Eliminar la carpeta de reserva de NuGet (opcional)</span><span class="sxs-lookup"><span data-stu-id="4fc99-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="4fc99-127">Paso 1: Mostrar los SDK y los entornos en tiempo de ejecución de .NET Core instalados</span><span class="sxs-lookup"><span data-stu-id="4fc99-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="4fc99-128">El comando `dotnet-core-uninstall list` enumera los SDK y los entornos en tiempo de ejecución de .NET Core instalados que se pueden quitar con esta herramienta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="4fc99-129">Visual Studio puede necesitar algunos SDK y entornos en tiempo de ejecución, que se muestran con una nota de por qué no se recomienda desinstalarlos.</span><span class="sxs-lookup"><span data-stu-id="4fc99-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

> [!NOTE]
> <span data-ttu-id="4fc99-130">En la mayoría de los casos, la salida del comando `dotnet-core-uninstall list` no coincidirá con la lista de versiones instaladas en la salida de `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-130">The output of the `dotnet-core-uninstall list` command will not match the list of installed versions in the output of `dotnet --info` in most cases.</span></span> <span data-ttu-id="4fc99-131">En concreto, esta herramienta no mostrará las versiones instaladas mediante archivos ZIP ni administradas por Visual Studio (cualquier versión instalada con Visual Studio 2019 16.3 o posterior).</span><span class="sxs-lookup"><span data-stu-id="4fc99-131">Specifically, this tool will not display versions installed by zip files or managed by Visual Studio (any version installed with Visual Studio 2019 16.3 or later).</span></span> <span data-ttu-id="4fc99-132">Una manera de comprobar si una versión está administrada por Visual Studio es verla en `Add or Remove Programs`, donde las versiones administradas de Visual Studio se marcan como tales en sus nombres para mostrar.</span><span class="sxs-lookup"><span data-stu-id="4fc99-132">One way to check if a version is managed by Visual Studio is to view it in `Add or Remove Programs`, where Visual Studio managed versions are marked as such in their display names.</span></span>

<span data-ttu-id="4fc99-133">**dotnet-core-uninstall list**</span><span class="sxs-lookup"><span data-stu-id="4fc99-133">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="4fc99-134">Sinopsis</span><span class="sxs-lookup"><span data-stu-id="4fc99-134">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="4fc99-135">Opciones</span><span class="sxs-lookup"><span data-stu-id="4fc99-135">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="4fc99-136">Windows</span><span class="sxs-lookup"><span data-stu-id="4fc99-136">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="4fc99-137">Enumera todos los entornos en tiempo de ejecución de ASP.NET Core que se pueden desinstalar con esta herramienta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-137">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="4fc99-138">Enumera todos los conjuntos de hospedaje de .NET Core que se pueden desinstalar con esta herramienta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-138">Lists all the .NET Core hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="4fc99-139">Enumera todos los entornos en tiempo de ejecución de .NET Core que se pueden desinstalar con esta herramienta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-139">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="4fc99-140">Enumera todos los SDK de .NET Core que se pueden desinstalar con esta herramienta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-140">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="4fc99-141">Establece el nivel de detalle.</span><span class="sxs-lookup"><span data-stu-id="4fc99-141">Sets the verbosity level.</span></span> <span data-ttu-id="4fc99-142">Los valores permitidos son `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` y `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="4fc99-143">El valor predeterminado es `normal`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-143">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="4fc99-144">Enumera todos los SDK y entornos en tiempo de ejecución de .NET Core x64 que se pueden desinstalar con esta herramienta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-144">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="4fc99-145">Enumera todos los SDK y entornos en tiempo de ejecución de .NET Core x86 que se pueden desinstalar con esta herramienta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-145">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="4fc99-146">macOS</span><span class="sxs-lookup"><span data-stu-id="4fc99-146">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="4fc99-147">Enumera todos los entornos en tiempo de ejecución de .NET Core que se pueden desinstalar con esta herramienta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-147">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="4fc99-148">Enumera todos los SDK de .NET Core que se pueden desinstalar con esta herramienta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-148">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="4fc99-149">Establece el nivel de detalle.</span><span class="sxs-lookup"><span data-stu-id="4fc99-149">Sets the verbosity level.</span></span> <span data-ttu-id="4fc99-150">Los valores permitidos son `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` y `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="4fc99-151">El valor predeterminado es `normal`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-151">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="4fc99-152">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="4fc99-152">Examples</span></span>

* <span data-ttu-id="4fc99-153">Enumerar todos los SDK y entornos en tiempo de ejecución de .NET Core que se pueden quitar con esta herramienta:</span><span class="sxs-lookup"><span data-stu-id="4fc99-153">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="4fc99-154">Enumerar todos los SDK y entornos en tiempo de ejecución de .NET Core x64:</span><span class="sxs-lookup"><span data-stu-id="4fc99-154">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="4fc99-155">Enumerar todos los SDK de .NET Core x86:</span><span class="sxs-lookup"><span data-stu-id="4fc99-155">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="4fc99-156">Paso 2: Realizar un simulacro</span><span class="sxs-lookup"><span data-stu-id="4fc99-156">Step 2 - Do a dry run</span></span>

<span data-ttu-id="4fc99-157">Los comandos `dotnet-core-uninstall dry-run` y `dotnet-core-uninstall whatif` muestran los SDK y los entornos en tiempo de ejecución de .NET Core que se quitarán en función de las opciones proporcionadas sin realizar la desinstalación.</span><span class="sxs-lookup"><span data-stu-id="4fc99-157">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="4fc99-158">Estos comandos son sinónimos.</span><span class="sxs-lookup"><span data-stu-id="4fc99-158">These commands are synonyms.</span></span>

<span data-ttu-id="4fc99-159">**dotnet-core-uninstall dry-run y dotnet-core-uninstall whatif**</span><span class="sxs-lookup"><span data-stu-id="4fc99-159">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="4fc99-160">Sinopsis</span><span class="sxs-lookup"><span data-stu-id="4fc99-160">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="4fc99-161">Argumentos</span><span class="sxs-lookup"><span data-stu-id="4fc99-161">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="4fc99-162">La versión especificada que se va a desinstalar.</span><span class="sxs-lookup"><span data-stu-id="4fc99-162">The specified version to uninstall.</span></span> <span data-ttu-id="4fc99-163">Puede enumerar varias versiones una detrás de la otra, separadas por espacios.</span><span class="sxs-lookup"><span data-stu-id="4fc99-163">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="4fc99-164">También se admiten los archivos de respuesta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-164">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="4fc99-165">Los archivos de respuesta son una alternativa a la colocación de todas las versiones en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="4fc99-165">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="4fc99-166">Son archivos de texto, normalmente con una extensión \*.rsp y cada versión aparece en una línea independiente.</span><span class="sxs-lookup"><span data-stu-id="4fc99-166">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="4fc99-167">Para especificar un archivo de respuesta para el argumento `VERSION`, use el carácter \@ seguido inmediatamente del nombre del archivo de respuesta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-167">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="4fc99-168">Opciones</span><span class="sxs-lookup"><span data-stu-id="4fc99-168">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="4fc99-169">Windows</span><span class="sxs-lookup"><span data-stu-id="4fc99-169">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="4fc99-170">Quita todos los SDK y entornos en tiempo de ejecución de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fc99-170">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="4fc99-171">Quita solo los SDK y los entornos en tiempo de ejecución de .NET Core que tienen una versión menor que la versión especificada.</span><span class="sxs-lookup"><span data-stu-id="4fc99-171">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="4fc99-172">La versión especificada permanece instalada.</span><span class="sxs-lookup"><span data-stu-id="4fc99-172">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="4fc99-173">Quita todos los SDK y entornos en tiempo de ejecución de .NET Core, excepto las versiones especificadas.</span><span class="sxs-lookup"><span data-stu-id="4fc99-173">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="4fc99-174">Quita los SDK y los entornos en tiempo de ejecución de .NET Core, excepto la versión más alta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-174">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="4fc99-175">Quita los SDK y los entornos en tiempo de ejecución de .NET Core reemplazados por revisiones superiores.</span><span class="sxs-lookup"><span data-stu-id="4fc99-175">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="4fc99-176">Esta opción protege el archivo global.json.</span><span class="sxs-lookup"><span data-stu-id="4fc99-176">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="4fc99-177">Quita los SDK y los entornos en tiempo de ejecución de .NET Core marcados como versiones preliminares.</span><span class="sxs-lookup"><span data-stu-id="4fc99-177">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="4fc99-178">Quita los SDK y los entornos en tiempo de ejecución de .NET Core marcados como versiones preliminares, excepto la versión preliminar más alta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-178">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="4fc99-179">Solo quita los entornos en tiempos de ejecución de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fc99-179">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="4fc99-180">Quita el entorno en tiempo de ejecución de .NET Core y los conjuntos de hospedaje.</span><span class="sxs-lookup"><span data-stu-id="4fc99-180">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="4fc99-181">Quita los SDK y los entornos en tiempo de ejecución de .NET Core que coinciden con la versión `major.minor` especificada.</span><span class="sxs-lookup"><span data-stu-id="4fc99-181">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="4fc99-182">Solo quita los entornos en tiempo de ejecución de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fc99-182">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="4fc99-183">Solo quita los SDK de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fc99-183">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="4fc99-184">Establece el nivel de detalle.</span><span class="sxs-lookup"><span data-stu-id="4fc99-184">Sets the verbosity level.</span></span> <span data-ttu-id="4fc99-185">Los valores permitidos son `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` y `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="4fc99-186">El valor predeterminado es `normal`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-186">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="4fc99-187">Se debe usar con `--sdk`, `--runtime` y `--aspnet-runtime` para quitar los SDK o los entornos en tiempo de ejecución x64.</span><span class="sxs-lookup"><span data-stu-id="4fc99-187">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="4fc99-188">Se debe usar con `--sdk`, `--runtime` y `--aspnet-runtime` para quitar los SDK o los entornos en tiempo de ejecución x86.</span><span class="sxs-lookup"><span data-stu-id="4fc99-188">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="4fc99-189">**`--force`** Fuerza la eliminación de las versiones que Visual Studio puede usar.</span><span class="sxs-lookup"><span data-stu-id="4fc99-189">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="4fc99-190">Notas:</span><span class="sxs-lookup"><span data-stu-id="4fc99-190">Notes:</span></span>

1. <span data-ttu-id="4fc99-191">Se requiere exactamente uno de los valores `--sdk`, `--runtime`, `--aspnet-runtime` y `--hosting-bundle`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-191">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="4fc99-192">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor` y `[<VERSION>...]` son valores exclusivos.</span><span class="sxs-lookup"><span data-stu-id="4fc99-192">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="4fc99-193">Si no se especifica `--x64` o `--x86`, se quitarán tanto x64 como x86.</span><span class="sxs-lookup"><span data-stu-id="4fc99-193">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="4fc99-194">macOS</span><span class="sxs-lookup"><span data-stu-id="4fc99-194">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="4fc99-195">Quita todos los SDK y entornos en tiempo de ejecución de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fc99-195">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="4fc99-196">Quita los SDK y los entornos en tiempo de ejecución de .NET Core inferiores a la versión especificada.</span><span class="sxs-lookup"><span data-stu-id="4fc99-196">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="4fc99-197">La versión especificada se conservará.</span><span class="sxs-lookup"><span data-stu-id="4fc99-197">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="4fc99-198">Quita los SDK y los entornos en tiempo de ejecución de .NET Core, excepto las versiones especificadas.</span><span class="sxs-lookup"><span data-stu-id="4fc99-198">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="4fc99-199">Quita los SDK y los entornos en tiempo de ejecución de .NET Core, excepto la versión más alta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-199">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="4fc99-200">Quita los SDK y los entornos en tiempo de ejecución de .NET Core reemplazados por revisiones superiores.</span><span class="sxs-lookup"><span data-stu-id="4fc99-200">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="4fc99-201">Esta opción protege el archivo global.json.</span><span class="sxs-lookup"><span data-stu-id="4fc99-201">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="4fc99-202">Quita los SDK y los entornos en tiempo de ejecución de .NET Core marcados como versiones preliminares.</span><span class="sxs-lookup"><span data-stu-id="4fc99-202">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="4fc99-203">Quita los SDK y los entornos en tiempo de ejecución de .NET Core marcados como versiones preliminares, excepto la versión preliminar más alta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-203">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="4fc99-204">Quita los SDK y los entornos en tiempo de ejecución de .NET Core que coinciden con la versión `major.minor` especificada.</span><span class="sxs-lookup"><span data-stu-id="4fc99-204">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="4fc99-205">Solo quita los entornos en tiempo de ejecución de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fc99-205">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="4fc99-206">Solo quita los SDK de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fc99-206">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="4fc99-207">Establece el nivel de detalle.</span><span class="sxs-lookup"><span data-stu-id="4fc99-207">Sets the verbosity level.</span></span> <span data-ttu-id="4fc99-208">Los valores permitidos son `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` y `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-208">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="4fc99-209">El valor predeterminado es `normal`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-209">The default value is `normal`.</span></span>
  
* <span data-ttu-id="4fc99-210">**`--force`** Fuerza la eliminación de las versiones que Visual Studio o los SDK puedes usar.</span><span class="sxs-lookup"><span data-stu-id="4fc99-210">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="4fc99-211">Notas:</span><span class="sxs-lookup"><span data-stu-id="4fc99-211">Notes:</span></span>

1. <span data-ttu-id="4fc99-212">Se requiere uno de los valores `--sdk` y `--runtime`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-212">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="4fc99-213">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor` y `[<VERSION>...]` son valores exclusivos.</span><span class="sxs-lookup"><span data-stu-id="4fc99-213">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="4fc99-214">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="4fc99-214">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="4fc99-215">De forma predeterminada, los SDK y los entornos en tiempo de ejecución de .NET Core que puede necesitar Visual Studio u otros SDK no se incluyen en la salida de `dotnet-core-uninstall dry-run`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-215">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="4fc99-216">En los siguientes ejemplos, es posible que algunos de los SDK y entornos en tiempo de ejecución especificados no se incluyan en la salida, según el estado de la máquina.</span><span class="sxs-lookup"><span data-stu-id="4fc99-216">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="4fc99-217">Para incluir todos los SDK y entornos en tiempo de ejecución, agréguelos explícitamente como argumentos o use la opción `--force`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-217">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="4fc99-218">Realizar un simulacro de la eliminación de todos entornos en tiempo de ejecución de .NET Core que se han reemplazado por revisiones superiores:</span><span class="sxs-lookup"><span data-stu-id="4fc99-218">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="4fc99-219">Realizar un simulacro de la eliminación de todos los SDK de .NET Core inferiores a la versión `2.2.301`:</span><span class="sxs-lookup"><span data-stu-id="4fc99-219">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="4fc99-220">Paso 3: Desinstalar los SDK y los entornos en tiempo de ejecución de .NET Core</span><span class="sxs-lookup"><span data-stu-id="4fc99-220">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="4fc99-221">`dotnet-core-uninstall remove` desinstala los SDK y los entornos en tiempo de ejecución de .NET Core especificados por una colección de opciones.</span><span class="sxs-lookup"><span data-stu-id="4fc99-221">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="4fc99-222">La herramienta no se puede usar para desinstalar los SDK y entornos en tiempo de ejecución con la versión 5.0 o posterior.</span><span class="sxs-lookup"><span data-stu-id="4fc99-222">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="4fc99-223">Dado que esta herramienta tiene un comportamiento destructivo, es **altamente** recomendable que realice un simulacro antes de ejecutar el comando remove.</span><span class="sxs-lookup"><span data-stu-id="4fc99-223">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="4fc99-224">El simulacro le mostrará qué SDK y entornos en tiempo de ejecución de .NET Core se quitarán cuando use el comando `remove`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-224">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="4fc99-225">Consulte [¿Puedo quitar una versión?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) para saber qué SDK y entornos en tiempo de ejecución se pueden quitar de forma segura.</span><span class="sxs-lookup"><span data-stu-id="4fc99-225">Refer to [Should I remove a version?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="4fc99-226">Tenga en cuenta las siguientes advertencias:</span><span class="sxs-lookup"><span data-stu-id="4fc99-226">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="4fc99-227">Esta herramienta puede desinstalar las versiones del SDK de .NET Core que necesitan los archivos `global.json` de la máquina.</span><span class="sxs-lookup"><span data-stu-id="4fc99-227">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="4fc99-228">Puede volver a instalar los SDK de .NET Core desde la página [Descarga de .NET Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="4fc99-228">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="4fc99-229">Esta herramienta puede desinstalar las versiones del entorno en tiempo de ejecución de .NET Core que necesitan las aplicaciones que dependen del marco de trabajo de la máquina.</span><span class="sxs-lookup"><span data-stu-id="4fc99-229">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="4fc99-230">Puede volver a instalar los entornos en tiempo de ejecución de .NET Core desde la página [Descarga de .NET Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="4fc99-230">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="4fc99-231">Esta herramienta puede desinstalar las versiones del SDK y del entorno en tiempo de ejecución de .NET Core en las que se basa Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4fc99-231">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="4fc99-232">Si interrumpe la instalación de Visual Studio, ejecute "Reparar" en el instalador de Visual Studio para volver a un estado de funcionamiento.</span><span class="sxs-lookup"><span data-stu-id="4fc99-232">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="4fc99-233">De forma predeterminada, todos los comandos mantienen los SDK y los entornos en tiempo de ejecución de .NET Core que puede necesitar Visual Studio u otros SDK.</span><span class="sxs-lookup"><span data-stu-id="4fc99-233">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="4fc99-234">Estos SDK y entornos en tiempos de ejecución se pueden desinstalar si se enumeran explícitamente como argumentos o mediante la opción `--force`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-234">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="4fc99-235">La herramienta requiere elevación para desinstalar los SDK y los entornos en tiempo de ejecución de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fc99-235">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="4fc99-236">Ejecute la herramienta en un símbolo del sistema de administrador en Windows y con `sudo` en macOS.</span><span class="sxs-lookup"><span data-stu-id="4fc99-236">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="4fc99-237">Los comandos `dry-run` y `whatif` no requieren elevación.</span><span class="sxs-lookup"><span data-stu-id="4fc99-237">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="4fc99-238">**dotnet-core-uninstall remove**</span><span class="sxs-lookup"><span data-stu-id="4fc99-238">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="4fc99-239">Sinopsis</span><span class="sxs-lookup"><span data-stu-id="4fc99-239">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="4fc99-240">Argumentos</span><span class="sxs-lookup"><span data-stu-id="4fc99-240">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="4fc99-241">La versión especificada que se va a desinstalar.</span><span class="sxs-lookup"><span data-stu-id="4fc99-241">The specified version to uninstall.</span></span> <span data-ttu-id="4fc99-242">Puede enumerar varias versiones una detrás de la otra, separadas por espacios.</span><span class="sxs-lookup"><span data-stu-id="4fc99-242">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="4fc99-243">También se admiten los archivos de respuesta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-243">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="4fc99-244">Los archivos de respuesta son una alternativa a la colocación de todas las versiones en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="4fc99-244">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="4fc99-245">Son archivos de texto, normalmente con una extensión \*.rsp y cada versión aparece en una línea independiente.</span><span class="sxs-lookup"><span data-stu-id="4fc99-245">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="4fc99-246">Para especificar un archivo de respuesta para el argumento `VERSION`, use el carácter \@ seguido inmediatamente del nombre del archivo de respuesta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-246">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="4fc99-247">Opciones</span><span class="sxs-lookup"><span data-stu-id="4fc99-247">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="4fc99-248">Windows</span><span class="sxs-lookup"><span data-stu-id="4fc99-248">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="4fc99-249">Quita todos los SDK y entornos en tiempo de ejecución de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fc99-249">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="4fc99-250">Quita solo los SDK y los entornos en tiempo de ejecución de .NET Core que tienen una versión menor que la versión especificada.</span><span class="sxs-lookup"><span data-stu-id="4fc99-250">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="4fc99-251">La versión especificada permanece instalada.</span><span class="sxs-lookup"><span data-stu-id="4fc99-251">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="4fc99-252">Quita todos los SDK y entornos en tiempo de ejecución de .NET Core, excepto las versiones especificadas.</span><span class="sxs-lookup"><span data-stu-id="4fc99-252">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="4fc99-253">Quita los SDK y los entornos en tiempo de ejecución de .NET Core, excepto la versión más alta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-253">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="4fc99-254">Quita los SDK y los entornos en tiempo de ejecución de .NET Core reemplazados por revisiones superiores.</span><span class="sxs-lookup"><span data-stu-id="4fc99-254">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="4fc99-255">Esta opción protege el archivo global.json.</span><span class="sxs-lookup"><span data-stu-id="4fc99-255">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="4fc99-256">Quita los SDK y los entornos en tiempo de ejecución de .NET Core marcados como versiones preliminares.</span><span class="sxs-lookup"><span data-stu-id="4fc99-256">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="4fc99-257">Quita los SDK y los entornos en tiempo de ejecución de .NET Core marcados como versiones preliminares, excepto la versión preliminar más alta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-257">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="4fc99-258">Solo quita los entornos en tiempos de ejecución de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fc99-258">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="4fc99-259">Solo quita conjuntos de hospedaje de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fc99-259">Removes .NET Core hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="4fc99-260">Quita los SDK y los entornos en tiempo de ejecución de .NET Core que coinciden con la versión `major.minor` especificada.</span><span class="sxs-lookup"><span data-stu-id="4fc99-260">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="4fc99-261">Solo quita los entornos en tiempo de ejecución de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fc99-261">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="4fc99-262">Solo quita los SDK de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fc99-262">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="4fc99-263">Establece el nivel de detalle.</span><span class="sxs-lookup"><span data-stu-id="4fc99-263">Sets the verbosity level.</span></span> <span data-ttu-id="4fc99-264">Los valores permitidos son `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` y `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-264">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="4fc99-265">El valor predeterminado es `normal`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-265">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="4fc99-266">Se debe usar con `--sdk`, `--runtime` y `--aspnet-runtime` para quitar los SDK o los entornos en tiempo de ejecución x64.</span><span class="sxs-lookup"><span data-stu-id="4fc99-266">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="4fc99-267">Se debe usar con `--sdk`, `--runtime` y `--aspnet-runtime` para quitar los SDK o los entornos en tiempo de ejecución x86.</span><span class="sxs-lookup"><span data-stu-id="4fc99-267">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="4fc99-268">**`-y, --yes`** Ejecuta el comando sin requerir una confirmación sí o no.</span><span class="sxs-lookup"><span data-stu-id="4fc99-268">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="4fc99-269">**`--force`** Fuerza la eliminación de las versiones que Visual Studio puede usar.</span><span class="sxs-lookup"><span data-stu-id="4fc99-269">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="4fc99-270">Notas:</span><span class="sxs-lookup"><span data-stu-id="4fc99-270">Notes:</span></span>

1. <span data-ttu-id="4fc99-271">Se requiere exactamente uno de los valores `--sdk`, `--runtime`, `--aspnet-runtime` y `--hosting-bundle`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-271">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="4fc99-272">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor` y `[<VERSION>...]` son valores exclusivos.</span><span class="sxs-lookup"><span data-stu-id="4fc99-272">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="4fc99-273">Si no se especifica `--x64` o `--x86`, se quitarán tanto x64 como x86.</span><span class="sxs-lookup"><span data-stu-id="4fc99-273">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="4fc99-274">macOS</span><span class="sxs-lookup"><span data-stu-id="4fc99-274">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="4fc99-275">Quita todos los SDK y entornos en tiempo de ejecución de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fc99-275">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="4fc99-276">Quita los SDK y los entornos en tiempo de ejecución de .NET Core inferiores a la versión especificada.</span><span class="sxs-lookup"><span data-stu-id="4fc99-276">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="4fc99-277">La versión especificada se conservará.</span><span class="sxs-lookup"><span data-stu-id="4fc99-277">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="4fc99-278">Quita los SDK y los entornos en tiempo de ejecución de .NET Core, excepto las versiones especificadas.</span><span class="sxs-lookup"><span data-stu-id="4fc99-278">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="4fc99-279">Quita los SDK y los entornos en tiempo de ejecución de .NET Core, excepto la versión más alta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-279">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="4fc99-280">Quita los SDK y los entornos en tiempo de ejecución de .NET Core reemplazados por revisiones superiores.</span><span class="sxs-lookup"><span data-stu-id="4fc99-280">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="4fc99-281">Esta opción protege el archivo global.json.</span><span class="sxs-lookup"><span data-stu-id="4fc99-281">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="4fc99-282">Quita los SDK y los entornos en tiempo de ejecución de .NET Core marcados como versiones preliminares.</span><span class="sxs-lookup"><span data-stu-id="4fc99-282">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="4fc99-283">Quita los SDK y los entornos en tiempo de ejecución de .NET Core marcados como versiones preliminares, excepto la versión preliminar más alta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-283">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="4fc99-284">Quita los SDK y los entornos en tiempo de ejecución de .NET Core que coinciden con la versión `major.minor` especificada.</span><span class="sxs-lookup"><span data-stu-id="4fc99-284">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="4fc99-285">Solo quita los entornos en tiempo de ejecución de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fc99-285">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="4fc99-286">Solo quita los SDK de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fc99-286">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="4fc99-287">Establece el nivel de detalle.</span><span class="sxs-lookup"><span data-stu-id="4fc99-287">Sets the verbosity level.</span></span> <span data-ttu-id="4fc99-288">Los valores permitidos son `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` y `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-288">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="4fc99-289">El valor predeterminado es `normal`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-289">The default value is `normal`.</span></span>

* <span data-ttu-id="4fc99-290">**`-y, --yes`** Ejecuta el comando sin requerir una confirmación S/N.</span><span class="sxs-lookup"><span data-stu-id="4fc99-290">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="4fc99-291">**`--force`** Fuerza la eliminación de las versiones que Visual Studio o los SDK puedes usar.</span><span class="sxs-lookup"><span data-stu-id="4fc99-291">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="4fc99-292">Notas:</span><span class="sxs-lookup"><span data-stu-id="4fc99-292">Notes:</span></span>

1. <span data-ttu-id="4fc99-293">Se requiere uno de los valores `--sdk` y `--runtime`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-293">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="4fc99-294">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor` y `[<VERSION>...]` son valores exclusivos.</span><span class="sxs-lookup"><span data-stu-id="4fc99-294">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="4fc99-295">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="4fc99-295">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="4fc99-296">De forma predeterminada, los SDK y los entornos en tiempo de ejecución de .NET Core que puede necesitar Visual Studio u otros SDK se mantienen.</span><span class="sxs-lookup"><span data-stu-id="4fc99-296">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="4fc99-297">En los siguientes ejemplos, es posible que algunos de los SDK y entornos en tiempo de ejecución especificados se mantengan, según el estado de la máquina.</span><span class="sxs-lookup"><span data-stu-id="4fc99-297">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="4fc99-298">Para quitar todos los SDK y entornos en tiempo de ejecución, agréguelos explícitamente como argumentos o use la opción `--force`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-298">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="4fc99-299">Quitar todos los entornos en tiempo de ejecución de .NET Core excepto la versión `3.0.0-preview6-27804-01` sin necesidad de la confirmación S/N:</span><span class="sxs-lookup"><span data-stu-id="4fc99-299">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="4fc99-300">Quitar todos los SDK de .NET Core 1.1 sin necesidad de la confirmación de S/N:</span><span class="sxs-lookup"><span data-stu-id="4fc99-300">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="4fc99-301">Quitar el SDK de .NET Core 1.1.11 sin salida de consola:</span><span class="sxs-lookup"><span data-stu-id="4fc99-301">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="4fc99-302">Quitar todos los SDK de .NET Core que se puedan quitar con seguridad con esta herramienta:</span><span class="sxs-lookup"><span data-stu-id="4fc99-302">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="4fc99-303">Quitar todos los SDK de .NET Core que puede quitar esta herramienta, incluidos los SDK que puede necesitar Visual Studio (no recomendado):</span><span class="sxs-lookup"><span data-stu-id="4fc99-303">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="4fc99-304">Quitar todos los SDK de .NET Core que se especifican en el archivo de respuesta `versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="4fc99-304">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="4fc99-305">El contenido de *versions.rsp* es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="4fc99-305">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="4fc99-306">Paso 4: Eliminar la carpeta de reserva de NuGet (opcional)</span><span class="sxs-lookup"><span data-stu-id="4fc99-306">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="4fc99-307">En algunos casos, ya no necesita `NuGetFallbackFolder` y puede que desee eliminarlo.</span><span class="sxs-lookup"><span data-stu-id="4fc99-307">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="4fc99-308">Para más información sobre cómo eliminar esta carpeta, consulte [Quitar NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="4fc99-308">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="4fc99-309">Desinstalación de la herramienta.</span><span class="sxs-lookup"><span data-stu-id="4fc99-309">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="4fc99-310">Windows</span><span class="sxs-lookup"><span data-stu-id="4fc99-310">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="4fc99-311">Abra **Agregar o quitar programas**.</span><span class="sxs-lookup"><span data-stu-id="4fc99-311">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="4fc99-312">Busque `Microsoft .NET Core SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="4fc99-312">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="4fc99-313">Seleccione **Desinstalar**.</span><span class="sxs-lookup"><span data-stu-id="4fc99-313">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="4fc99-314">macOS</span><span class="sxs-lookup"><span data-stu-id="4fc99-314">macOS</span></span>](#tab/macos)

<span data-ttu-id="4fc99-315">Elimine el archivo *dotnet-Core-Uninstall.tar.gz* descargado del directorio donde se instaló.</span><span class="sxs-lookup"><span data-stu-id="4fc99-315">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="4fc99-316">Si descomprimió el contenido de este archivo en otro directorio, asegúrese de eliminar también dicho contenido.</span><span class="sxs-lookup"><span data-stu-id="4fc99-316">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---

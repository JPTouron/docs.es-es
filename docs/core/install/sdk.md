---
title: 'Instalación del SDK de .NET Core en Windows, Linux y macOS: .NET Core'
description: Obtenga información sobre cómo instalar .NET Core en Windows, Linux y macOS. Descubra las dependencias necesarias para desarrollar aplicaciones en .NET Core.
author: thraka
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: f8e5cc134d4132c83544effa7f1937f2a2c8d012
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596311"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="b04ce-104">Instalación del SDK de .NET Core</span><span class="sxs-lookup"><span data-stu-id="b04ce-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="b04ce-105">En este artículo obtendrá información sobre cómo instalar el SDK de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b04ce-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="b04ce-106">El SDK de .NET Core se usa para crear aplicaciones y bibliotecas de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b04ce-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="b04ce-107">El entorno de ejecución de .NET Core siempre se instala con el SDK.</span><span class="sxs-lookup"><span data-stu-id="b04ce-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="b04ce-108">Instalación mediante un instalador</span><span class="sxs-lookup"><span data-stu-id="b04ce-108">Install with an installer</span></span>

<span data-ttu-id="b04ce-109">Windows tiene instaladores independientes que se pueden usar para instalar el SDK de .NET Core 3.1:</span><span class="sxs-lookup"><span data-stu-id="b04ce-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="b04ce-110">CPU de x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="b04ce-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="b04ce-111">CPU de x86 (32 bits)</span><span class="sxs-lookup"><span data-stu-id="b04ce-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="b04ce-112">Instalación mediante un instalador</span><span class="sxs-lookup"><span data-stu-id="b04ce-112">Install with an installer</span></span>

<span data-ttu-id="b04ce-113">macOS tiene instaladores independientes que se pueden usar para instalar el SDK de .NET Core 3.1:</span><span class="sxs-lookup"><span data-stu-id="b04ce-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="b04ce-114">CPU de x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="b04ce-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="b04ce-115">Descarga e instalación de forma manual</span><span class="sxs-lookup"><span data-stu-id="b04ce-115">Download and manually install</span></span>

<span data-ttu-id="b04ce-116">Como alternativa a los instaladores de macOS para .NET Core, puede descargar e instalar el SDK de forma manual.</span><span class="sxs-lookup"><span data-stu-id="b04ce-116">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK.</span></span>

<span data-ttu-id="b04ce-117">Para extraer el SDK y hacer que los comandos de la CLI de .NET Core estén disponibles en el terminal, en primer lugar [descargue](#all-net-core-downloads) una versión binaria de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b04ce-117">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="b04ce-118">Después, abra un terminal y ejecute los comandos siguientes.</span><span class="sxs-lookup"><span data-stu-id="b04ce-118">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="b04ce-119">Se supone que el entorno de ejecución se ha descargado al archivo `~/Downloads/dotnet-sdk.pkg`.</span><span class="sxs-lookup"><span data-stu-id="b04ce-119">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-sdk.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a><span data-ttu-id="b04ce-120">Instalar en Linux</span><span class="sxs-lookup"><span data-stu-id="b04ce-120">Install on Linux</span></span>

<span data-ttu-id="b04ce-121">Este artículo se retirará pronto.</span><span class="sxs-lookup"><span data-stu-id="b04ce-121">This article will be removed soon.</span></span> <span data-ttu-id="b04ce-122">En este momento se reemplaza por [Instalación de .NET Core en Linux](linux.md).</span><span class="sxs-lookup"><span data-stu-id="b04ce-122">It is currently replaced by [Install .NET Core on Linux](linux.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="b04ce-123">Instalación con Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b04ce-123">Install with Visual Studio</span></span>

<span data-ttu-id="b04ce-124">Si usa Visual Studio para desarrollar aplicaciones de .NET Core, en la tabla siguiente se describe la versión mínima necesaria de Visual Studio, basada en la versión del SDK de .NET Core de destino.</span><span class="sxs-lookup"><span data-stu-id="b04ce-124">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="b04ce-125">Versión del SDK de .NET Core</span><span class="sxs-lookup"><span data-stu-id="b04ce-125">.NET Core SDK version</span></span> | <span data-ttu-id="b04ce-126">Versión de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b04ce-126">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="b04ce-127">3.1</span><span class="sxs-lookup"><span data-stu-id="b04ce-127">3.1</span></span>                   | <span data-ttu-id="b04ce-128">Visual Studio 2019, versión 16.4 o posterior.</span><span class="sxs-lookup"><span data-stu-id="b04ce-128">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="b04ce-129">3.0</span><span class="sxs-lookup"><span data-stu-id="b04ce-129">3.0</span></span>                   | <span data-ttu-id="b04ce-130">Visual Studio 2019, versión 16.3 o posterior.</span><span class="sxs-lookup"><span data-stu-id="b04ce-130">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="b04ce-131">2.2</span><span class="sxs-lookup"><span data-stu-id="b04ce-131">2.2</span></span>                   | <span data-ttu-id="b04ce-132">Visual Studio 2017, versión 15.9 o posterior.</span><span class="sxs-lookup"><span data-stu-id="b04ce-132">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="b04ce-133">2.1</span><span class="sxs-lookup"><span data-stu-id="b04ce-133">2.1</span></span>                   | <span data-ttu-id="b04ce-134">Visual Studio 2017, versión 15.7 o posterior.</span><span class="sxs-lookup"><span data-stu-id="b04ce-134">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="b04ce-135">Si ya tiene Visual Studio instalado, puede comprobar la versión siguiendo los pasos que se detallan a continuación.</span><span class="sxs-lookup"><span data-stu-id="b04ce-135">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="b04ce-136">Abra Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b04ce-136">Open Visual Studio.</span></span>
01. <span data-ttu-id="b04ce-137">Seleccione **Ayuda** > **Acerca de Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b04ce-137">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="b04ce-138">Lea el número de versión en el cuadro de diálogo **Acerca de**.</span><span class="sxs-lookup"><span data-stu-id="b04ce-138">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="b04ce-139">Visual Studio puede instalar el SDK y el entorno de ejecución de .NET Core más recientes.</span><span class="sxs-lookup"><span data-stu-id="b04ce-139">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="b04ce-140">[Descargue Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="b04ce-140">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="b04ce-141">Selección de una carga de trabajo</span><span class="sxs-lookup"><span data-stu-id="b04ce-141">Select a workload</span></span>

<span data-ttu-id="b04ce-142">Al instalar o modificar Visual Studio, seleccione una de las cargas de trabajo siguientes o más, en función del tipo de aplicación que quiera compilar:</span><span class="sxs-lookup"><span data-stu-id="b04ce-142">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="b04ce-143">La carga de trabajo **Desarrollo multiplataforma de .NET Core** en la sección **Otros conjuntos de herramientas**.</span><span class="sxs-lookup"><span data-stu-id="b04ce-143">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="b04ce-144">La carga de trabajo **Desarrollo de ASP.NET y web** en la sección **Web y nube**.</span><span class="sxs-lookup"><span data-stu-id="b04ce-144">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="b04ce-145">La carga de trabajo **Desarrollo de Azure** en la sección **Web y nube**.</span><span class="sxs-lookup"><span data-stu-id="b04ce-145">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="b04ce-146">La carga de trabajo **Desarrollo de escritorio de .NET** en la sección **Móviles y de escritorio**.</span><span class="sxs-lookup"><span data-stu-id="b04ce-146">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="b04ce-147">[![Visual Studio 2019 para Windows con la carga de trabajo de .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="b04ce-147">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="b04ce-148">Descarga e instalación de forma manual</span><span class="sxs-lookup"><span data-stu-id="b04ce-148">Download and manually install</span></span>

<span data-ttu-id="b04ce-149">Para extraer el runtime y hacer que los comandos de la CLI de .NET Core estén disponibles en el terminal, en primer lugar [descargue](#all-net-core-downloads) una versión binaria de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b04ce-149">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="b04ce-150">A continuación, cree un directorio para la instalación, por ejemplo `%USERPROFILE%\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="b04ce-150">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="b04ce-151">Por último, extraiga el archivo zip descargado en ese directorio.</span><span class="sxs-lookup"><span data-stu-id="b04ce-151">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="b04ce-152">De forma predeterminada, los comandos y las aplicaciones de la CLI de .NET Core no usarán la versión de .NET Core instalada de esta manera y debe elegir explícitamente usarla.</span><span class="sxs-lookup"><span data-stu-id="b04ce-152">By default, .NET Core CLI commands and apps won't use .NET Core installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="b04ce-153">Para ello, cambie las variables de entorno con las que se inicia una aplicación:</span><span class="sxs-lookup"><span data-stu-id="b04ce-153">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="b04ce-154">Este enfoque permite instalar varias versiones en ubicaciones independientes y elegir explícitamente qué ubicación de instalación debe usar una aplicación mediante la ejecución de la aplicación con variables de entorno que apuntan a esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="b04ce-154">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="b04ce-155">Incluso cuando se establecen estas variables de entorno, .NET Core sigue teniendo en cuenta la ubicación de instalación global predeterminada al seleccionar el mejor marco para ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b04ce-155">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="b04ce-156">Normalmente, el valor predeterminado es `C:\Program Files\dotnet`, que usan los instaladores.</span><span class="sxs-lookup"><span data-stu-id="b04ce-156">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="b04ce-157">Puede indicar al motor en tiempo de ejecución que solo use la ubicación de instalación personalizada mediante la configuración de esta variable de entorno:</span><span class="sxs-lookup"><span data-stu-id="b04ce-157">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="b04ce-158">Instalación con Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="b04ce-158">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="b04ce-159">Visual Studio para Mac instala el SDK de .NET Core cuando se selecciona la carga de trabajo **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="b04ce-159">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="b04ce-160">Para empezar con el desarrollo en .NET Core en macOS, vea [Instalación de Visual Studio 2019 para Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="b04ce-160">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="b04ce-161">Para obtener la versión más reciente, .NET Core 3.1, se debe usar la versión preliminar de Visual Studio para Mac 8.4.</span><span class="sxs-lookup"><span data-stu-id="b04ce-161">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="b04ce-162">[![Visual Studio 2019 para Mac de macOS con la característica de carga de trabajo de .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="b04ce-162">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="b04ce-163">Instalación junto con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b04ce-163">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="b04ce-164">Visual Studio Code es un editor de código fuente ligero y eficaz que se ejecuta en el escritorio.</span><span class="sxs-lookup"><span data-stu-id="b04ce-164">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="b04ce-165">Visual Studio Code está disponible para Windows, macOS y Linux.</span><span class="sxs-lookup"><span data-stu-id="b04ce-165">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="b04ce-166">Aunque Visual Studio Code no viene con un instalador automatizado de .NET Core como Visual Studio, agregar compatibilidad con .NET Core es sencillo.</span><span class="sxs-lookup"><span data-stu-id="b04ce-166">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="b04ce-167">[Descargue e instale Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="b04ce-167">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="b04ce-168">[Descargue e instale el SDK de .NET Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="b04ce-168">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="b04ce-169">[Instale la extensión de C# desde el Marketplace de Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="b04ce-169">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="b04ce-170">Instalación mediante la automatización de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b04ce-170">Install with PowerShell automation</span></span>

<span data-ttu-id="b04ce-171">Los [scripts de dotnet-install](../tools/dotnet-install-script.md) se usan para la automatización y las instalaciones que no son de administrador del SDK.</span><span class="sxs-lookup"><span data-stu-id="b04ce-171">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="b04ce-172">Se puede descargar el script desde la [página de referencia del script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="b04ce-172">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="b04ce-173">El valor predeterminado del script es instalar la versión más reciente de [soporte técnico a largo plazo (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core), que actualmente es .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="b04ce-173">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="b04ce-174">Para instalar la versión actual de .NET Core, ejecute el script con el modificador siguiente.</span><span class="sxs-lookup"><span data-stu-id="b04ce-174">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="b04ce-175">Instalación mediante la automatización de Bash</span><span class="sxs-lookup"><span data-stu-id="b04ce-175">Install with bash automation</span></span>

<span data-ttu-id="b04ce-176">Los [scripts de dotnet-install](../tools/dotnet-install-script.md) se usan para la automatización y las instalaciones que no son de administrador del SDK.</span><span class="sxs-lookup"><span data-stu-id="b04ce-176">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="b04ce-177">Se puede descargar el script desde la [página de referencia del script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="b04ce-177">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="b04ce-178">El valor predeterminado del script es instalar la versión más reciente de [soporte técnico a largo plazo (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core), que actualmente es .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="b04ce-178">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="b04ce-179">Para instalar la versión actual de .NET Core, ejecute el script con el modificador siguiente.</span><span class="sxs-lookup"><span data-stu-id="b04ce-179">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="b04ce-180">Todas las descargas de .NET Core</span><span class="sxs-lookup"><span data-stu-id="b04ce-180">All .NET Core downloads</span></span>

<span data-ttu-id="b04ce-181">Puede descargar e instalar .NET Core directamente con uno de los vínculos siguientes:</span><span class="sxs-lookup"><span data-stu-id="b04ce-181">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="b04ce-182">Descargas de .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="b04ce-182">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="b04ce-183">Descargas de .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b04ce-183">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="b04ce-184">Descargas de .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="b04ce-184">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="b04ce-185">Descargas de .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b04ce-185">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="b04ce-186">Docker</span><span class="sxs-lookup"><span data-stu-id="b04ce-186">Docker</span></span>

<span data-ttu-id="b04ce-187">Los contenedores proporcionan una manera ligera de aislar la aplicación del resto del sistema host.</span><span class="sxs-lookup"><span data-stu-id="b04ce-187">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="b04ce-188">Los contenedores de la misma máquina comparten solo el kernel y usan los recursos proporcionados a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b04ce-188">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="b04ce-189">.NET Core puede ejecutarse en un contenedor de Docker.</span><span class="sxs-lookup"><span data-stu-id="b04ce-189">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="b04ce-190">Las imágenes oficiales de Docker en .NET Core se publican en el registro de contenedor de Microsoft (MCR) y se pueden encontrar en el [repositorio de Docker Hub para Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="b04ce-190">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="b04ce-191">Cada repositorio contiene imágenes para diferentes combinaciones de .NET (SDK o Runtime) y del sistema operativo que puede usar.</span><span class="sxs-lookup"><span data-stu-id="b04ce-191">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="b04ce-192">Microsoft ofrece imágenes que se adaptan a escenarios específicos.</span><span class="sxs-lookup"><span data-stu-id="b04ce-192">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="b04ce-193">Por ejemplo, el [repositorio de ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) proporciona imágenes que se compilan para ejecutar aplicaciones de ASP.NET Core en producción.</span><span class="sxs-lookup"><span data-stu-id="b04ce-193">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="b04ce-194">Para obtener más información sobre el uso de .NET Core en un contenedor de Docker, vea [Introducción a .NET y Docker](../docker/introduction.md) y [Ejemplos](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="b04ce-194">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="b04ce-195">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="b04ce-195">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="b04ce-196">[Tutorial: Tutorial Hola mundo](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="b04ce-196">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="b04ce-197">[Tutorial: Creación de una aplicación con Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="b04ce-197">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="b04ce-198">[Tutorial: Inclusión de una aplicación de .NET Core en un contenedor](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="b04ce-198">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="b04ce-199">[Trabajo con la certificación de macOS Catalina](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="b04ce-199">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="b04ce-200">[Tutorial: Introducción a macOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="b04ce-200">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="b04ce-201">[Tutorial: Creación de una aplicación con Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="b04ce-201">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="b04ce-202">[Tutorial: Inclusión de una aplicación de .NET Core en un contenedor](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="b04ce-202">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="b04ce-203">[Tutorial: Creación de una aplicación con Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="b04ce-203">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="b04ce-204">[Tutorial: Inclusión de una aplicación de .NET Core en un contenedor](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="b04ce-204">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

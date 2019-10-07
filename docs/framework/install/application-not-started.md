---
title: Solución del error "No se pudo iniciar esta aplicación"
description: Obtenga información sobre qué hacer si ve el cuadro de diálogo "No se pudo iniciar esta aplicación".
author: rpetrusha
ms.author: ronpet
ms.date: 09/05/2019
ms.openlocfilehash: 2534979e8dea886c2d7298c57e12b66d7a962c69
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71401285"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a><span data-ttu-id="6632a-103">Solución de un mensaje de error "No se pudo iniciar esta aplicación"</span><span class="sxs-lookup"><span data-stu-id="6632a-103">Troubleshooting a 'This application could not be started' error message</span></span>

<span data-ttu-id="6632a-104">Las aplicaciones que se desarrollan para .NET Framework suelen requerir que se instale una versión específica de .NET Framework en el sistema.</span><span class="sxs-lookup"><span data-stu-id="6632a-104">Applications that are developed for the .NET Framework typically require that a specific version of the .NET Framework be installed on your system.</span></span> <span data-ttu-id="6632a-105">En algunos casos, puede intentar ejecutar una aplicación sin una versión instalada ni la versión esperada de .NET Framework presente.</span><span class="sxs-lookup"><span data-stu-id="6632a-105">In some cases, you may attempt to run an application without either an installed version or the expected version of the .NET Framework present.</span></span> <span data-ttu-id="6632a-106">Esto suele generar un cuadro de diálogo de error similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="6632a-106">This often produces an error dialog box like the following:</span></span>

![No se pudo iniciar esta aplicación.](media/application-not-started/app-could-not-be-started.png)

<span data-ttu-id="6632a-108">Por lo general, esto indica una de las condiciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="6632a-108">This typically indicates one of the following conditions:</span></span>

- <span data-ttu-id="6632a-109">Se dañó una instalación de .NET Framework del sistema.</span><span class="sxs-lookup"><span data-stu-id="6632a-109">A .NET Framework installation on your system has become corrupted.</span></span>

- <span data-ttu-id="6632a-110">No se puede detectar la versión de .NET Framework que se necesita para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6632a-110">The version of the .NET Framework needed by your application cannot be detected.</span></span>

<span data-ttu-id="6632a-111">Para solucionar este problema de manera que pueda ejecutar la aplicación, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="6632a-111">To address this issue so that you can run your application, do the following:</span></span>

1. <span data-ttu-id="6632a-112">Descargue la [herramienta de reparación de .NET Framework (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span><span class="sxs-lookup"><span data-stu-id="6632a-112">Download the [.NET Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span></span> <span data-ttu-id="6632a-113">La herramienta se ejecuta automáticamente cuando se completa la descarga.</span><span class="sxs-lookup"><span data-stu-id="6632a-113">The tool runs automatically when the download completes.</span></span>

1. <span data-ttu-id="6632a-114">Si la herramienta de reparación de .NET Framework recomienda realizar cualquier acción adicional, como las que se muestran en la figura siguiente, seleccione **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="6632a-114">If the .NET Framework Repair Tool recommends any additional action, such as those shown in the following figure, select **Next**.</span></span>

   ![Cambios recomendados](media/application-not-started/repair-tool-recommended-changes.png)

1. <span data-ttu-id="6632a-116">La herramienta de reparación de .NET Framework muestra un cuadro de diálogo que se ve en la ilustración siguiente para indicar que se completaron los cambios.</span><span class="sxs-lookup"><span data-stu-id="6632a-116">The .NET Framework Repair Tools displays a dialog box shown in the following figure to indicate that changes are complete.</span></span> <span data-ttu-id="6632a-117">Deje abierto el cuadro de diálogo mientras vuelve a ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6632a-117">Leave the dialog box open while you to try rerun your application.</span></span> <span data-ttu-id="6632a-118">Esto debe realizarse correctamente si la herramienta de reparación de .NET Framework ha identificado y corregido una instalación dañada de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6632a-118">This should succeed if the .NET Framework Repair Tool has identified and corrected a corrupted .NET Framework installation.</span></span>

   ![Cambios recomendados](media/application-not-started/repair-tool-changes-complete.png)

1. <span data-ttu-id="6632a-120">Si la aplicación se ejecuta correctamente, seleccione el botón **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="6632a-120">If your application runs successfully, select the **Finish** button.</span></span> <span data-ttu-id="6632a-121">En caso contrario, seleccione el botón **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="6632a-121">Otherwise, select the **Next** button.</span></span>

1. <span data-ttu-id="6632a-122">Si seleccionó el botón **Siguiente**, la herramienta de reparación de .NET Framework muestra un cuadro de diálogo como el siguiente.</span><span class="sxs-lookup"><span data-stu-id="6632a-122">If you selected the **Next** button, the .NET Framework Repair Tool displays a a dialog box like the following.</span></span> <span data-ttu-id="6632a-123">Seleccione el botón **Finalizar** para enviar información de diagnóstico a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6632a-123">Select the **Finish** button to send diagnostic information to Microsoft.</span></span>

   ![No se puede resolver el problema](media/application-not-started/repair-tool-no-resolution.png)

1. <span data-ttu-id="6632a-125">Si sigue sin poder ejecutar la aplicación, instale la versión más reciente de .NET Framework compatible con su versión de Windows, tal como se muestra en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="6632a-125">If you still cannot run the application, install the latest version of the .NET Framework supported by your version of Windows, as shown in the following table.</span></span>

   |<span data-ttu-id="6632a-126">Versión de Windows</span><span class="sxs-lookup"><span data-stu-id="6632a-126">Windows version</span></span>|<span data-ttu-id="6632a-127">Instalación de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6632a-127">.NET Framework installation</span></span>|
   |---|---|
   |<span data-ttu-id="6632a-128">Actualización de aniversario de Windows 10 (versión 1607) o versiones posteriores</span><span class="sxs-lookup"><span data-stu-id="6632a-128">Windows 10 Anniversary Update and later versions</span></span>|[<span data-ttu-id="6632a-129">Tiempo de ejecución de .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="6632a-129">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="6632a-130">Windows 10, actualización de noviembre de Windows 10</span><span class="sxs-lookup"><span data-stu-id="6632a-130">Windows 10, Windows 10 November Update</span></span>|[<span data-ttu-id="6632a-131">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="6632a-131">.NET Framework 4.6.2</span></span>](https://www.microsoft.com/download/details.aspx?id=53345)|
   |<span data-ttu-id="6632a-132">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="6632a-132">Windows 8.1</span></span>|[<span data-ttu-id="6632a-133">Tiempo de ejecución de .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="6632a-133">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="6632a-134">Windows 8</span><span class="sxs-lookup"><span data-stu-id="6632a-134">Windows 8</span></span>|[<span data-ttu-id="6632a-135">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="6632a-135">.NET Framework 4.6.1</span></span>](https://www.microsoft.com/download/details.aspx?id=49981)|
   |<span data-ttu-id="6632a-136">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="6632a-136">Windows 7 SP1</span></span>|[<span data-ttu-id="6632a-137">Tiempo de ejecución de .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="6632a-137">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="6632a-138">Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="6632a-138">Windows Vista SP2</span></span>|[<span data-ttu-id="6632a-139">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="6632a-139">.NET Framework 4.6</span></span>](https://www.microsoft.com/download/details.aspx?id=48130)|

   > [!NOTE]
   >  <span data-ttu-id="6632a-140">.NET Framework 4.8 instalado previamente en la Actualización de mayo de 2019 de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="6632a-140">.NET Framework 4.8 is preinstalled on Windows 10 May 2019 Update.</span></span>

1. <span data-ttu-id="6632a-141">Intente iniciar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6632a-141">Attempt to launch the application.</span></span>

1. <span data-ttu-id="6632a-142">En algunos casos, puede ver un cuadro de diálogo como el siguiente, en el que se le pida que instale .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="6632a-142">In some cases, you may see a dialog box like the following, which asks you to install the .NET Framework 3.5.</span></span> <span data-ttu-id="6632a-143">Seleccione **Download and install this feature** (Descargar e instalar esta característica) para instalar .NET Framework 3.5 y vuelva a iniciar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6632a-143">Select **Download and install this feature** to install the .NET Framework 3.5, then launch the application again.</span></span>

   ![No se puede resolver el problema](media/application-not-started/install-3-5.png)

## <a name="see-also"></a><span data-ttu-id="6632a-145">Vea también</span><span class="sxs-lookup"><span data-stu-id="6632a-145">See also</span></span>

- [<span data-ttu-id="6632a-146">Requisitos del sistema de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6632a-146">.NET Framework System Requirements</span></span>](../get-started/system-requirements.md)
- [<span data-ttu-id="6632a-147">Guía de instalación de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6632a-147">.NET Framework installation guide</span></span>](index.md)
- [<span data-ttu-id="6632a-148">Solución de problemas en instalaciones y desinstalaciones bloqueadas de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6632a-148">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
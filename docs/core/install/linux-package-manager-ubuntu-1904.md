---
title: 'Instalación de .NET Core en el administrador de paquetes de Ubuntu 19.04: .NET Core'
description: Use un administrador de paquetes para instalar el SDK y el entorno de ejecución de .NET Core en Ubuntu 19.04.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 69bfc3395f5cd92ed54850e5ea8b76eba7f27d83
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74999054"
---
# <a name="ubuntu-1904-package-manager---install-net-core"></a><span data-ttu-id="bda1b-103">Administrador de paquetes de Ubuntu 19.04: instalación de .NET Core</span><span class="sxs-lookup"><span data-stu-id="bda1b-103">Ubuntu 19.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="bda1b-104">En este artículo se describe cómo usar un administrador de paquetes para instalar .NET Core en Ubuntu 19.04.</span><span class="sxs-lookup"><span data-stu-id="bda1b-104">This article describes how to use a package manager to install .NET Core on Ubuntu 19.04.</span></span> <span data-ttu-id="bda1b-105">Si va a instalar el entorno de ejecución, le recomendamos que instale el [entorno de ejecución de ASP.NET Core](#install-the-aspnet-core-runtime), ya que incluye los de .NET Core y ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="bda1b-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="bda1b-106">Registro de la clave y la fuente de Microsoft</span><span class="sxs-lookup"><span data-stu-id="bda1b-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="bda1b-107">Antes de instalar .NET, deberá realizar lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="bda1b-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="bda1b-108">Registrar clave de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bda1b-108">Register the Microsoft key</span></span>
- <span data-ttu-id="bda1b-109">Registrar el repositorio del producto.</span><span class="sxs-lookup"><span data-stu-id="bda1b-109">register the product repository</span></span>
- <span data-ttu-id="bda1b-110">Instalar las dependencias necesarias.</span><span class="sxs-lookup"><span data-stu-id="bda1b-110">Install required dependencies</span></span>

<span data-ttu-id="bda1b-111">Esto solo se debe hacer una vez por máquina.</span><span class="sxs-lookup"><span data-stu-id="bda1b-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="bda1b-112">Abra un terminal y ejecute los comandos siguientes.</span><span class="sxs-lookup"><span data-stu-id="bda1b-112">Open a terminal and run the following commands.</span></span>

```bash
wget -q https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="bda1b-113">Instalación del SDK de .NET Core</span><span class="sxs-lookup"><span data-stu-id="bda1b-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="bda1b-114">Actualice los productos disponibles para la instalación y, después, instale el SDK de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bda1b-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="bda1b-115">En el terminal, ejecute los comandos siguientes.</span><span class="sxs-lookup"><span data-stu-id="bda1b-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="bda1b-116">Si recibe un mensaje de error similar a **No se puede encontrar el paquete dotnet-sdk-3.1**, vea la sección [Solución de problemas del administrador de paquetes](#troubleshoot-the-package-manager).</span><span class="sxs-lookup"><span data-stu-id="bda1b-116">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="bda1b-117">Instalación del entorno de ejecución de ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bda1b-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="bda1b-118">Actualice los productos disponibles para la instalación y, después, instale el entorno de ejecución de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="bda1b-118">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="bda1b-119">En el terminal, ejecute los comandos siguientes.</span><span class="sxs-lookup"><span data-stu-id="bda1b-119">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="bda1b-120">Si recibe un mensaje de error similar a **No se puede encontrar el paquete aspnetcore-runtime-3.1**, vea la sección [Solución de problemas del administrador de paquetes](#troubleshoot-the-package-manager).</span><span class="sxs-lookup"><span data-stu-id="bda1b-120">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="bda1b-121">Instalación del entorno de ejecución de .NET Core</span><span class="sxs-lookup"><span data-stu-id="bda1b-121">Install the .NET Core runtime</span></span>

<span data-ttu-id="bda1b-122">Actualice los productos disponibles para la instalación y, después, instale el entorno de ejecución de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bda1b-122">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="bda1b-123">En el terminal, ejecute los comandos siguientes.</span><span class="sxs-lookup"><span data-stu-id="bda1b-123">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="bda1b-124">Si recibe un mensaje de error similar a **No se puede encontrar el paquete dotnet-runtime-3.1**, vea la sección [Solución de problemas del administrador de paquetes](#troubleshoot-the-package-manager).</span><span class="sxs-lookup"><span data-stu-id="bda1b-124">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="bda1b-125">Procedimiento para instalar otras versiones</span><span class="sxs-lookup"><span data-stu-id="bda1b-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="bda1b-126">Solución de problemas del administrador de paquetes</span><span class="sxs-lookup"><span data-stu-id="bda1b-126">Troubleshoot the package manager</span></span>

<span data-ttu-id="bda1b-127">Si recibe un mensaje de error similar a **No se puede encontrar el paquete (el paquete .NET Core)** , ejecute los comandos siguientes.</span><span class="sxs-lookup"><span data-stu-id="bda1b-127">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="bda1b-128">Si eso no funciona, puede ejecutar una instalación manual con los comandos siguientes.</span><span class="sxs-lookup"><span data-stu-id="bda1b-128">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/19.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```
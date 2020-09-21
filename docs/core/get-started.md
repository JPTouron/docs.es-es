---
title: Introducción a .NET Core
description: Encuentre recursos para aprender a crear aplicaciones .NET Core en Windows, Linux y macOS.
author: adegeo
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 6106f66dfbbe382ee9f61eb8b7bda70ab9b72d0b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538554"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="09b0a-103">Introducción a .NET Core</span><span class="sxs-lookup"><span data-stu-id="09b0a-103">Get started with .NET Core</span></span>

<span data-ttu-id="09b0a-104">En este artículo se proporciona información sobre cómo comenzar con .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09b0a-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="09b0a-105">.NET Core se puede instalar en Windows, Linux y macOS.</span><span class="sxs-lookup"><span data-stu-id="09b0a-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="09b0a-106">Puede programar en su editor de texto preferido y crear aplicaciones y bibliotecas multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="09b0a-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span>

<span data-ttu-id="09b0a-107">Si no está seguro de qué es .NET Core o cómo se relaciona con otras tecnologías .NET, comience con la información general [¿Qué es .NET?](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet).</span><span class="sxs-lookup"><span data-stu-id="09b0a-107">If you're unsure what .NET Core is or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="09b0a-108">En resumen, .NET Core es una implementación multiplataforma de código abierto de .NET.</span><span class="sxs-lookup"><span data-stu-id="09b0a-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="09b0a-109">Crear una aplicación</span><span class="sxs-lookup"><span data-stu-id="09b0a-109">Create an application</span></span>

<span data-ttu-id="09b0a-110">En primer lugar, descargue e instale el [SDK de .NET Core](https://dotnet.microsoft.com/download) en el equipo.</span><span class="sxs-lookup"><span data-stu-id="09b0a-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="09b0a-111">A continuación, abra un terminal como **PowerShell**, **Símbolo del sistema** o **bash**.</span><span class="sxs-lookup"><span data-stu-id="09b0a-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="09b0a-112">Escriba los comandos `dotnet` siguientes para crear y ejecutar una aplicación C#:</span><span class="sxs-lookup"><span data-stu-id="09b0a-112">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="09b0a-113">Debería ver los siguientes resultados:</span><span class="sxs-lookup"><span data-stu-id="09b0a-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="09b0a-114">¡Enhorabuena!</span><span class="sxs-lookup"><span data-stu-id="09b0a-114">Congratulations!</span></span> <span data-ttu-id="09b0a-115">Ha creado una sencilla aplicación .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09b0a-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="09b0a-116">También puede usar [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio ](./tutorials/with-visual-studio.md) (solo Windows) o [Visual Studio para Mac](tutorials/with-visual-studio-mac.md) (solo macOS), para crear una aplicación .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09b0a-116">You can also use [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/with-visual-studio-mac.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="09b0a-117">Tutoriales</span><span class="sxs-lookup"><span data-stu-id="09b0a-117">Tutorials</span></span>

<span data-ttu-id="09b0a-118">Para comenzar a desarrollar aplicaciones .NET Core, puede seguir estos tutoriales paso a paso:</span><span class="sxs-lookup"><span data-stu-id="09b0a-118">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="09b0a-119">Windows</span><span class="sxs-lookup"><span data-stu-id="09b0a-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="09b0a-120">Creación de su primera aplicación de consola con .NET Core en Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="09b0a-120">Create your first .NET Core console application in Visual Studio 2019</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="09b0a-121">Compilación de una biblioteca de clases con .NET Standard en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="09b0a-121">Build a class library with .NET Standard in Visual Studio</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="09b0a-122">Tutorial: Depuración de una aplicación de consola de .NET Core con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="09b0a-122">Tutorial: Create a .NET Core console app using Visual Studio Code</span></span>](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| <span data-ttu-id="09b0a-123">![icono de cámara de cine para vídeo](./media/video-icon.png "Ver un vídeo")</span><span class="sxs-lookup"><span data-stu-id="09b0a-123">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="09b0a-124">Vea el vídeo de Channel 9 sobre [cómo instalar y usar Visual Studio Code y .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span><span class="sxs-lookup"><span data-stu-id="09b0a-124">Watch the [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) video on Channel 9.</span></span> |
| <span data-ttu-id="09b0a-125">![icono de cámara de cine para vídeo](./media/video-icon.png "Ver un vídeo")</span><span class="sxs-lookup"><span data-stu-id="09b0a-125">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="09b0a-126">Vea los vídeos [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) en YouTube.</span><span class="sxs-lookup"><span data-stu-id="09b0a-126">Watch the [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) videos on YouTube.</span></span> |

<span data-ttu-id="09b0a-127">Vea el artículo [Dependencias y requisitos de .NET Core](./install/windows.md) para obtener una lista de las versiones de Windows admitidas.</span><span class="sxs-lookup"><span data-stu-id="09b0a-127">See the [.NET Core dependencies and requirements](./install/windows.md) article for a list of the supported Windows versions.</span></span>

# <a name="linux"></a>[<span data-ttu-id="09b0a-128">Linux</span><span class="sxs-lookup"><span data-stu-id="09b0a-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="09b0a-129">Para comenzar a desarrollar aplicaciones .NET Core, puede seguir estos tutoriales paso a paso:</span><span class="sxs-lookup"><span data-stu-id="09b0a-129">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="09b0a-130">Tutorial: Depuración de una aplicación de consola de .NET Core con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="09b0a-130">Tutorial: Create a .NET Core console app using Visual Studio Code</span></span>](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| <span data-ttu-id="09b0a-131">![icono de cámara de cine para vídeo](./media/video-icon.png "Ver un vídeo")</span><span class="sxs-lookup"><span data-stu-id="09b0a-131">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="09b0a-132">Vea un vídeo de [introducción a Visual Studio Code mediante C# y .NET Core en Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="09b0a-132">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span> |

<span data-ttu-id="09b0a-133">Vea el artículo [Dependencias y requisitos de .NET Core](./install/linux.md) para obtener una lista de las distribuciones y las versiones de Linux admitidas.</span><span class="sxs-lookup"><span data-stu-id="09b0a-133">See the [.NET Core dependencies and requirements](./install/linux.md) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macos"></a>[<span data-ttu-id="09b0a-134">macOS</span><span class="sxs-lookup"><span data-stu-id="09b0a-134">macOS</span></span>](#tab/macos)

<span data-ttu-id="09b0a-135">Para comenzar a desarrollar aplicaciones .NET Core, puede seguir estos tutoriales paso a paso:</span><span class="sxs-lookup"><span data-stu-id="09b0a-135">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="09b0a-136">Tutorial: Depuración de una aplicación de consola de .NET Core con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="09b0a-136">Tutorial: Create a .NET Core console application using Visual Studio Code</span></span>](tutorials/with-visual-studio-code.md)
- [<span data-ttu-id="09b0a-137">Tutorial: Creación de una aplicación de consola de .NET Core con Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="09b0a-137">Tutorial: Create a .NET Core console application using Visual Studio for Mac</span></span>](tutorials/with-visual-studio-mac.md)
- [<span data-ttu-id="09b0a-138">Creación de una biblioteca de .NET Standard en macOS mediante Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="09b0a-138">Build a .NET Standard library on macOS using Visual Studio for Mac</span></span>](tutorials/library-with-visual-studio-mac.md)

|   |   |
|---|---|
| <span data-ttu-id="09b0a-139">![icono de cámara de cine para vídeo](media/video-icon.png "Ver un vídeo")</span><span class="sxs-lookup"><span data-stu-id="09b0a-139">![movie camera icon for video](media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="09b0a-140">Vea un vídeo de [introducción a Visual Studio Code mediante C# y .NET Core en macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span><span class="sxs-lookup"><span data-stu-id="09b0a-140">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span> |

<span data-ttu-id="09b0a-141">Vea el artículo [Dependencias y requisitos de .NET Core](./install/macos.md) para obtener una lista de las versiones de OS X / macOS admitidas.</span><span class="sxs-lookup"><span data-stu-id="09b0a-141">See the [.NET Core dependencies and requirements](./install/macos.md) article for a list of the supported OS X / macOS versions.</span></span>

---

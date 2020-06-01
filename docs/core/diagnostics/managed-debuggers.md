---
title: 'Depuradores administrados: .NET Core'
description: Información general de los depuradores administrados de Visual Studio y Visual Studio Code.
ms.date: 08/05/2019
ms.openlocfilehash: 28cc21980bc78234f7af3b4668e2fa77fbf8ce5b
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2020
ms.locfileid: "84200855"
---
# <a name="net-core-managed-debuggers"></a><span data-ttu-id="bc8ec-103">Depuradores administrados de .Net Core</span><span class="sxs-lookup"><span data-stu-id="bc8ec-103">.NET Core managed debuggers</span></span>

<span data-ttu-id="bc8ec-104">Los depuradores permiten a los programas pausarse o ejecutarse paso a paso.</span><span class="sxs-lookup"><span data-stu-id="bc8ec-104">Debuggers allow programs to be paused or executed step-by-step.</span></span> <span data-ttu-id="bc8ec-105">Cuando se pausa, se puede ver el estado actual del proceso.</span><span class="sxs-lookup"><span data-stu-id="bc8ec-105">When paused, the current state of the process can be viewed.</span></span> <span data-ttu-id="bc8ec-106">Al recorrer las secciones clave, se entiende mejor el código y el motivo por el que genera determinado resultado.</span><span class="sxs-lookup"><span data-stu-id="bc8ec-106">By stepping through key sections, you gain understanding of your code and why it produces the result that it does.</span></span>

<span data-ttu-id="bc8ec-107">Microsoft proporciona depuradores para código administrado en **Visual Studio** y **Visual Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="bc8ec-107">Microsoft provides debuggers for managed code in **Visual Studio** and **Visual Studio Code**.</span></span>

## <a name="visual-studio-managed-debugger"></a><span data-ttu-id="bc8ec-108">Depurador administrado de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bc8ec-108">Visual Studio managed debugger</span></span>

<span data-ttu-id="bc8ec-109">**Visual Studio**  es un entorno de desarrollo integrado con el depurador más completo disponible.</span><span class="sxs-lookup"><span data-stu-id="bc8ec-109">**Visual Studio** is an integrated development environment with the most comprehensive debugger available.</span></span> <span data-ttu-id="bc8ec-110">Visual Studio es una opción excelente para los desarrolladores que trabajan en Windows.</span><span class="sxs-lookup"><span data-stu-id="bc8ec-110">Visual Studio is an excellent choice for developers working on Windows.</span></span>

- [<span data-ttu-id="bc8ec-111">Tutorial: Depuración de una aplicación .NET Core en Windows con Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bc8ec-111">Tutorial - Debugging a .NET Core application on Windows with Visual Studio</span></span>](../tutorials/debugging-with-visual-studio.md)

<span data-ttu-id="bc8ec-112">Aunque Visual Studio es una aplicación de Windows, se puede usar para depurar aplicaciones de Linux y macOS de forma remota.</span><span class="sxs-lookup"><span data-stu-id="bc8ec-112">While Visual Studio is a Windows application, it can still be used to debug Linux and macOS apps remotely.</span></span>

- [<span data-ttu-id="bc8ec-113">Depuración de una aplicación .NET Core en Linux/OSX con Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bc8ec-113">Debugging a .NET Core application on Linux/OSX with Visual Studio</span></span>](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 <span data-ttu-id="bc8ec-114">La depuración de aplicaciones ASP.NET Core requiere instrucciones ligeramente distintas.</span><span class="sxs-lookup"><span data-stu-id="bc8ec-114">Debugging ASP.NET Core apps require slightly different instructions.</span></span>

- [<span data-ttu-id="bc8ec-115">Depuración de aplicaciones ASP.NET Core en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bc8ec-115">Debug ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a><span data-ttu-id="bc8ec-116">Depurador administrado de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="bc8ec-116">Visual Studio Code managed debugger</span></span>

<span data-ttu-id="bc8ec-117">**Visual Studio Code** es un editor de código ligero y multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="bc8ec-117">**Visual Studio Code** is a lightweight cross-platform code editor.</span></span> <span data-ttu-id="bc8ec-118">Usa la misma implementación de depurador de .NET Core que Visual Studio, pero con una interfaz de usuario simplificada.</span><span class="sxs-lookup"><span data-stu-id="bc8ec-118">It uses the same .NET Core debugger implementation as Visual Studio, but with a simplified user interface.</span></span>

- [<span data-ttu-id="bc8ec-119">Tutorial: Depuración de una aplicación .NET Core con Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bc8ec-119">Tutorial - Debugging a .NET Core application with Visual Studio Code</span></span>](../tutorials/debugging-with-visual-studio-code.md)
- <span data-ttu-id="bc8ec-120">[Debugging in Visual Studio Code](https://code.visualstudio.com/docs/editor/debugging) (Depuración en Visual Studio Code)</span><span class="sxs-lookup"><span data-stu-id="bc8ec-120">[Debugging in Visual Studio Code](https://code.visualstudio.com/docs/editor/debugging)</span></span>

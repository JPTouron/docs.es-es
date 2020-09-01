---
ms.openlocfilehash: 115cd6be935ae12a1293f948a0f899c6c3ff0d78
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608468"
---
### <a name="winhttphandler-removed-from-net-runtime"></a><span data-ttu-id="3f4de-101">WinHttpHandler quitado del entorno de ejecución de .NET</span><span class="sxs-lookup"><span data-stu-id="3f4de-101">WinHttpHandler removed from .NET runtime</span></span>

<span data-ttu-id="3f4de-102">La clase `WinHttpHandler` se ha quitado del ensamblado *System.Net.Http.dll*.</span><span class="sxs-lookup"><span data-stu-id="3f4de-102">The `WinHttpHandler` class was removed from the *System.Net.Http.dll* assembly.</span></span> <span data-ttu-id="3f4de-103">Ahora solo está disponible como un [paquete NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/) fuera de banda (OOB).</span><span class="sxs-lookup"><span data-stu-id="3f4de-103">It's now available only as an out-of-band (OOB) [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3f4de-104">Versión introducida</span><span class="sxs-lookup"><span data-stu-id="3f4de-104">Version introduced</span></span>

<span data-ttu-id="3f4de-105">5.0</span><span class="sxs-lookup"><span data-stu-id="3f4de-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="3f4de-106">Descripción del cambio</span><span class="sxs-lookup"><span data-stu-id="3f4de-106">Change description</span></span>

<span data-ttu-id="3f4de-107">En versiones anteriores de .NET, la clase <xref:System.Net.Http.WinHttpHandler> está disponible como parte de las bibliotecas básicas de .NET.</span><span class="sxs-lookup"><span data-stu-id="3f4de-107">In previous .NET versions, the <xref:System.Net.Http.WinHttpHandler> class is available as part of the core .NET libraries.</span></span> <span data-ttu-id="3f4de-108">A partir de .NET 5.0, la clase solo está disponible como un <xref:System.Net.Http.WinHttpHandler>[paquete NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/) instalado por separado.</span><span class="sxs-lookup"><span data-stu-id="3f4de-108">Starting in .NET 5.0, the <xref:System.Net.Http.WinHttpHandler> class is only available as a separately installed [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3f4de-109">Acción recomendada</span><span class="sxs-lookup"><span data-stu-id="3f4de-109">Recommended action</span></span>

<span data-ttu-id="3f4de-110">Instale el [paquete NuGet System.Net.Http.WinHttpHandler](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span><span class="sxs-lookup"><span data-stu-id="3f4de-110">Install the [System.Net.Http.WinHttpHandler NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span> <span data-ttu-id="3f4de-111">O bien, si no necesita características específicas de WinHTTP, use <xref:System.Net.Http.SocketsHttpHandler> en su lugar.</span><span class="sxs-lookup"><span data-stu-id="3f4de-111">Or, if you don't require WinHTTP-specific features, use <xref:System.Net.Http.SocketsHttpHandler> instead.</span></span>

#### <a name="category"></a><span data-ttu-id="3f4de-112">Categoría</span><span class="sxs-lookup"><span data-stu-id="3f4de-112">Category</span></span>

<span data-ttu-id="3f4de-113">Redes</span><span class="sxs-lookup"><span data-stu-id="3f4de-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3f4de-114">API afectadas</span><span class="sxs-lookup"><span data-stu-id="3f4de-114">Affected APIs</span></span>

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

-->
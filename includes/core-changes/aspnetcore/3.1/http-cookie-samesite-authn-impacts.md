---
ms.openlocfilehash: 8b6d334677991382d235fd53cd3c98e3a77d650d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539623"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a><span data-ttu-id="a6360-101">HTTP: Los cambios de SameSite en los exploradores afectan a la autenticación.</span><span class="sxs-lookup"><span data-stu-id="a6360-101">HTTP: Browser SameSite changes impact authentication</span></span>

<span data-ttu-id="a6360-102">Algunos exploradores, como Chrome y Firefox, han realizado cambios importantes en sus implementaciones de `SameSite` para las cookies.</span><span class="sxs-lookup"><span data-stu-id="a6360-102">Some browsers, such as Chrome and Firefox, made breaking changes to their implementations of `SameSite` for cookies.</span></span> <span data-ttu-id="a6360-103">Los cambios afectan a escenarios de autenticación remota, como OpenID Connect y WS-Federation, que deben no participar mediante el envío de `SameSite=None`.</span><span class="sxs-lookup"><span data-stu-id="a6360-103">The changes impact remote authentication scenarios, such as OpenID Connect and WS-Federation, which must opt out by sending `SameSite=None`.</span></span> <span data-ttu-id="a6360-104">Sin embargo, `SameSite=None` se interrumpe en iOS 12 y en algunas versiones anteriores de otros exploradores.</span><span class="sxs-lookup"><span data-stu-id="a6360-104">However, `SameSite=None` breaks on iOS 12 and some older versions of other browsers.</span></span> <span data-ttu-id="a6360-105">La aplicación debe detectar estas versiones y omitir `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="a6360-105">The app needs to sniff these versions and omit `SameSite`.</span></span>

<span data-ttu-id="a6360-106">Para obtener información sobre esta incidencia, vea [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span><span class="sxs-lookup"><span data-stu-id="a6360-106">For discussion on this issue, see [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a6360-107">Versión introducida</span><span class="sxs-lookup"><span data-stu-id="a6360-107">Version introduced</span></span>

<span data-ttu-id="a6360-108">3.1, versión preliminar 1</span><span class="sxs-lookup"><span data-stu-id="a6360-108">3.1 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a6360-109">Comportamiento anterior</span><span class="sxs-lookup"><span data-stu-id="a6360-109">Old behavior</span></span>

<span data-ttu-id="a6360-110">`SameSite` es una extensión de proyecto de norma de 2016 para cookies HTTP.</span><span class="sxs-lookup"><span data-stu-id="a6360-110">`SameSite` is a 2016 draft standard extension to HTTP cookies.</span></span> <span data-ttu-id="a6360-111">Su objetivo era mitigar la falsificación de solicitud entre sitios (CSRF).</span><span class="sxs-lookup"><span data-stu-id="a6360-111">It's intended to mitigate Cross-Site Request Forgery (CSRF).</span></span> <span data-ttu-id="a6360-112">Originalmente se diseñó como una característica en la que los servidores participaban si agregaban los nuevos parámetros.</span><span class="sxs-lookup"><span data-stu-id="a6360-112">This was originally designed as a feature the servers would opt into by adding the new parameters.</span></span> <span data-ttu-id="a6360-113">ASP.NET Core 2.0 agregó compatibilidad inicial con `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="a6360-113">ASP.NET Core 2.0 added initial support for `SameSite`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a6360-114">Comportamiento nuevo</span><span class="sxs-lookup"><span data-stu-id="a6360-114">New behavior</span></span>

<span data-ttu-id="a6360-115">Google ha propuesto un nuevo proyecto de norma que no es compatible con versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="a6360-115">Google proposed a new draft standard that isn't backwards compatible.</span></span> <span data-ttu-id="a6360-116">La norma cambia el modo predeterminado a `Lax` y agrega una nueva entrada `None` para no participar. `Lax` basta para la mayoría de las cookies de aplicación, aunque interrumpe escenarios entre sitios como el inicio de sesión de OpenID Connect y WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="a6360-116">The standard changes the default mode to `Lax` and adds a new entry `None` to opt out. `Lax` suffices for most app cookies; however, it breaks cross-site scenarios like OpenID Connect and WS-Federation login.</span></span> <span data-ttu-id="a6360-117">La mayoría de los inicios de sesión de OAuth no se ven afectados debido a las diferencias respecto al flujo de la solicitud.</span><span class="sxs-lookup"><span data-stu-id="a6360-117">Most OAuth logins aren't affected because of differences in how the request flows.</span></span> <span data-ttu-id="a6360-118">El nuevo parámetro `None` origina problemas de compatibilidad con los clientes que han implementado el proyecto de norma anterior (por ejemplo, iOS 12).</span><span class="sxs-lookup"><span data-stu-id="a6360-118">The new `None` parameter causes compatibility problems with clients that implemented the prior draft standard (for example, iOS 12).</span></span> <span data-ttu-id="a6360-119">Chrome 80 va a incluir los cambios.</span><span class="sxs-lookup"><span data-stu-id="a6360-119">Chrome 80 will include the changes.</span></span> <span data-ttu-id="a6360-120">Vea [Actualizaciones de SameSite](https://www.chromium.org/updates/same-site) para conocer la escala de tiempo de lanzamiento del producto Chrome.</span><span class="sxs-lookup"><span data-stu-id="a6360-120">See [SameSite Updates](https://www.chromium.org/updates/same-site) for the Chrome product launch timeline.</span></span>

<span data-ttu-id="a6360-121">ASP.NET Core 3.1 se ha actualizado para implementar el nuevo comportamiento de `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="a6360-121">ASP.NET Core 3.1 has been updated to implement the new `SameSite` behavior.</span></span> <span data-ttu-id="a6360-122">La actualización vuelve a definir el comportamiento de `SameSiteMode.None` para emitir `SameSite=None` y agrega un nuevo valor `SameSiteMode.Unspecified` para omitir el atributo `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="a6360-122">The update redefines the behavior of `SameSiteMode.None` to emit `SameSite=None` and adds a new value `SameSiteMode.Unspecified` to omit the `SameSite` attribute.</span></span> <span data-ttu-id="a6360-123">Todas las API de cookies ahora tienen como valor predeterminado `Unspecified`, aunque algunos componentes que usan cookies establecen valores más específicos en sus escenarios, como la correlación de OpenID Connect y las cookies nonce.</span><span class="sxs-lookup"><span data-stu-id="a6360-123">All cookie APIs now default to `Unspecified`, though some components that use cookies set values more specific to their scenarios such as the OpenID Connect correlation and nonce cookies.</span></span>

<span data-ttu-id="a6360-124">Para obtener información sobre otros cambios recientes en esta área, vea [HTTP: Cambio a Ninguno de algunos valores predeterminados de cookie de SameSite](../../../../docs/core/compatibility/2.2-3.0.md#http-some-cookie-samesite-defaults-changed-to-none).</span><span class="sxs-lookup"><span data-stu-id="a6360-124">For other recent changes in this area, see [HTTP: Some cookie SameSite defaults changed to None](../../../../docs/core/compatibility/2.2-3.0.md#http-some-cookie-samesite-defaults-changed-to-none).</span></span> <span data-ttu-id="a6360-125">En ASP.NET Core 3.0, la mayoría de los valores predeterminados se han cambiado de <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> a <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType>, aunque se sigue usando la norma anterior.</span><span class="sxs-lookup"><span data-stu-id="a6360-125">In ASP.NET Core 3.0, most defaults were changed from <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> to <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (but still using the prior standard).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a6360-126">Motivo del cambio</span><span class="sxs-lookup"><span data-stu-id="a6360-126">Reason for change</span></span>

<span data-ttu-id="a6360-127">Cambios en el explorador y la especificación, como se ha explicado en el texto anterior.</span><span class="sxs-lookup"><span data-stu-id="a6360-127">Browser and specification changes as outlined in the preceding text.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a6360-128">Acción recomendada</span><span class="sxs-lookup"><span data-stu-id="a6360-128">Recommended action</span></span>

<span data-ttu-id="a6360-129">Las aplicaciones que interactúan con sitios remotos, por ejemplo mediante inicio de sesión de terceros, necesitan:</span><span class="sxs-lookup"><span data-stu-id="a6360-129">Apps that interact with remote sites, such as through third-party login, need to:</span></span>

* <span data-ttu-id="a6360-130">Probar esos escenarios en varios exploradores.</span><span class="sxs-lookup"><span data-stu-id="a6360-130">Test those scenarios on multiple browsers.</span></span>
* <span data-ttu-id="a6360-131">Aplicar la mitigación de detección de exploradores de la directiva de cookies tratada en [Compatibilidad con exploradores anteriores](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="a6360-131">Apply the cookie policy browser sniffing mitigation discussed in [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="a6360-132">Para obtener instrucciones para las pruebas y la detección de exploradores, vea la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="a6360-132">For testing and browser sniffing instructions, see the following section.</span></span>

##### <a name="determine-if-youre-affected"></a><span data-ttu-id="a6360-133">Procedimiento para determinar la afectación</span><span class="sxs-lookup"><span data-stu-id="a6360-133">Determine if you're affected</span></span>

<span data-ttu-id="a6360-134">Pruebe la aplicación web con una versión cliente que pueda participar en el nuevo comportamiento.</span><span class="sxs-lookup"><span data-stu-id="a6360-134">Test your web app using a client version that can opt into the new behavior.</span></span> <span data-ttu-id="a6360-135">Chrome, Firefox y Microsoft Edge Chromium tienen nuevas marcas de características de participación que se pueden usar para las pruebas.</span><span class="sxs-lookup"><span data-stu-id="a6360-135">Chrome, Firefox, and Microsoft Edge Chromium all have new opt-in feature flags that can be used for testing.</span></span> <span data-ttu-id="a6360-136">Compruebe que la aplicación es compatible con versiones cliente anteriores después de haber aplicado las revisiones, especialmente en el caso de Safari.</span><span class="sxs-lookup"><span data-stu-id="a6360-136">Verify that your app is compatible with older client versions after you've applied the patches, especially Safari.</span></span> <span data-ttu-id="a6360-137">Para obtener más información, vea [Compatibilidad con exploradores anteriores](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="a6360-137">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="chrome"></a><span data-ttu-id="a6360-138">Chrome</span><span class="sxs-lookup"><span data-stu-id="a6360-138">Chrome</span></span>

<span data-ttu-id="a6360-139">Chrome 78 y versiones posteriores generan resultados de prueba engañosos.</span><span class="sxs-lookup"><span data-stu-id="a6360-139">Chrome 78 and later yield misleading test results.</span></span> <span data-ttu-id="a6360-140">Esas versiones tienen aplicada una mitigación temporal y permiten las cookies con menos de dos minutos de antigüedad.</span><span class="sxs-lookup"><span data-stu-id="a6360-140">Those versions have a temporary mitigation in place and allow cookies less than two minutes old.</span></span> <span data-ttu-id="a6360-141">Con las marcas de prueba adecuadas habilitadas, Chrome 76 y 77 generan resultados más precisos.</span><span class="sxs-lookup"><span data-stu-id="a6360-141">With the appropriate test flags enabled, Chrome 76 and 77 yield more accurate results.</span></span> <span data-ttu-id="a6360-142">Para probar el nuevo comportamiento, cambie `chrome://flags/#same-site-by-default-cookies` a habilitado.</span><span class="sxs-lookup"><span data-stu-id="a6360-142">To test the new behavior, toggle `chrome://flags/#same-site-by-default-cookies` to enabled.</span></span> <span data-ttu-id="a6360-143">Se ha notificado que en Chrome 75 y versiones anteriores se produce un error con el nuevo valor `None`.</span><span class="sxs-lookup"><span data-stu-id="a6360-143">Chrome 75 and earlier are reported to fail with the new `None` setting.</span></span> <span data-ttu-id="a6360-144">Para obtener más información, vea [Compatibilidad con exploradores anteriores](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="a6360-144">For more information, see [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="a6360-145">Google no tiene disponibles versiones anteriores de Chrome.</span><span class="sxs-lookup"><span data-stu-id="a6360-145">Google doesn't make older Chrome versions available.</span></span> <span data-ttu-id="a6360-146">Sin embargo, puede descargar versiones anteriores de Chromium, lo que basta para las pruebas.</span><span class="sxs-lookup"><span data-stu-id="a6360-146">You can, however, download older versions of Chromium, which will suffice for testing.</span></span> <span data-ttu-id="a6360-147">Siga las instrucciones de [Descargar Chromium](https://www.chromium.org/getting-involved/download-chromium).</span><span class="sxs-lookup"><span data-stu-id="a6360-147">Follow the instructions at [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span></span>

* [<span data-ttu-id="a6360-148">Chromium 76 Win64</span><span class="sxs-lookup"><span data-stu-id="a6360-148">Chromium 76 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [<span data-ttu-id="a6360-149">Chromium 74 Win64</span><span class="sxs-lookup"><span data-stu-id="a6360-149">Chromium 74 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a><span data-ttu-id="a6360-150">Safari</span><span class="sxs-lookup"><span data-stu-id="a6360-150">Safari</span></span>

<span data-ttu-id="a6360-151">Safari 12 ha implementado estrictamente el proyecto anterior, con lo que se produce un error si se detecta el nuevo valor `None` en las cookies.</span><span class="sxs-lookup"><span data-stu-id="a6360-151">Safari 12 strictly implemented the prior draft and fails if it sees the new `None` value in cookies.</span></span> <span data-ttu-id="a6360-152">Esto se debe evitar con el código de detección de exploradores mostrado en [Compatibilidad con exploradores anteriores](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="a6360-152">This must be avoided via the browser sniffing code shown in [Support older browsers](#support-older-browsers).</span></span> <span data-ttu-id="a6360-153">Asegúrese de probar Safari 12 y 13, así como los inicios de sesión de estilo sistema operativo basados en WebKit mediante la Biblioteca de autenticación de Microsoft (MSAL), la Biblioteca de autenticación de Active Directory (ADAL) o cualquier biblioteca que esté usando.</span><span class="sxs-lookup"><span data-stu-id="a6360-153">Ensure you test Safari 12 and 13 as well as WebKit-based, OS-style logins using Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL), or whichever library you're using.</span></span> <span data-ttu-id="a6360-154">El problema depende de la versión del sistema operativo subyacente.</span><span class="sxs-lookup"><span data-stu-id="a6360-154">The problem is dependent on the underlying OS version.</span></span> <span data-ttu-id="a6360-155">Se sabe que OSX Mojave 10.14 e iOS 12 tienen problemas de compatibilidad con el nuevo comportamiento.</span><span class="sxs-lookup"><span data-stu-id="a6360-155">OSX Mojave 10.14 and iOS 12 are known to have compatibility problems with the new behavior.</span></span> <span data-ttu-id="a6360-156">La actualización a OSX Catalina 10.15 o iOS 13 corrige el problema.</span><span class="sxs-lookup"><span data-stu-id="a6360-156">Upgrading to OSX Catalina 10.15 or iOS 13 fixes the problem.</span></span> <span data-ttu-id="a6360-157">Safari no tiene actualmente una marca de participación para probar el comportamiento de la nueva especificación.</span><span class="sxs-lookup"><span data-stu-id="a6360-157">Safari doesn't currently have an opt-in flag for testing the new specification behavior.</span></span>

##### <a name="firefox"></a><span data-ttu-id="a6360-158">Firefox</span><span class="sxs-lookup"><span data-stu-id="a6360-158">Firefox</span></span>

<span data-ttu-id="a6360-159">La compatibilidad de Firefox con la nueva norma se puede probar en la versión 68 y posteriores mediante la participación en la página `about:config` con la marca de características `network.cookie.sameSite.laxByDefault`.</span><span class="sxs-lookup"><span data-stu-id="a6360-159">Firefox support for the new standard can be tested on version 68 and later by opting in on the `about:config` page with the feature flag `network.cookie.sameSite.laxByDefault`.</span></span> <span data-ttu-id="a6360-160">No se han comunicado problemas de compatibilidad en versiones anteriores de Firefox.</span><span class="sxs-lookup"><span data-stu-id="a6360-160">No compatibility issues have been reported on older versions of Firefox.</span></span>

##### <a name="microsoft-edge"></a><span data-ttu-id="a6360-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="a6360-161">Microsoft Edge</span></span>

<span data-ttu-id="a6360-162">Aunque Microsoft Edge admite la antigua norma `SameSite`, a partir de la versión 44 no tiene ningún problema de compatibilidad con la nueva.</span><span class="sxs-lookup"><span data-stu-id="a6360-162">While Microsoft Edge supports the old `SameSite` standard, as of version 44 it didn't have any compatibility problems with the new standard.</span></span>

##### <a name="microsoft-edge-chromium"></a><span data-ttu-id="a6360-163">Microsoft Edge Chromium</span><span class="sxs-lookup"><span data-stu-id="a6360-163">Microsoft Edge Chromium</span></span>

<span data-ttu-id="a6360-164">La marca de características es `edge://flags/#same-site-by-default-cookies`.</span><span class="sxs-lookup"><span data-stu-id="a6360-164">The feature flag is `edge://flags/#same-site-by-default-cookies`.</span></span> <span data-ttu-id="a6360-165">No se ha observado ningún problema de compatibilidad al realizar pruebas con Microsoft Edge Chromium 78.</span><span class="sxs-lookup"><span data-stu-id="a6360-165">No compatibility issues were observed when testing with Microsoft Edge Chromium 78.</span></span>

##### <a name="electron"></a><span data-ttu-id="a6360-166">Electron</span><span class="sxs-lookup"><span data-stu-id="a6360-166">Electron</span></span>

<span data-ttu-id="a6360-167">Las versiones de Electron incluyen versiones anteriores de Chromium.</span><span class="sxs-lookup"><span data-stu-id="a6360-167">Versions of Electron include older versions of Chromium.</span></span> <span data-ttu-id="a6360-168">Por ejemplo, la versión de Electron usada por Microsoft Teams es Chromium 66, que exhibe el comportamiento anterior.</span><span class="sxs-lookup"><span data-stu-id="a6360-168">For example, the version of Electron used by Microsoft Teams is Chromium 66, which exhibits the older behavior.</span></span> <span data-ttu-id="a6360-169">Realice sus propias pruebas de compatibilidad con la versión de Electron que use el producto.</span><span class="sxs-lookup"><span data-stu-id="a6360-169">Perform your own compatibility testing with the version of Electron your product uses.</span></span> <span data-ttu-id="a6360-170">Para obtener más información, vea [Compatibilidad con exploradores anteriores](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="a6360-170">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="support-older-browsers"></a><span data-ttu-id="a6360-171">Compatibilidad con exploradores anteriores</span><span class="sxs-lookup"><span data-stu-id="a6360-171">Support older browsers</span></span>

<span data-ttu-id="a6360-172">La norma `SameSite` de 2016 obligaba a tratar los valores desconocidos como valores `SameSite=Strict`.</span><span class="sxs-lookup"><span data-stu-id="a6360-172">The 2016 `SameSite` standard mandated that unknown values be treated as `SameSite=Strict` values.</span></span> <span data-ttu-id="a6360-173">Por tanto, los exploradores anteriores que admiten la norma original se pueden interrumpir al detectar una propiedad `SameSite` con un valor de `None`.</span><span class="sxs-lookup"><span data-stu-id="a6360-173">Consequently, any older browsers that support the original standard may break when they see a `SameSite` property with a value of `None`.</span></span> <span data-ttu-id="a6360-174">Las aplicaciones web deben implementar la detección de exploradores si pretenden admitir estos exploradores antiguos.</span><span class="sxs-lookup"><span data-stu-id="a6360-174">Web apps must implement browser sniffing if they intend to support these old browsers.</span></span> <span data-ttu-id="a6360-175">ASP.NET Core no implementa la detección de exploradores automáticamente porque los valores de encabezado de solicitud `User-Agent` son muy inestables y cambian semanalmente.</span><span class="sxs-lookup"><span data-stu-id="a6360-175">ASP.NET Core doesn't implement browser sniffing for you because `User-Agent` request header values are highly unstable and change on a weekly basis.</span></span> <span data-ttu-id="a6360-176">En su lugar, un punto de extensión de la directiva de cookies permite agregar lógica específica de `User-Agent`.</span><span class="sxs-lookup"><span data-stu-id="a6360-176">Instead, an extension point in the cookie policy allows you to add `User-Agent`-specific logic.</span></span>

<span data-ttu-id="a6360-177">En *Startup.cs*, agregue el siguiente código:</span><span class="sxs-lookup"><span data-stu-id="a6360-177">In *Startup.cs*, add the following code:</span></span>

```csharp
private void CheckSameSite(HttpContext httpContext, CookieOptions options)
{
    if (options.SameSite == SameSiteMode.None)
    {
        var userAgent = httpContext.Request.Headers["User-Agent"].ToString();
        // TODO: Use your User Agent library of choice here.
        if (/* UserAgent doesn't support new behavior */)
        {
            options.SameSite = SameSiteMode.Unspecified;
        }
    }
}

public void ConfigureServices(IServiceCollection services)
{
    services.Configure<CookiePolicyOptions>(options =>
    {
        options.MinimumSameSitePolicy = SameSiteMode.Unspecified;
        options.OnAppendCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
        options.OnDeleteCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
    });
}

public void Configure(IApplicationBuilder app)
{
    // Before UseAuthentication or anything else that writes cookies.
    app.UseCookiePolicy();

    app.UseAuthentication();
    // code omitted for brevity
}
```

##### <a name="opt-out-switches"></a><span data-ttu-id="a6360-178">Modificadores de no participación</span><span class="sxs-lookup"><span data-stu-id="a6360-178">Opt-out switches</span></span>

<span data-ttu-id="a6360-179">El modificador de compatibilidad `Microsoft.AspNetCore.SuppressSameSiteNone` permite no participar temporalmente en el nuevo comportamiento de cookies de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a6360-179">The `Microsoft.AspNetCore.SuppressSameSiteNone` compatibility switch enables you to temporarily opt out of the new ASP.NET Core cookie behavior.</span></span> <span data-ttu-id="a6360-180">Agregue el siguiente JSON a un archivo *runtimeconfig.template.json* del proyecto:</span><span class="sxs-lookup"><span data-stu-id="a6360-180">Add the following JSON to a *runtimeconfig.template.json* file in your project:</span></span>

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a><span data-ttu-id="a6360-181">Otras versiones</span><span class="sxs-lookup"><span data-stu-id="a6360-181">Other Versions</span></span>

<span data-ttu-id="a6360-182">Próximamente habrá revisiones de `SameSite` relacionadas para:</span><span class="sxs-lookup"><span data-stu-id="a6360-182">Related `SameSite` patches are forthcoming for:</span></span>

* <span data-ttu-id="a6360-183">ASP.NET Core 2.1, 2.2 y 3.0</span><span class="sxs-lookup"><span data-stu-id="a6360-183">ASP.NET Core 2.1, 2.2, and 3.0</span></span>
* <span data-ttu-id="a6360-184">`Microsoft.Owin` 4.1</span><span class="sxs-lookup"><span data-stu-id="a6360-184">`Microsoft.Owin` 4.1</span></span>
* <span data-ttu-id="a6360-185">`System.Web` (para .NET Framework 4.7.2 y posterior)</span><span class="sxs-lookup"><span data-stu-id="a6360-185">`System.Web` (for .NET Framework 4.7.2 and later)</span></span>

#### <a name="category"></a><span data-ttu-id="a6360-186">Categoría</span><span class="sxs-lookup"><span data-stu-id="a6360-186">Category</span></span>

<span data-ttu-id="a6360-187">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a6360-187">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a6360-188">API afectadas</span><span class="sxs-lookup"><span data-stu-id="a6360-188">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieBuilder.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieOptions.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`
- `Overload:Microsoft.AspNetCore.Http.CookieBuilder.SameSite`
- `Overload:Microsoft.AspNetCore.Http.CookieOptions.SameSite`
- `T:Microsoft.AspNetCore.Http.SameSiteMode`
- `T:Microsoft.Net.Http.Headers.SameSiteMode`
- `Overload:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite`

-->

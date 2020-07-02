---
ms.openlocfilehash: bd656478a55856e676853e57f3e7386ea0aa0211
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614827"
---
### <a name="currentculture-is-not-preserved-across-wpf-dispatcher-operations"></a>CurrentCulture no se conserva entre operaciones del distribuidor de WPF

#### <a name="details"></a>Detalles

A partir de .NET Framework 4.6, los cambios efectuados en <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> o <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> dentro de un <xref:System.Windows.Threading.Dispatcher?displayProperty=fullName> se perderán al final de la operación de ese distribuidor. De igual forma, es posible que los cambios en <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> o <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> realizados fuera de una operación de distribuidor no surtan efecto cuando que se ejecuta esa operación. En términos prácticos, esto significa que es posible que los cambios en <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> y <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> no fluyan entre las devoluciones de llamada de la interfaz de usuario de WPF y otro código de una aplicación de WPF. Esto se debe a un cambio en <xref:System.Threading.ExecutionContext?displayProperty=fullName> que hace que <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> y <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> se almacenen en el contexto de ejecución a partir de las aplicaciones destinadas a .NET Framework 4.6. Las operaciones de distribuidor de WPF almacenan el contexto de ejecución usado para iniciar la operación y restaurar el contexto anterior cuando la operación se complete. Dado que <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> y <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> ahora forman parte de este contexto, los cambios efectuados en ellas como parte de una operación de distribuidor no persisten fuera de la operación.

#### <a name="suggestion"></a>Sugerencia

Las aplicaciones afectadas por este cambio pueden solucionarlo si se almacenan los elementos <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> o <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> deseados en un campo y se protegen todos los cuerpos de las operaciones de distribuidor (incluidos los controladores de devolución de llamadas de eventos de interfaz de usuario) en los que se establezcan los elementos <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> y <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> correctos. Además, como el cambio de ExecutionContext subyacente a este cambio de WPF solo afecta a las aplicaciones destinadas a .NET Framework 4.6 o una versión más reciente, es posible evitar esta interrupción estableciendo como destino .NET Framework 4.5.2. Las aplicaciones destinadas a .NET Framework 4.6 o una versión posterior también pueden solucionarlo si se establece el modificador de compatibilidad siguiente:

<pre><code class="lang-csharp">AppContext.SetSwitch(&quot;Switch.System.Globalization.NoAsyncCurrentCulture&quot;, true);&#13;&#10;</code></pre>

WPF ha solucionado este problema en .NET Framework 4.6.2. También se ha corregido en .NET Framework 4.6, 4.6.1 a través de [KB 3139549](https://support.microsoft.com/kb/3139549). Las aplicaciones destinadas a .NET Framework 4.6 o una versión posterior obtendrán automáticamente el comportamiento correcto en las aplicaciones de WPF: <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>) se conservará entre las operaciones del distribuidor.

| NOMBRE    | Valor       |
|:--------|:------------|
| Ámbito   | Secundaria       |
| Versión | 4.6         |
| Tipo    | Redestinación |

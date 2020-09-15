---
ms.openlocfilehash: 0ef39d67cd4335658658f5772b5bce49d827cad0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614939"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a>Evento SelectionChanged y propiedad SelectedValue de Selector

#### <a name="details"></a>Detalles

A partir de .NET Framework 4.7.1, un <xref:System.Windows.Controls.Primitives.Selector> siempre actualiza el valor de su propiedad <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> antes de generar el evento <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> cuando cambia su selección. Esto hace que la propiedad SelectedValue sea coherente con las demás propiedades de selección (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> y <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>), que se actualizan antes de que se genere el evento.<p/>En .NET Framework 4.7 y versiones anteriores, la actualización de SelectedValue se realizaba antes que el evento en la mayoría de los casos, pero se producía después del evento si el cambio de selección se debía al cambio de la propiedad <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>.

#### <a name="suggestion"></a>Sugerencia

Las aplicaciones que tienen como destino .NET Framework 4.7.1 o una versión posterior pueden rechazar este cambio y usar el comportamiento heredado si se agrega lo siguiente a la sección `<runtime>` del archivo de configuración de la aplicación:

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

Las aplicaciones que tienen como destino .NET Framework 4.7 o versiones anteriores, pero que se ejecutan en .NET Framework 4.7.1 o versiones posteriores, pueden habilitar el comportamiento nuevo si se agrega la línea siguiente a la sección `<runtime>` del archivo .configuration de la aplicación:

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| NOMBRE    | Valor       |
|:--------|:------------|
| Ámbito   | Secundaria       |
| Versión | 4.7.1       |
| Tipo    | Redestinación |

#### <a name="affected-apis"></a>API afectadas

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>

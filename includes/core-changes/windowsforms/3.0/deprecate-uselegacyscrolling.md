---
ms.openlocfilehash: dd850e83540ffed4dc95b00f807f49b0dd3725e9
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721392"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>No se admite el modificador de compatibilidad DomainUpDown.UseLegacyScrolling

El modificador de compatibilidad `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`, que se introdujo en .NET Framework 4.7.1, no se admite en Windows Forms en .NET Core 3.0.

#### <a name="change-description"></a>Descripción del cambio

A partir de .NET Framework 4.7.1, el modificador de compatibilidad `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` permite a los desarrolladores rechazar las acciones independientes de <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> y <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>. El modificador restaura el comportamiento heredado, en el que se rechaza la acción <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> si hay texto de contexto, y el desarrollador debe usar la acción <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> en el control antes de la acción <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>. Para obtener más información, consulte [Elemento \<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

En .NET Core, no se admite el modificador `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`.

#### <a name="version-introduced"></a>Versión introducida

3.0 (versión preliminar 9)

#### <a name="recommended-action"></a>Acción recomendada

Quite el modificador. No se admite el modificador y no hay ninguna funcionalidad alternativa disponible.

#### <a name="category"></a>Categoría

Windows Forms

#### <a name="affected-apis"></a>API afectadas

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->

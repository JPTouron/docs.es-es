---
ms.openlocfilehash: 4fb1ffed97a5b7f906bed13a69f1e71563d11dae
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556218"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>Se ha quitado el atributo SerializableAttribute de algunos tipos de Windows Forms

El atributo <xref:System.SerializableAttribute> se ha quitado de algunas clases de Windows Forms que no tienen ningún escenario de serialización binaria conocido.

#### <a name="change-description"></a>Descripción del cambio

Los tipos siguientes se representan con el atributo <xref:System.SerializableAttribute> en .NET Framework, pero este atributo se ha quitado en .NET Core:

- `System.InvariantComparer`
- <xref:System.ComponentModel.Design.ExceptionCollection?displayProperty=nameWithType>
- <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerException?displayProperty=nameWithType>
- `System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService.CodeDomSerializationStore`
- <xref:System.Drawing.Design.ToolboxItem?displayProperty=nameWithType>
- `System.Resources.ResXNullRef`
- `System.Resources.ResXDataNode`
- `System.Resources.ResXFileRef`
- <xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>
- `System.Windows.Forms.NativeMethods.MSOCRINFOSTRUCT`
- `System.Windows.Forms.NativeMethods.MSG`

Históricamente, este mecanismo de serialización ha presentado problemas graves de mantenimiento y de seguridad. Mantener el atributo `SerializableAttribute` en tipos significa que se deben comprobar esos tipos por si hay cambios de serialización de una versión a otra y, posiblemente, también de un marco a otro. Esto dificulta el desarrollo de esos tipos y puede requerir un mantenimiento costoso. Estos tipos no tienen ningún escenario conocido de serialización binaria, lo cual reduce el impacto de la eliminación del atributo.

Para obtener más información, vea [Serialización binaria](~/docs/standard/serialization/binary-serialization.md).

#### <a name="version-introduced"></a>Versión introducida

3.0

#### <a name="recommended-action"></a>Acción recomendada

Actualice cualquier código que pueda depender de estos tipos que están marcados como serializables.

#### <a name="category"></a>Categoría

Windows Forms

#### <a name="affected-apis"></a>API afectadas

- Ninguna

<!--

#### Affected APIs

- Not detectable via API analysis

-->

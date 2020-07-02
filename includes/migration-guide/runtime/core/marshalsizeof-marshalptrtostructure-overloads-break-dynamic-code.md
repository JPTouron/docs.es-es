---
ms.openlocfilehash: c462c7b4ec8423ce8fd331d3cd31154283cf1f1d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620587"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>Las sobrecargas de Marshal.SizeOf y Marshal.PtrToStructure interrumpen el código dinámico

#### <a name="details"></a>Detalles

A partir de .NET Framework 4.5.1, el enlace dinámico a los métodos <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> o <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> (por ejemplo, a través de Windows PowerShell, IronPython o la palabra clave dynamic de C#) puede dar lugar a excepciones <code>MethodInvocationExceptions</code>, ya que se han agregado nuevas sobrecargas de estos métodos que pueden resultar ambiguas para los motores de scripting.

#### <a name="suggestion"></a>Sugerencia

Actualice los scripts para que indiquen claramente qué sobrecarga se debe usar. Normalmente, puede hacerse convirtiendo de forma explícita los parámetros de tipo del método como <xref:System.Type>. Visite [este vínculo](https://support.microsoft.com/kb/2909958/) para consultar información más detallada y ejemplos de soluciones alternativas para este problema.

| NOMBRE    | Valor       |
|:--------|:------------|
| Ámbito   |Secundaria|
|Versión|4.5.1|
|Tipo|Tiempo de ejecución|

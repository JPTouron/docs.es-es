---
title: Etiquetas XML recomendadas para comentarios de documentación
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 9f877ee3fc9d616dc1e946293489a8aab96ac2e1
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872800"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Etiquetas XML recomendadas para comentarios de documentación (Visual Basic)

El compilador de Visual Basic puede procesar comentarios de documentación en el código en un archivo XML. Puede usar herramientas adicionales para procesar el archivo XML en la documentación de.  
  
 Los comentarios XML se permiten en construcciones de código como tipos y miembros de tipo. En el caso de los tipos parciales, solo una parte del tipo puede tener comentarios XML, aunque no hay ninguna restricción en el comentario de sus miembros.  
  
> [!NOTE]
> Los comentarios de documentación no se pueden aplicar a espacios de nombres. La razón es que un espacio de nombres puede abarcar varios ensamblados, y no todos los ensamblados deben cargarse al mismo tiempo.  
  
 El compilador procesa cualquier etiqueta que sea XML válida. Las siguientes etiquetas proporcionan funcionalidad de uso común en la documentación del usuario.  
  
||||  
|---|---|---|  
|[\<c>](c.md)|[\<code>](code.md)|[\<example>](example.md)|  
|[\<exception>](exception.md)<sup>1</sup>|[\<include>](include.md)<sup>1</sup>|[\<list>](list.md)|  
|[\<para>](para.md)|[\<param>](param.md)<sup>1</sup>|[\<paramref>](paramref.md)|  
|[\<permission>](permission.md)<sup>1</sup>|[\<remarks>](remarks.md)|[\<returns>](returns.md)|  
|[\<see>](see.md)<sup>1</sup>|[\<seealso>](seealso.md)<sup>1</sup>|[\<summary>](summary.md)|  
|[\<typeparam>](typeparam.md)<sup>1</sup>|[\<value>](value.md)||  
  
 (<sup>1</sup> el compilador comprueba la sintaxis).  
  
> [!NOTE]
> Si desea que los corchetes angulares aparezcan en el texto de un Comentario de documentación, use `&lt;` y `&gt;` . Por ejemplo, la cadena `"&lt;text in angle brackets&gt;"` aparecerá como `<text in angle brackets>` .  
  
## <a name="see-also"></a>Vea también

- [Documentar el código con XML](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
- [-doc](../../reference/command-line-compiler/doc.md)
- [Procedimiento para crear documentación XML](../../programming-guide/program-structure/how-to-create-xml-documentation.md)

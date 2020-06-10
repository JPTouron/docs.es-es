---
title: <see> - Guía de programación de C#
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 0f10feb0931c6d38c817fdecb925f68d439abb59
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287251"
---
# <a name="see-c-programming-guide"></a>\<see> (guía de programación de C#)

## <a name="syntax"></a>Sintaxis

```xml
<see cref="member"/>
```

## <a name="parameters"></a>Parámetros

- cref = "`member`"

  Referencia a un miembro o campo al cual se puede llamar desde el entorno de compilación actual. El compilador comprueba si el elemento de código dado existe y pasa `member` al nombre de elemento en el resultado XML. Agregue *member* entre comillas dobles (" ").

## <a name="remarks"></a>Comentarios

La etiqueta `<see>` permite especificar un vínculo desde el texto. Use [\<seealso>](./seealso.md) para indicar que el texto debe colocarse en una sección Vea también. Use el [atributo cref](./cref-attribute.md) para crear hipervínculos internos a las páginas de documentación de los elementos de código.

Compile con [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para procesar los comentarios de documentación de un archivo.

En el ejemplo siguiente, se muestra una etiqueta `<see>` dentro de una sección de resumen.

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a>Vea también

- [Guía de programación de C#](../index.md)
- [Etiquetas recomendadas para los comentarios de documentación](./recommended-tags-for-documentation-comments.md)

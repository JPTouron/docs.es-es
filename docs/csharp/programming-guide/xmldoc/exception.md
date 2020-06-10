---
title: <exception> - Guía de programación de C#
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: fb193c586456497ee60aad941d56241ad7c6b63a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287401"
---
# <a name="exception-c-programming-guide"></a>\<exception> (guía de programación de C#)

## <a name="syntax"></a>Sintaxis

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a>Parámetros

- cref = "`member`"

  Una referencia a una excepción que está disponible desde el entorno de compilación actual. El compilador comprueba si la excepción dada existe y traduce `member` al nombre de elemento canónico en la salida XML. `member` debe aparecer entre comillas dobles (" ").

  Para más información sobre cómo dar formato a `member` para hacer referencia a un tipo genérico, consulte [Procesar el archivo XML](processing-the-xml-file.md).

- `description`

  Descripción de la excepción.

## <a name="remarks"></a>Comentarios

La etiqueta `<exception>` le permite especificar qué excepciones se pueden producir. Esta etiqueta se puede aplicar a definiciones de métodos, propiedades, eventos e indizadores.

Compile con [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para procesar los comentarios de documentación de un archivo.

Para más información sobre el control de excepciones, vea [Excepciones y control de excepciones](../exceptions/index.md).

## <a name="example"></a>Ejemplo

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a>Vea también

- [Guía de programación de C#](../index.md)
- [Etiquetas recomendadas para los comentarios de documentación](recommended-tags-for-documentation-comments.md)

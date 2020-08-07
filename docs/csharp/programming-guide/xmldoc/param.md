---
title: <param> - Guía de programación de C#
description: Aprenda sobre la etiqueta XML <param> . Esta etiqueta se usa en el comentario de una declaración de método para describir uno de los parámetros del método.
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: a9e3b2e86528afcbe1330788e248f0143efb5c1b
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381559"
---
# <a name="param-c-programming-guide"></a>\<param> (guía de programación de C#)

## <a name="syntax"></a>Sintaxis

```xml
<param name="name">description</param>
```

## <a name="parameters"></a>Parámetros

- `name`

  Nombre de un parámetro de método. Ponga el nombre entre comillas dobles (" ").

- `description`

  Descripción del parámetro.

## <a name="remarks"></a>Comentarios

La etiqueta `<param>` debe usarse en el comentario de una declaración de método para describir uno de los parámetros del método. Para documentar varios parámetros, use varias etiquetas `<param>`.

El texto de la etiqueta `<param>` se muestra en IntelliSense, el examinador de objetos y el informe web de comentario de código.

Compile con [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para procesar los comentarios de documentación de un archivo.

## <a name="example"></a>Ejemplo

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a>Vea también

- [Guía de programación de C#](../index.md)
- [Etiquetas recomendadas para los comentarios de documentación](./recommended-tags-for-documentation-comments.md)

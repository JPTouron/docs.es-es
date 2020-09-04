---
description: 'var: Referencia de C#'
title: 'var: Referencia de C#'
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: 303a880a54a79e50515060e0ea28e8d021fa1b76
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141717"
---
# <a name="var-c-reference"></a>var (Referencia de C#)

A partir de Visual C# 3.0, las variables que se declaran en el ámbito de método pueden tener un "tipo" `var` implícito. Una variable local con tipo implícito es fuertemente tipada exactamente igual que si hubiera declarado el tipo, solo que en este caso es el compilador el que lo determina. Las dos declaraciones siguientes de `i` tienen una función equivalente:

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

Para obtener más información, vea [Variables locales con asignación implícita de tipos](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) y [Relaciones entre tipos en operaciones de consulta LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

> [!IMPORTANT]
> Cuando `var` se usa con tipos de referencia que aceptan valores NULL, siempre implica un tipo de referencia que acepta valores NULL, aunque el tipo de expresión no los acepte.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestran dos expresiones de consulta. En la primera expresión, el uso de `var` se permite pero no es necesario, ya que el tipo del resultado de la consulta se puede indicar explícitamente como `IEnumerable<string>`. En cambio, en la segunda expresión, `var` permite que el resultado sea una colección de tipos anónimos y solo el compilador puede tener acceso al nombre de ese tipo. El uso de `var` elimina la necesidad de crear una nueva clase para el resultado. Tenga en cuenta que, en el ejemplo 2, la variable de iteración `foreach``item` también debe tener tipo implícito.

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>Vea también

- [Referencia de C#](../index.md)
- [Guía de programación de C#](../../programming-guide/index.md)
- [Variables locales con asignación implícita de tipos](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)

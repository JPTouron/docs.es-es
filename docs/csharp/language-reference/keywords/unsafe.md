---
description: unsafe (palabra clave) - Referencia de C#
title: unsafe (palabra clave) - Referencia de C#
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: 2e047a4cff77877862c5cbbb5e49eb1a75b42499
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141964"
---
# <a name="unsafe-c-reference"></a>unsafe (Referencia de C#)

La palabra clave `unsafe` denota un contexto no seguro, que es necesario para realizar cualquier operación que implique punteros. Para obtener más información, vea [Código no seguro y punteros (Guía de programación de C#)](../../programming-guide/unsafe-code-pointers/index.md).

Puede usar el codificador `unsafe` en la declaración de un tipo o miembro. Por consiguiente, toda la extensión textual del tipo o miembro se considera un contexto no seguro. Por ejemplo, el siguiente método se declara con el modificador `unsafe`:

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

El ámbito del contexto no seguro se extiende desde la lista de parámetros hasta el final del método, por lo que también pueden usarse punteros en la lista de parámetros:

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

También puede usarse un bloque no seguro para habilitar el uso de código no seguro en el bloque. Por ejemplo:

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

Para compilar código no seguro, debe especificar la opción del compilador [`-unsafe`](../compiler-options/unsafe-compiler-option.md). Common Language Runtime no puede comprobar el código no seguro.

## <a name="example"></a>Ejemplo

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a>Especificación del lenguaje C#

Para más información, vea la sección sobre [código no seguro](~/_csharplang/spec/unsafe-code.md) de la [Especificación del lenguaje C#](/dotnet/csharp/language-reference/language-specification/introduction). La especificación del lenguaje es la fuente definitiva de la sintaxis y el uso de C#.

## <a name="see-also"></a>Vea también

- [Referencia de C#](../index.md)
- [Guía de programación de C#](../../programming-guide/index.md)
- [Palabras clave de C#](index.md)
- [fixed (instrucción)](fixed-statement.md)
- [Código no seguro y punteros](../../programming-guide/unsafe-code-pointers/index.md)
- [Búferes de tamaño fijo](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)

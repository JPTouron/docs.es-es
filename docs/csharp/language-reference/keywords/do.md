---
title: do - Referencia de C#
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: d75dd816278a876fa05d133e5eb189d606300a5c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401932"
---
# <a name="do-c-reference"></a>do (Referencia de C#)

La instrucción `do` ejecuta una instrucción o un bloque de instrucciones mientras que una expresión booleana especificada se evalúa como `true`. Como esa expresión se evalúa después de cada ejecución del bucle, un bucle `do-while` se ejecuta una o varias veces. Esto es diferente del bucle [while](while.md), que se ejecuta cero o varias veces.

En cualquier punto del bloque de instrucciones `do`, se puede salir del bucle mediante la instrucción [break](break.md).

Puede ir directamente a la evaluación de la expresión `while` mediante la instrucción [continue](continue.md). Si la expresión se evalúa como `true`, la ejecución continúa en la primera instrucción del bucle. En caso contrario, la ejecución continúa en la primera instrucción después del bucle.

También se puede salir de un bucle `do-while` mediante las instrucciones [goto](goto.md), [return](return.md) o [throw](throw.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el uso de la instrucción `do`. Haga clic en **Ejecutar** para ejecutar el código de ejemplo. Después, puede modificar el código y volver a ejecutarlo.

[!code-csharp-interactive[do loop example](snippets/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a>Especificación del lenguaje C#

Para más información, vea la sección sobre la [instrucción do](~/_csharplang/spec/statements.md#the-do-statement) de la [Especificación del lenguaje C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Vea también

- [Referencia de C#](../index.md)
- [Guía de programación de C#](../../programming-guide/index.md)
- [Palabras clave de C#](index.md)
- [while (Instrucción)](while.md)

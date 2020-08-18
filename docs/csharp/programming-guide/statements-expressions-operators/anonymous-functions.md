---
title: 'Funciones anónimas: Guía de programación de C#'
description: Aprenda sobre las funciones anónimas. Puede usar una expresión lambda o un método anónimo para crear una función anónima.
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: 1fde7d535054f09d55018a010468776622ebfba7
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063268"
---
# <a name="anonymous-functions-c-programming-guide"></a>Funciones anónimas (Guía de programación de C#)

Una función anónima es una instrucción o expresión "alineada" que se puede usar siempre que se espera un tipo delegado. Se puede usar para inicializar un delegado con nombre o se puede pasar como un parámetro de método en lugar de un tipo delegado con nombre.

Puede usar una [expresión lambda](../../language-reference/operators/lambda-expressions.md) o un [método anónimo](../../language-reference/operators/delegate-operator.md) para crear una función anónima. Se recomienda usar expresiones lambda porque proporcionan una manera más concisa y expresiva para escribir código alineado. A diferencia de los métodos anónimos, algunos tipos de expresiones lambda se pueden convertir en los tipos de árbol de expresión.

## <a name="the-evolution-of-delegates-in-c"></a>La evolución de los delegados en C\#

 En C# 1.0, una instancia de un delegado se creaba al inicializarla de forma explícita con un método que se definía en otro lugar en el código. C# 2.0 introdujo el concepto de métodos anónimos como una manera de escribir bloques de instrucciones insertados sin nombre que se podían ejecutar en la invocación de un delegado. C# 3.0 introdujo las expresiones lambda, que son similares en concepto a los métodos anónimos, pero más expresivas y concisas. Estas dos características se conocen colectivamente como *funciones anónimas*. Por lo general, las aplicaciones que tienen como destino .NET Framework 3.5 y versiones posteriores deberían usar expresiones lambda.  
  
 En el ejemplo siguiente se muestra la evolución de la creación de delegados desde C# 1.0 a C# 3.0:  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a>Especificación del lenguaje C#

Para obtener más información, vea la sección [Expresiones de función anónima](~/_csharplang/spec/expressions.md#anonymous-function-expressions) de la [Especificación del lenguaje C#](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Vea también

- [Instrucciones, expresiones y operadores](./index.md)
- [Expresiones lambda](../../language-reference/operators/lambda-expressions.md)
- [Delegados](../delegates/index.md)
- [Árboles de expresión (C#)](../concepts/expression-trees/index.md)

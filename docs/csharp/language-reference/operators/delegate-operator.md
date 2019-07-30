---
title: 'Operador delegate: referencia de C#'
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 1fe281776bd75d8fa869065cd24e85f04fec849d
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331834"
---
# <a name="delegate-operator-c-reference"></a><span data-ttu-id="27a40-102">Operador delegate (referencia de C#)</span><span class="sxs-lookup"><span data-stu-id="27a40-102">delegate operator (C# reference)</span></span>

<span data-ttu-id="27a40-103">El operador `delegate` crea un método anónimo que se puede convertir en un tipo delegado:</span><span class="sxs-lookup"><span data-stu-id="27a40-103">The `delegate` operator creates an anonymous method that can be converted to a delegate type:</span></span>

[!code-csharp-interactive[anonymous method](~/samples/csharp/language-reference/operators/DelegateOperator.cs#AnonymousMethod)]

<span data-ttu-id="27a40-104">A partir de C# 3, las [expresiones lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) brindan una manera más concisa y expresiva para crear una función anónima.</span><span class="sxs-lookup"><span data-stu-id="27a40-104">Beginning with C# 3, [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) provide a more concise and expressive way to create an anonymous function.</span></span> <span data-ttu-id="27a40-105">Use el [operador =>](lambda-operator.md) para construir una expresión lambda:</span><span class="sxs-lookup"><span data-stu-id="27a40-105">Use the [=> operator](lambda-operator.md) to construct a lambda expression:</span></span>

[!code-csharp-interactive[lambda expression](~/samples/csharp/language-reference/operators/DelegateOperator.cs#Lambda)]

<span data-ttu-id="27a40-106">Al usar el operador `delegate`, puede omitir la lista de parámetros.</span><span class="sxs-lookup"><span data-stu-id="27a40-106">When you use the `delegate` operator, you might omit the parameter list.</span></span> <span data-ttu-id="27a40-107">Si lo hace, el método anónimo creado se puede convertir en un tipo delegado con cualquier lista de parámetros, tal como se muestra en el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="27a40-107">If you do that, the created anonymous method can be converted to a delegate type with any list of  parameters, as the following example shows:</span></span>

[!code-csharp-interactive[no parameter list](~/samples/csharp/language-reference/operators/DelegateOperator.cs#WithoutParameterList)]

<span data-ttu-id="27a40-108">Esta es la única funcionalidad de los métodos anónimos que las expresiones lambda no admiten.</span><span class="sxs-lookup"><span data-stu-id="27a40-108">That's the only functionality of anonymous methods that is not supported by lambda expressions.</span></span> <span data-ttu-id="27a40-109">En todos los demás casos, una expresión lambda es una de las maneras preferidas de escribir código alineado.</span><span class="sxs-lookup"><span data-stu-id="27a40-109">In all other cases, a lambda expression is a preferred way to write inline code.</span></span> <span data-ttu-id="27a40-110">Para más información sobre las características de las expresiones lambda, como capturar las variables externas, consulte [Expresiones lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="27a40-110">For more information about features of lambda expressions, for example, capturing outer variables, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="27a40-111">También puede usar la palabra clave `delegate` para declarar un [tipo delegado](../builtin-types/reference-types.md#the-delegate-type).</span><span class="sxs-lookup"><span data-stu-id="27a40-111">You also use the `delegate` keyword to declare a [delegate type](../builtin-types/reference-types.md#the-delegate-type).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="27a40-112">Especificación del lenguaje C#</span><span class="sxs-lookup"><span data-stu-id="27a40-112">C# language specification</span></span>

<span data-ttu-id="27a40-113">Para obtener más información, vea la sección [Expresiones de función anónima](~/_csharplang/spec/expressions.md#anonymous-function-expressions) de la [Especificación del lenguaje C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="27a40-113">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="27a40-114">Vea también</span><span class="sxs-lookup"><span data-stu-id="27a40-114">See also</span></span>

- [<span data-ttu-id="27a40-115">Referencia de C#</span><span class="sxs-lookup"><span data-stu-id="27a40-115">C# reference</span></span>](../index.md)
- [<span data-ttu-id="27a40-116">Operadores de C#</span><span class="sxs-lookup"><span data-stu-id="27a40-116">C# operators</span></span>](index.md)
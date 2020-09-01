---
description: 'try-finally: Referencia de C#'
title: 'try-finally: Referencia de C#'
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 621c5bf1607136361b72f978681607ec2aec150f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141977"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="068e6-103">try-finally (Referencia de C#)</span><span class="sxs-lookup"><span data-stu-id="068e6-103">try-finally (C# Reference)</span></span>

<span data-ttu-id="068e6-104">Mediante el uso de un bloque `finally`, puede limpiar todos los recursos asignados en un bloque [try](try-catch.md) y ejecutar código incluso si se produce una excepción en el bloque `try`.</span><span class="sxs-lookup"><span data-stu-id="068e6-104">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="068e6-105">Normalmente, las instrucciones de un bloque `finally` se ejecutan cuando el control abandona una instrucción `try`.</span><span class="sxs-lookup"><span data-stu-id="068e6-105">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="068e6-106">La transferencia de control se puede producir como resultado de la ejecución normal, de la ejecución de una instrucción `break`, `continue`, `goto` o `return`, o de la propagación de una excepción fuera de la instrucción `try`.</span><span class="sxs-lookup"><span data-stu-id="068e6-106">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="068e6-107">Dentro de una excepción controlada, se garantiza la ejecución del bloque `finally` asociado.</span><span class="sxs-lookup"><span data-stu-id="068e6-107">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="068e6-108">Pero en el caso de una excepción no controlada, la ejecución del bloque `finally` depende de la manera en que se desencadene la operación de desenredo de la excepción.</span><span class="sxs-lookup"><span data-stu-id="068e6-108">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="068e6-109">Esto, a su vez, depende de cómo esté configurado el equipo.</span><span class="sxs-lookup"><span data-stu-id="068e6-109">That, in turn, is dependent on how your computer is set up.</span></span>

<span data-ttu-id="068e6-110">Normalmente, cuando una excepción no controlada finaliza una aplicación, no es importante si el bloque `finally` se ejecuta o no.</span><span class="sxs-lookup"><span data-stu-id="068e6-110">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="068e6-111">Pero si tiene instrucciones en un bloque `finally` que debe ejecutarse incluso en esa situación, una solución es agregar un bloque `catch` a la instrucción `try`-`finally`.</span><span class="sxs-lookup"><span data-stu-id="068e6-111">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="068e6-112">Como alternativa, puede capturar la excepción que se podría producir en el bloque `try` de una instrucción `try`-`finally` más arriba en la pila de llamadas.</span><span class="sxs-lookup"><span data-stu-id="068e6-112">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="068e6-113">Es decir, puede capturar la excepción en el método que llama al método que contiene la instrucción `try`-`finally`, en el método que llama a ese método o en cualquier método en la pila de llamadas.</span><span class="sxs-lookup"><span data-stu-id="068e6-113">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="068e6-114">Si no se captura la excepción, la ejecución del bloque `finally` depende de si el sistema operativo decide desencadenar una operación de desenredo de la excepción.</span><span class="sxs-lookup"><span data-stu-id="068e6-114">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="068e6-115">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="068e6-115">Example</span></span>

<span data-ttu-id="068e6-116">En el ejemplo siguiente, una instrucción de conversión no válida provoca una excepción `System.InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="068e6-116">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="068e6-117">Se trata de una excepción no controlada.</span><span class="sxs-lookup"><span data-stu-id="068e6-117">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="068e6-118">En el ejemplo siguiente, se captura una excepción del método `TryCast` en un método más arriba en la pila de llamadas.</span><span class="sxs-lookup"><span data-stu-id="068e6-118">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="068e6-119">Para obtener más información sobre `finally`, vea [try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="068e6-119">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="068e6-120">C# también contiene la [instrucción using](using-statement.md), que proporciona una función similar para objetos <xref:System.IDisposable> en una sintaxis adecuada.</span><span class="sxs-lookup"><span data-stu-id="068e6-120">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="068e6-121">Especificación del lenguaje C#</span><span class="sxs-lookup"><span data-stu-id="068e6-121">C# language specification</span></span>

<span data-ttu-id="068e6-122">Para obtener más información, vea la sección sobre la [instrucción try](~/_csharplang/spec/statements.md#the-try-statement) de la [Especificación del lenguaje C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="068e6-122">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="068e6-123">Vea también</span><span class="sxs-lookup"><span data-stu-id="068e6-123">See also</span></span>

- [<span data-ttu-id="068e6-124">Referencia de C#</span><span class="sxs-lookup"><span data-stu-id="068e6-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="068e6-125">Guía de programación de C#</span><span class="sxs-lookup"><span data-stu-id="068e6-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="068e6-126">Palabras clave de C#</span><span class="sxs-lookup"><span data-stu-id="068e6-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="068e6-127">Instrucciones try, throw y catch (C++)</span><span class="sxs-lookup"><span data-stu-id="068e6-127">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="068e6-128">throw</span><span class="sxs-lookup"><span data-stu-id="068e6-128">throw</span></span>](throw.md)
- [<span data-ttu-id="068e6-129">try-catch</span><span class="sxs-lookup"><span data-stu-id="068e6-129">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="068e6-130">Cómo: Iniciar excepciones explícitamente</span><span class="sxs-lookup"><span data-stu-id="068e6-130">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)

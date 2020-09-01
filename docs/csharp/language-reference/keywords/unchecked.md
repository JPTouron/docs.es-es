---
description: unchecked (palabra clave) - Referencia de C#
title: unchecked (palabra clave) - Referencia de C#
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: bb66639e3657b247b9ebcad1594daf1f57a5c76b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141990"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="a3a94-103">unchecked (Referencia de C#)</span><span class="sxs-lookup"><span data-stu-id="a3a94-103">unchecked (C# Reference)</span></span>

<span data-ttu-id="a3a94-104">La palabra clave `unchecked` se usa para suprimir la comprobación de desbordamiento en las operaciones y conversiones aritméticas de tipos enteros.</span><span class="sxs-lookup"><span data-stu-id="a3a94-104">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="a3a94-105">En un contexto unchecked, si una expresión genera un valor que está fuera del intervalo del tipo de destino, no se marca el desbordamiento.</span><span class="sxs-lookup"><span data-stu-id="a3a94-105">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="a3a94-106">Por ejemplo, dado que el cálculo del siguiente ejemplo se realiza en un bloque o una expresión `unchecked`, el hecho de que el resultado sea demasiado grande para un entero se omite y se asigna a `int1` el valor -2 147 483 639.</span><span class="sxs-lookup"><span data-stu-id="a3a94-106">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

<span data-ttu-id="a3a94-107">Si se quita el entorno `unchecked`, se produce un error de compilación.</span><span class="sxs-lookup"><span data-stu-id="a3a94-107">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="a3a94-108">El desbordamiento se puede detectar en tiempo de compilación porque todos los términos de la expresión son constantes.</span><span class="sxs-lookup"><span data-stu-id="a3a94-108">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>

<span data-ttu-id="a3a94-109">Las expresiones que contienen términos no constantes son unchecked de forma predeterminada en tiempo de compilación y tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="a3a94-109">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="a3a94-110">Vea [checked](checked.md) para obtener información sobre cómo habilitar un entorno checked.</span><span class="sxs-lookup"><span data-stu-id="a3a94-110">See [checked](checked.md) for information about enabling a checked environment.</span></span>

<span data-ttu-id="a3a94-111">Puesto que la comprobación de desbordamiento lleva tiempo, el uso del código unchecked en situaciones donde no hay riesgo de desbordamiento puede mejorar el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="a3a94-111">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="a3a94-112">Pero si el desbordamiento es una posibilidad, se debe usar un entorno checked.</span><span class="sxs-lookup"><span data-stu-id="a3a94-112">However, if overflow is a possibility, a checked environment should be used.</span></span>

## <a name="example"></a><span data-ttu-id="a3a94-113">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a3a94-113">Example</span></span>

<span data-ttu-id="a3a94-114">En este ejemplo se muestra cómo usar la palabra clave `unchecked`.</span><span class="sxs-lookup"><span data-stu-id="a3a94-114">This sample shows how to use the `unchecked` keyword.</span></span>

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="a3a94-115">Especificación del lenguaje C#</span><span class="sxs-lookup"><span data-stu-id="a3a94-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a3a94-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="a3a94-116">See also</span></span>

- [<span data-ttu-id="a3a94-117">Referencia de C#</span><span class="sxs-lookup"><span data-stu-id="a3a94-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a3a94-118">Guía de programación de C#</span><span class="sxs-lookup"><span data-stu-id="a3a94-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a3a94-119">Palabras clave de C#</span><span class="sxs-lookup"><span data-stu-id="a3a94-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a3a94-120">Checked y unchecked</span><span class="sxs-lookup"><span data-stu-id="a3a94-120">Checked and Unchecked</span></span>](checked-and-unchecked.md)
- [<span data-ttu-id="a3a94-121">checked</span><span class="sxs-lookup"><span data-stu-id="a3a94-121">checked</span></span>](checked.md)

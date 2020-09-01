---
description: 'Palabra clave out (modificador genérico): Referencia de C#'
title: 'Palabra clave out (modificador genérico): Referencia de C#'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 84f3647309c0772f6ae61d3614f8649fe277f153
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142341"
---
# <a name="out-generic-modifier-c-reference"></a><span data-ttu-id="83e6d-103">out (Modificador genérico) (Referencia de C#)</span><span class="sxs-lookup"><span data-stu-id="83e6d-103">out (generic modifier) (C# Reference)</span></span>

<span data-ttu-id="83e6d-104">Para los parámetros de tipo genérico, la palabra clave `out` especifica que el parámetro de tipo es covariante.</span><span class="sxs-lookup"><span data-stu-id="83e6d-104">For generic type parameters, the `out` keyword specifies that the type parameter is covariant.</span></span> <span data-ttu-id="83e6d-105">Puede usar la palabra clave `out` en las interfaces y delegados genéricos.</span><span class="sxs-lookup"><span data-stu-id="83e6d-105">You can use the `out` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="83e6d-106">La covarianza le permite usar un tipo más derivado que el que se especifica en el parámetro genérico.</span><span class="sxs-lookup"><span data-stu-id="83e6d-106">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="83e6d-107">Esto permite la conversión implícita de las clases que implementan interfaces covariantes y la conversión implícita de los tipos de delegado.</span><span class="sxs-lookup"><span data-stu-id="83e6d-107">This allows for implicit conversion of classes that implement covariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="83e6d-108">La covarianza y la contravarianza son compatibles con los tipos de referencia, pero no lo son con los tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="83e6d-108">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="83e6d-109">Una interfaz con un parámetro de tipo covariante permite que sus métodos devuelvan tipos más derivados que los especificados por el parámetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="83e6d-109">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="83e6d-110">Por ejemplo, dado que en .NET Framework 4, en <xref:System.Collections.Generic.IEnumerable%601>, el tipo T es covariante, puede asignar un objeto del tipo `IEnumerable(Of String)` a otro objeto del tipo `IEnumerable(Of Object)` sin usar ningún método de conversión especial.</span><span class="sxs-lookup"><span data-stu-id="83e6d-110">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>

<span data-ttu-id="83e6d-111">A un delegado covariante se le puede asignar otro delegado del mismo tipo, pero con un parámetro de tipo genérico más derivado.</span><span class="sxs-lookup"><span data-stu-id="83e6d-111">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>

<span data-ttu-id="83e6d-112">Para obtener más información, vea [Covarianza y contravarianza](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="83e6d-112">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="example---covariant-generic-interface"></a><span data-ttu-id="83e6d-113">Ejemplo: interfaz genérica covariante</span><span class="sxs-lookup"><span data-stu-id="83e6d-113">Example - covariant generic interface</span></span>

<span data-ttu-id="83e6d-114">En el ejemplo siguiente se muestra cómo declarar, extender e implementar una interfaz genérica covariante.</span><span class="sxs-lookup"><span data-stu-id="83e6d-114">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="83e6d-115">También se muestra cómo usar la conversión implícita para las clases que implementan una interfaz covariante.</span><span class="sxs-lookup"><span data-stu-id="83e6d-115">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>

[!code-csharp[csVarianceKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#3)]

<span data-ttu-id="83e6d-116">En una interfaz genérica, un parámetro de tipo se puede declarar como covariante si cumple las siguientes condiciones:</span><span class="sxs-lookup"><span data-stu-id="83e6d-116">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>

- <span data-ttu-id="83e6d-117">El parámetro de tipo se usa solamente como tipo de valor devuelto de los métodos de interfaz y no como tipo de los argumentos de método.</span><span class="sxs-lookup"><span data-stu-id="83e6d-117">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>

    > [!NOTE]
    > <span data-ttu-id="83e6d-118">Hay una excepción para esta regla.</span><span class="sxs-lookup"><span data-stu-id="83e6d-118">There is one exception to this rule.</span></span> <span data-ttu-id="83e6d-119">Si en una interfaz covariante tiene un delegado genérico contravariante como parámetro de método, puede usar el tipo covariante como parámetro de tipo genérico para este delegado.</span><span class="sxs-lookup"><span data-stu-id="83e6d-119">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="83e6d-120">Para obtener más información sobre los delegados genéricos covariantes y contravariantes, vea [Varianza en delegados](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) y [Usar la varianza para los delegados genéricos Func y Action](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="83e6d-120">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

- <span data-ttu-id="83e6d-121">El parámetro de tipo no se usa como restricción genérica para los métodos de interfaz.</span><span class="sxs-lookup"><span data-stu-id="83e6d-121">The type parameter is not used as a generic constraint for the interface methods.</span></span>

## <a name="example---covariant-generic-delegate"></a><span data-ttu-id="83e6d-122">Ejemplo: delegado genérico covariante</span><span class="sxs-lookup"><span data-stu-id="83e6d-122">Example - covariant generic delegate</span></span>

<span data-ttu-id="83e6d-123">En el ejemplo siguiente se muestra cómo declarar, invocar y crear instancias de un delegado genérico covariante.</span><span class="sxs-lookup"><span data-stu-id="83e6d-123">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="83e6d-124">También se muestra cómo convertir implícitamente los tipos de delegado.</span><span class="sxs-lookup"><span data-stu-id="83e6d-124">It also shows how to implicitly convert delegate types.</span></span>

[!code-csharp[csVarianceKeywords#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#4)]

<span data-ttu-id="83e6d-125">En un delegado genérico, un tipo se puede declarar como covariante si se usa solamente como tipo de valor devuelto por un método y no se usa para los argumentos de método.</span><span class="sxs-lookup"><span data-stu-id="83e6d-125">In a generic delegate, a type can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="83e6d-126">Especificación del lenguaje C#</span><span class="sxs-lookup"><span data-stu-id="83e6d-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="83e6d-127">Vea también</span><span class="sxs-lookup"><span data-stu-id="83e6d-127">See also</span></span>

- [<span data-ttu-id="83e6d-128">Varianza en interfaces genéricas</span><span class="sxs-lookup"><span data-stu-id="83e6d-128">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="83e6d-129">in</span><span class="sxs-lookup"><span data-stu-id="83e6d-129">in</span></span>](in-generic-modifier.md)
- [<span data-ttu-id="83e6d-130">Modificadores</span><span class="sxs-lookup"><span data-stu-id="83e6d-130">Modifiers</span></span>](index.md)

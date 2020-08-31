---
description: 'Operadores de asignación: referencia de C#'
title: 'Operadores de asignación: referencia de C#'
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 3df118143b692cc8655de31cce23af41f7da125c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2020
ms.locfileid: "89117888"
---
# <a name="assignment-operators-c-reference"></a><span data-ttu-id="d3179-103">Operadores de asignación (referencia de C#)</span><span class="sxs-lookup"><span data-stu-id="d3179-103">Assignment operators (C# reference)</span></span>

<span data-ttu-id="d3179-104">El operador de asignación `=` asigna el valor de su operando de la derecha a una variable, una [propiedad](../../programming-guide/classes-and-structs/properties.md) o un elemento de [indizador](../../programming-guide/indexers/index.md) proporcionado por el operando de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="d3179-104">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="d3179-105">El resultado de una expresión de asignación es el valor asignado al operando izquierdo.</span><span class="sxs-lookup"><span data-stu-id="d3179-105">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="d3179-106">El tipo del operando de la derecha debe ser el mismo que el del operando de la izquierda o debe poder convertirse implícitamente en él.</span><span class="sxs-lookup"><span data-stu-id="d3179-106">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="d3179-107">El operador de asignación `=` es asociativo a la derecha, es decir, una expresión con el formato</span><span class="sxs-lookup"><span data-stu-id="d3179-107">The assignment operator `=` is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="d3179-108">se evalúa como</span><span class="sxs-lookup"><span data-stu-id="d3179-108">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="d3179-109">En el ejemplo siguiente se muestra el uso del operador de asignación con una variable local, una propiedad y un elemento indexador como su operando izquierdo:</span><span class="sxs-lookup"><span data-stu-id="d3179-109">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](snippets/shared/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="d3179-110">Operador de asignación ref</span><span class="sxs-lookup"><span data-stu-id="d3179-110">ref assignment operator</span></span>

<span data-ttu-id="d3179-111">A partir C# 7.3, puede usar el operador de asignación ref `= ref` para reasignar una variable [local de tipo ref](../keywords/ref.md#ref-locals) o [local de tipo ref readonly](../keywords/ref.md#ref-readonly-locals).</span><span class="sxs-lookup"><span data-stu-id="d3179-111">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="d3179-112">En el siguiente ejemplo se muestra el uso del operador de asignación ref:</span><span class="sxs-lookup"><span data-stu-id="d3179-112">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](snippets/shared/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="d3179-113">En el caso del operador de asignación de referencias, sus dos operandos deben ser del mismo tipo.</span><span class="sxs-lookup"><span data-stu-id="d3179-113">In the case of the ref assignment operator, the both of its operands must be of the same type.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="d3179-114">Asignación compuesta</span><span class="sxs-lookup"><span data-stu-id="d3179-114">Compound assignment</span></span>

<span data-ttu-id="d3179-115">Para un operador binario `op`, una expresión de asignación compuesta con el formato</span><span class="sxs-lookup"><span data-stu-id="d3179-115">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="d3179-116">es equivalente a</span><span class="sxs-lookup"><span data-stu-id="d3179-116">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="d3179-117">salvo que `x` solo se evalúa una vez.</span><span class="sxs-lookup"><span data-stu-id="d3179-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="d3179-118">La asignación compuesta es compatible con operadores [aritméticos](arithmetic-operators.md#compound-assignment), [lógicos booleanos](boolean-logical-operators.md#compound-assignment) y de [desplazamiento y lógicos bit a bit](bitwise-and-shift-operators.md#compound-assignment).</span><span class="sxs-lookup"><span data-stu-id="d3179-118">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="d3179-119">Asignación de uso combinado de NULL</span><span class="sxs-lookup"><span data-stu-id="d3179-119">Null-coalescing assignment</span></span>

<span data-ttu-id="d3179-120">A partir de C# 8.0, puede usar el operador de asignación de uso combinado de NULL `??=` para asignar el valor de su operando derecho al operando izquierdo solo si el operando izquierdo se evalúa como `null`.</span><span class="sxs-lookup"><span data-stu-id="d3179-120">Beginning with C# 8.0, you can use the null-coalescing assignment operator `??=` to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="d3179-121">Para obtener más información, consulte [Operadores ?? y ??](null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="d3179-121">For more information, see the [?? and ??= operators](null-coalescing-operator.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="d3179-122">Posibilidad de sobrecarga del operador</span><span class="sxs-lookup"><span data-stu-id="d3179-122">Operator overloadability</span></span>

<span data-ttu-id="d3179-123">Un tipo definido por el usuario no puede [sobrecargar](operator-overloading.md) el operador de asignación.</span><span class="sxs-lookup"><span data-stu-id="d3179-123">A user-defined type cannot [overload](operator-overloading.md) the assignment operator.</span></span> <span data-ttu-id="d3179-124">Sin embargo, un tipo definido por el usuario puede definir una conversión implícita a otro tipo.</span><span class="sxs-lookup"><span data-stu-id="d3179-124">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="d3179-125">De este modo, el valor de un tipo definido por el usuario puede asignarse a una variable, una propiedad o un elemento de indizador de otro tipo.</span><span class="sxs-lookup"><span data-stu-id="d3179-125">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="d3179-126">Para obtener más información, vea [Operadores de conversión definidos por el usuario](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="d3179-126">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

<span data-ttu-id="d3179-127">Un tipo definido por el usuario no puede sobrecargar de forma explícita un operador de asignación compuesta.</span><span class="sxs-lookup"><span data-stu-id="d3179-127">A user-defined type cannot explicitly overload a compound assignment operator.</span></span> <span data-ttu-id="d3179-128">Pero si un tipo definido por el usuario sobrecarga un operador binario `op`, el operador `op=`, si existe, también se sobrecarga de forma implícita.</span><span class="sxs-lookup"><span data-stu-id="d3179-128">However, if a user-defined type overloads a binary operator `op`, the `op=` operator, if it exists, is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d3179-129">especificación del lenguaje C#</span><span class="sxs-lookup"><span data-stu-id="d3179-129">C# language specification</span></span>

<span data-ttu-id="d3179-130">Para más información, consulte la sección sobre [operadores de asignación](~/_csharplang/spec/expressions.md#assignment-operators) de la [Especificación del lenguaje C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d3179-130">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="d3179-131">Para más información sobre el operador de asignación de referencias `= ref`, vea la [nota de propuesta de características](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="d3179-131">For more information about the ref assignment operator `= ref`, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d3179-132">Vea también</span><span class="sxs-lookup"><span data-stu-id="d3179-132">See also</span></span>

- [<span data-ttu-id="d3179-133">Referencia de C#</span><span class="sxs-lookup"><span data-stu-id="d3179-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d3179-134">Operadores y expresiones de C#</span><span class="sxs-lookup"><span data-stu-id="d3179-134">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="d3179-135">ref (palabra clave)</span><span class="sxs-lookup"><span data-stu-id="d3179-135">ref keyword</span></span>](../keywords/ref.md)

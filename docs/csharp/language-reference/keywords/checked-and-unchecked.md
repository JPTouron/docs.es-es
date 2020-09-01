---
description: 'Checked y Unchecked: Referencia de C#'
title: 'Checked y Unchecked: Referencia de C#'
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: a8d6a26e28062da682689bf64a9e38ea5fd158b2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138272"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="83abf-103">Checked y Unchecked (Referencia de C#)</span><span class="sxs-lookup"><span data-stu-id="83abf-103">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="83abf-104">Las instrucciones de C# se pueden ejecutar en un contexto comprobado o no comprobado.</span><span class="sxs-lookup"><span data-stu-id="83abf-104">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="83abf-105">En un contexto no comprobado, el desbordamiento aritmético produce una excepción.</span><span class="sxs-lookup"><span data-stu-id="83abf-105">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="83abf-106">En un contexto sin comprobar, se omite el desbordamiento aritmético y se produce un truncamiento del resultado al descartar los bits de orden superior que no caben en el tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="83abf-106">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
- <span data-ttu-id="83abf-107">[checked](checked.md) Especifica un contexto comprobado.</span><span class="sxs-lookup"><span data-stu-id="83abf-107">[checked](checked.md) Specify checked context.</span></span>  
  
- <span data-ttu-id="83abf-108">[unchecked](unchecked.md) Especifica un contexto no comprobado.</span><span class="sxs-lookup"><span data-stu-id="83abf-108">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="83abf-109">Las siguientes operaciones se ven afectadas por la comprobación del desbordamiento:</span><span class="sxs-lookup"><span data-stu-id="83abf-109">The following operations are affected by the overflow checking:</span></span>  
  
- <span data-ttu-id="83abf-110">Expresiones que usan los siguientes operadores predefinidos en tipos integrales:</span><span class="sxs-lookup"><span data-stu-id="83abf-110">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="83abf-111">`++`, `--`, `-` unario, `+`, `-`, `*`, `/`</span><span class="sxs-lookup"><span data-stu-id="83abf-111">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
- <span data-ttu-id="83abf-112">Conversiones numéricas explícitas entre tipos integrales o de `float` o `double` a un tipo integral.</span><span class="sxs-lookup"><span data-stu-id="83abf-112">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="83abf-113">Si no se especifica `checked` ni `unchecked`, el contexto predeterminado para expresiones no constantes (expresiones que se evalúan en tiempo de ejecución) se define por medio del valor de la opción del compilador [/checked](../compiler-options/checked-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="83abf-113">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="83abf-114">De forma predeterminada, el valor de esa opción se desactiva y se ejecutan operaciones aritméticas en un contexto sin comprobar. </span><span class="sxs-lookup"><span data-stu-id="83abf-114">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>

 <span data-ttu-id="83abf-115">Para expresiones constantes (expresiones que se pueden evaluar completamente en tiempo de compilación), el contexto predeterminado se comprueba siempre.</span><span class="sxs-lookup"><span data-stu-id="83abf-115">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="83abf-116">A menos que se coloque de forma explícita una expresión constante en un contexto sin comprobar, los desbordamientos que se producen durante la evaluación de tiempo de compilación de la expresión dan lugar a errores en tiempo de compilación.</span><span class="sxs-lookup"><span data-stu-id="83abf-116">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="83abf-117">Vea también</span><span class="sxs-lookup"><span data-stu-id="83abf-117">See also</span></span>

- [<span data-ttu-id="83abf-118">Referencia de C#</span><span class="sxs-lookup"><span data-stu-id="83abf-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="83abf-119">Guía de programación de C#</span><span class="sxs-lookup"><span data-stu-id="83abf-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="83abf-120">Palabras clave de C#</span><span class="sxs-lookup"><span data-stu-id="83abf-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="83abf-121">Palabras clave de instrucciones</span><span class="sxs-lookup"><span data-stu-id="83abf-121">Statement Keywords</span></span>](statement-keywords.md)

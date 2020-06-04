---
title: Tipo de datos Integer
ms.date: 01/31/2018
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
ms.openlocfilehash: aa7b64162308d6af2763b29034c5a7276c973876
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415614"
---
# <a name="integer-data-type-visual-basic"></a><span data-ttu-id="57ab4-102">Tipo de datos Integer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57ab4-102">Integer data type (Visual Basic)</span></span>

<span data-ttu-id="57ab4-103">Contiene enteros de 32 bits con signo (4 bytes) comprendidos en el intervalo entre -2.147.483.648 y 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="57ab4-103">Holds signed 32-bit (4-byte) integers that range in value from -2,147,483,648 through 2,147,483,647.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57ab4-104">Observaciones</span><span class="sxs-lookup"><span data-stu-id="57ab4-104">Remarks</span></span>

 <span data-ttu-id="57ab4-105">El tipo de datos `Integer` proporciona un rendimiento óptimo en un procesador de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="57ab4-105">The `Integer` data type provides optimal performance on a 32-bit processor.</span></span> <span data-ttu-id="57ab4-106">Los demás tipos enteros son más lentos a la hora de cargarse y almacenarse en la memoria.</span><span class="sxs-lookup"><span data-stu-id="57ab4-106">The other integral types are slower to load and store from and to memory.</span></span>  
  
 <span data-ttu-id="57ab4-107">El valor predeterminado de `Integer` es 0.</span><span class="sxs-lookup"><span data-stu-id="57ab4-107">The default value of `Integer` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="57ab4-108">Asignaciones literales</span><span class="sxs-lookup"><span data-stu-id="57ab4-108">Literal assignments</span></span>

<span data-ttu-id="57ab4-109">Puede declarar e inicializar una `Integer` variable asignándole un literal decimal, un literal hexadecimal, un literal octal o (empezando por Visual Basic 2017) un literal binario.</span><span class="sxs-lookup"><span data-stu-id="57ab4-109">You can declare and initialize an `Integer` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="57ab4-110">Si el literal entero está fuera del intervalo de `Integer` (es decir, si es inferior a <xref:System.Int32.MinValue?displayProperty=nameWithType> o mayor que <xref:System.Int32.MaxValue?displayProperty=nameWithType>, se produce un error de compilación.</span><span class="sxs-lookup"><span data-stu-id="57ab4-110">If the integer literal is outside the range of `Integer` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="57ab4-111">En el ejemplo siguiente, los enteros que equivalen a 90 946 que se representan como literales binarios, hexadecimales y decimales se asignan a valores `Integer`.</span><span class="sxs-lookup"><span data-stu-id="57ab4-111">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `Integer` values.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> <span data-ttu-id="57ab4-112">Use el prefijo `&h` o `&H` para denotar un literal hexadecimal, el prefijo `&b` o `&B` para denotar un literal binario, y el prefijo `&o` o `&O` para denotar un literal octal.</span><span class="sxs-lookup"><span data-stu-id="57ab4-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="57ab4-113">Los literales decimales no tienen prefijo.</span><span class="sxs-lookup"><span data-stu-id="57ab4-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="57ab4-114">A partir de Visual Basic 2017, también puede usar el carácter de subrayado, `_` , como separador de dígitos para mejorar la legibilidad, como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="57ab4-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

<span data-ttu-id="57ab4-115">A partir de Visual Basic 15,5, también puede usar el carácter de subrayado ( `_` ) como separador inicial entre el prefijo y los dígitos hexadecimales, binarios o octales.</span><span class="sxs-lookup"><span data-stu-id="57ab4-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="57ab4-116">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="57ab4-116">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="57ab4-117">Los literales numéricos también pueden incluir el `I` [carácter de tipo](../../programming-guide/language-features/data-types/type-characters.md) para denotar el `Integer` tipo de datos, como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="57ab4-117">Numeric literals can also include the `I` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Integer` data type, as the following example shows.</span></span>

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a><span data-ttu-id="57ab4-118">sugerencias de programación</span><span class="sxs-lookup"><span data-stu-id="57ab4-118">Programming tips</span></span>

- <span data-ttu-id="57ab4-119">**Consideraciones de interoperabilidad.**</span><span class="sxs-lookup"><span data-stu-id="57ab4-119">**Interop Considerations.**</span></span> <span data-ttu-id="57ab4-120">Si interactúa con componentes que no se han escrito para el .NET Framework, como objetos de automatización o COM, recuerde que `Integer` tiene un ancho de datos diferente (16 bits) en otros entornos.</span><span class="sxs-lookup"><span data-stu-id="57ab4-120">If you are interfacing with components not written for the .NET Framework, such as Automation or COM objects, remember that `Integer` has a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="57ab4-121">Al pasar un argumento de 16 bits a esos componentes, declárelo en el código de Visual Basic como `Short` en lugar de como `Integer`.</span><span class="sxs-lookup"><span data-stu-id="57ab4-121">If you are passing a 16-bit argument to such a component, declare it as `Short` instead of `Integer` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="57ab4-122">**Ampliación.**</span><span class="sxs-lookup"><span data-stu-id="57ab4-122">**Widening.**</span></span> <span data-ttu-id="57ab4-123">El tipo de datos `Integer` se amplía a `Long`, `Decimal`, `Single` o `Double`.</span><span class="sxs-lookup"><span data-stu-id="57ab4-123">The `Integer` data type widens to `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="57ab4-124">Esto significa que puede convertir un tipo de datos `Integer` en cualquiera de estos tipos sin que se produzca un error <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="57ab4-124">This means you can convert `Integer` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="57ab4-125">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="57ab4-125">**Type Characters.**</span></span> <span data-ttu-id="57ab4-126">Al agregar el carácter de tipo literal `I` a un literal, el tipo de datos se convierte forzosamente en el tipo de datos `Integer`.</span><span class="sxs-lookup"><span data-stu-id="57ab4-126">Appending the literal type character `I` to a literal forces it to the `Integer` data type.</span></span> <span data-ttu-id="57ab4-127">Si se agrega el carácter de tipo identificador `%` a cualquier identificador, se convierte forzosamente al tipo `Integer`.</span><span class="sxs-lookup"><span data-stu-id="57ab4-127">Appending the identifier type character `%` to any identifier forces it to `Integer`.</span></span>  
  
- <span data-ttu-id="57ab4-128">**Tipo de Framework.**</span><span class="sxs-lookup"><span data-stu-id="57ab4-128">**Framework Type.**</span></span> <span data-ttu-id="57ab4-129">El tipo correspondiente en .NET Framework es la estructura <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="57ab4-129">The corresponding type in the .NET Framework is the <xref:System.Int32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="57ab4-130">Intervalo</span><span class="sxs-lookup"><span data-stu-id="57ab4-130">Range</span></span>

<span data-ttu-id="57ab4-131">Si intenta establecer una variable de un tipo entero en un número que está fuera del intervalo correspondiente a ese tipo, se produce un error.</span><span class="sxs-lookup"><span data-stu-id="57ab4-131">If you try to set a variable of an integral type to a number outside the range for that type, an error occurs.</span></span> <span data-ttu-id="57ab4-132">Si intenta establecerlo en una fracción, el número se redondea hacia arriba o hacia abajo al valor entero más cercano.</span><span class="sxs-lookup"><span data-stu-id="57ab4-132">If you try to set it to a fraction, the number is rounded up or down to the nearest integer value.</span></span> <span data-ttu-id="57ab4-133">Si el número está equidistante a dos valores enteros, el valor se redondea al entero par más próximo.</span><span class="sxs-lookup"><span data-stu-id="57ab4-133">If the number is equally close to two integer values, the value is rounded to the nearest even integer.</span></span> <span data-ttu-id="57ab4-134">Este comportamiento minimiza los errores de redondeo que se derivan de redondear de forma consistente un valor de punto medio en una dirección única.</span><span class="sxs-lookup"><span data-stu-id="57ab4-134">This behavior minimizes rounding errors that result from consistently rounding a midpoint value in a single direction.</span></span> <span data-ttu-id="57ab4-135">En el código siguiente se muestran ejemplos de redondeo.</span><span class="sxs-lookup"><span data-stu-id="57ab4-135">The following code shows examples of rounding.</span></span>  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a><span data-ttu-id="57ab4-136">Consulte también</span><span class="sxs-lookup"><span data-stu-id="57ab4-136">See also</span></span>

- <xref:System.Int32?displayProperty=nameWithType>
- [<span data-ttu-id="57ab4-137">Tipos de datos</span><span class="sxs-lookup"><span data-stu-id="57ab4-137">Data Types</span></span>](index.md)
- [<span data-ttu-id="57ab4-138">Tipo de datos Long</span><span class="sxs-lookup"><span data-stu-id="57ab4-138">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="57ab4-139">Tipo de datos Short</span><span class="sxs-lookup"><span data-stu-id="57ab4-139">Short Data Type</span></span>](short-data-type.md)
- [<span data-ttu-id="57ab4-140">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="57ab4-140">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="57ab4-141">Resumen de las conversiones</span><span class="sxs-lookup"><span data-stu-id="57ab4-141">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="57ab4-142">Uso eficiente de los tipos de datos</span><span class="sxs-lookup"><span data-stu-id="57ab4-142">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)

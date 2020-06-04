---
title: Like (Operador)
ms.date: 07/20/2015
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
ms.openlocfilehash: 4279d90c74c80403146448a8ba5a6051ec9d12f6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401566"
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="5d27d-102">Like (operador, Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d27d-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="5d27d-103">Compara una cadena con un patrón.</span><span class="sxs-lookup"><span data-stu-id="5d27d-103">Compares a string against a pattern.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="5d27d-104">El `Like` operador no se admite actualmente en los proyectos de .net Core y .net Standard.</span><span class="sxs-lookup"><span data-stu-id="5d27d-104">The `Like` operator is currently not supported in .NET Core and .NET Standard projects.</span></span>

## <a name="syntax"></a><span data-ttu-id="5d27d-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5d27d-105">Syntax</span></span>  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="5d27d-106">Partes</span><span class="sxs-lookup"><span data-stu-id="5d27d-106">Parts</span></span>  
 `result`  
 <span data-ttu-id="5d27d-107">Necesario.</span><span class="sxs-lookup"><span data-stu-id="5d27d-107">Required.</span></span> <span data-ttu-id="5d27d-108">Cualquier `Boolean` variable.</span><span class="sxs-lookup"><span data-stu-id="5d27d-108">Any `Boolean` variable.</span></span> <span data-ttu-id="5d27d-109">El resultado es un `Boolean` valor que indica si el satisface o no `string` el `pattern` .</span><span class="sxs-lookup"><span data-stu-id="5d27d-109">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="5d27d-110">Necesario.</span><span class="sxs-lookup"><span data-stu-id="5d27d-110">Required.</span></span> <span data-ttu-id="5d27d-111">Cualquier expresión `String` .</span><span class="sxs-lookup"><span data-stu-id="5d27d-111">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="5d27d-112">Necesario.</span><span class="sxs-lookup"><span data-stu-id="5d27d-112">Required.</span></span> <span data-ttu-id="5d27d-113">Cualquier `String` expresión que se ajuste a las convenciones de coincidencia de patrones descritas en "Comentarios".</span><span class="sxs-lookup"><span data-stu-id="5d27d-113">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d27d-114">Observaciones</span><span class="sxs-lookup"><span data-stu-id="5d27d-114">Remarks</span></span>  
 <span data-ttu-id="5d27d-115">Si el valor de `string` satisface el modelo contenido en `pattern` , `result` es `True` .</span><span class="sxs-lookup"><span data-stu-id="5d27d-115">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="5d27d-116">Si la cadena no satisface el modelo, `result` es `False` .</span><span class="sxs-lookup"><span data-stu-id="5d27d-116">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="5d27d-117">Si `string` y `pattern` son cadenas vacías, el resultado es `True` .</span><span class="sxs-lookup"><span data-stu-id="5d27d-117">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="5d27d-118">Método de comparación</span><span class="sxs-lookup"><span data-stu-id="5d27d-118">Comparison Method</span></span>  
 <span data-ttu-id="5d27d-119">El comportamiento del `Like` operador depende de la [instrucción Option Compare](../statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d27d-119">The behavior of the `Like` operator depends on the [Option Compare Statement](../statements/option-compare-statement.md).</span></span> <span data-ttu-id="5d27d-120">El método predeterminado de comparación de cadenas para cada archivo de código fuente es `Option Compare Binary` .</span><span class="sxs-lookup"><span data-stu-id="5d27d-120">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="5d27d-121">Opciones de patrón</span><span class="sxs-lookup"><span data-stu-id="5d27d-121">Pattern Options</span></span>  
 <span data-ttu-id="5d27d-122">La coincidencia de patrones integrada proporciona una herramienta versátil para comparaciones de cadenas.</span><span class="sxs-lookup"><span data-stu-id="5d27d-122">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="5d27d-123">Las características de coincidencia de patrones permiten buscar coincidencias con cada carácter de `string` un carácter específico, un carácter comodín, una lista de caracteres o un intervalo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5d27d-123">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="5d27d-124">En la tabla siguiente se muestran los caracteres `pattern` que se permiten en y en qué coinciden.</span><span class="sxs-lookup"><span data-stu-id="5d27d-124">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="5d27d-125">Caracteres en`pattern`</span><span class="sxs-lookup"><span data-stu-id="5d27d-125">Characters in `pattern`</span></span>|<span data-ttu-id="5d27d-126">Coincidencias en`string`</span><span class="sxs-lookup"><span data-stu-id="5d27d-126">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="5d27d-127">Un carácter cualquiera</span><span class="sxs-lookup"><span data-stu-id="5d27d-127">Any single character</span></span>|  
|`*`|<span data-ttu-id="5d27d-128">Cero o más caracteres</span><span class="sxs-lookup"><span data-stu-id="5d27d-128">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="5d27d-129">Cualquier dígito individual (0 – 9)</span><span class="sxs-lookup"><span data-stu-id="5d27d-129">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="5d27d-130">Cualquier carácter individual de`charlist`</span><span class="sxs-lookup"><span data-stu-id="5d27d-130">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="5d27d-131">Cualquier carácter individual que no esté en`charlist`</span><span class="sxs-lookup"><span data-stu-id="5d27d-131">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="5d27d-132">Listas de caracteres</span><span class="sxs-lookup"><span data-stu-id="5d27d-132">Character Lists</span></span>  
 <span data-ttu-id="5d27d-133">Un grupo de uno o más caracteres ( `charlist` ) encerrado entre corchetes ( `[ ]` ) se puede usar para buscar coincidencias con cualquier carácter individual de `string` y puede incluir prácticamente cualquier código de carácter, incluidos los dígitos.</span><span class="sxs-lookup"><span data-stu-id="5d27d-133">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="5d27d-134">Un signo de exclamación ( `!` ) al principio de `charlist` significa que se realiza una coincidencia si se encuentra algún carácter excepto los caracteres de en `charlist` `string` .</span><span class="sxs-lookup"><span data-stu-id="5d27d-134">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="5d27d-135">Cuando se usa fuera de corchetes, el signo de exclamación coincide con sí mismo.</span><span class="sxs-lookup"><span data-stu-id="5d27d-135">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="5d27d-136">Caracteres especiales</span><span class="sxs-lookup"><span data-stu-id="5d27d-136">Special Characters</span></span>  
 <span data-ttu-id="5d27d-137">Para que coincida con los caracteres especiales, corchete de apertura ( `[` ), signo de interrogación ( `?` ), signo de número ( `#` ) y asterisco ( `*` ), escríbalos entre corchetes.</span><span class="sxs-lookup"><span data-stu-id="5d27d-137">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="5d27d-138">El corchete de cierre ( `]` ) no se puede usar dentro de un grupo para que coincida, pero se puede usar fuera de un grupo como un carácter individual.</span><span class="sxs-lookup"><span data-stu-id="5d27d-138">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="5d27d-139">La secuencia de caracteres `[]` se considera una cadena de longitud cero ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="5d27d-139">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="5d27d-140">Sin embargo, no puede formar parte de una lista de caracteres entre corchetes.</span><span class="sxs-lookup"><span data-stu-id="5d27d-140">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="5d27d-141">Si desea comprobar si una posición en `string` contiene uno de un grupo de caracteres o ningún carácter, puede usar `Like` dos veces.</span><span class="sxs-lookup"><span data-stu-id="5d27d-141">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="5d27d-142">Para obtener un ejemplo, vea [Cómo: buscar coincidencias de una cadena con un patrón](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="5d27d-142">For an example, see [How to: Match a String against a Pattern](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="5d27d-143">Intervalos de caracteres</span><span class="sxs-lookup"><span data-stu-id="5d27d-143">Character Ranges</span></span>  
 <span data-ttu-id="5d27d-144">Si usa un guión ( `–` ) para separar los límites inferior y superior del intervalo, `charlist` puede especificar un intervalo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5d27d-144">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="5d27d-145">Por ejemplo, `[A–Z]` da como resultado una coincidencia si la posición del carácter correspondiente en `string` contiene cualquier carácter dentro del intervalo `A` – `Z` , y `[!H–L]` da como resultado una coincidencia si la posición del carácter correspondiente contiene algún carácter fuera del intervalo `H` : `L` .</span><span class="sxs-lookup"><span data-stu-id="5d27d-145">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="5d27d-146">Cuando se especifica un intervalo de caracteres, deben aparecer en orden ascendente, es decir, de menor a mayor.</span><span class="sxs-lookup"><span data-stu-id="5d27d-146">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="5d27d-147">Por lo tanto, `[A–Z]` es un patrón válido, pero `[Z–A]` no lo es.</span><span class="sxs-lookup"><span data-stu-id="5d27d-147">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="5d27d-148">Varios intervalos de caracteres</span><span class="sxs-lookup"><span data-stu-id="5d27d-148">Multiple Character Ranges</span></span>  
 <span data-ttu-id="5d27d-149">Para especificar varios intervalos para la misma posición de carácter, colóquelos dentro de los mismos corchetes sin delimitadores.</span><span class="sxs-lookup"><span data-stu-id="5d27d-149">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="5d27d-150">Por ejemplo, `[A–CX–Z]` da como resultado una coincidencia si la posición del carácter correspondiente en `string` contiene cualquier carácter dentro del intervalo `A` , `C` o del `X` intervalo `Z` .</span><span class="sxs-lookup"><span data-stu-id="5d27d-150">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="5d27d-151">Uso del guión</span><span class="sxs-lookup"><span data-stu-id="5d27d-151">Usage of the Hyphen</span></span>  
 <span data-ttu-id="5d27d-152">Un guion ( `–` ) puede aparecer al principio (después de un signo de exclamación, si existe) o al final de `charlist` para que coincida.</span><span class="sxs-lookup"><span data-stu-id="5d27d-152">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="5d27d-153">En cualquier otra ubicación, el guión identifica un intervalo de caracteres delimitado por los caracteres situados a cada lado del guión.</span><span class="sxs-lookup"><span data-stu-id="5d27d-153">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="5d27d-154">Secuencia de intercalación</span><span class="sxs-lookup"><span data-stu-id="5d27d-154">Collating Sequence</span></span>  
 <span data-ttu-id="5d27d-155">El significado de un intervalo especificado depende del orden de los caracteres en tiempo de ejecución, según determina `Option Compare` y la configuración regional del sistema en el que se ejecuta el código.</span><span class="sxs-lookup"><span data-stu-id="5d27d-155">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="5d27d-156">Con `Option Compare Binary` , el intervalo `[A–E]` coincide con `A` ,, `B` `C` , `D` y `E` .</span><span class="sxs-lookup"><span data-stu-id="5d27d-156">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="5d27d-157">Con, coincide con,,,,,,,,,, `Option Compare Text` `[A–E]` `A` `a` `À` `à` `B` `b` `C` `c` `D` `d` `E` y `e` .</span><span class="sxs-lookup"><span data-stu-id="5d27d-157">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="5d27d-158">El intervalo no coincide `Ê` o `ê` porque los caracteres acentuados se intercalan después de los caracteres no acentuados en el criterio de ordenación.</span><span class="sxs-lookup"><span data-stu-id="5d27d-158">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="5d27d-159">Caracteres de dígrafo</span><span class="sxs-lookup"><span data-stu-id="5d27d-159">Digraph Characters</span></span>  
 <span data-ttu-id="5d27d-160">En algunos idiomas, hay caracteres alfabéticos que representan dos caracteres independientes.</span><span class="sxs-lookup"><span data-stu-id="5d27d-160">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="5d27d-161">Por ejemplo, varios lenguajes utilizan el carácter `æ` para representar los caracteres `a` y `e` cuando aparecen juntos.</span><span class="sxs-lookup"><span data-stu-id="5d27d-161">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="5d27d-162">El `Like` operador reconoce que el carácter de un solo gráfico y los dos caracteres individuales son equivalentes.</span><span class="sxs-lookup"><span data-stu-id="5d27d-162">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="5d27d-163">Cuando se especifica un idioma que usa un carácter de dígrafo en la configuración regional del sistema, una aparición del carácter de un solo gráfico en `pattern` o `string` coincide con la secuencia de dos caracteres equivalentes de la otra cadena.</span><span class="sxs-lookup"><span data-stu-id="5d27d-163">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="5d27d-164">Del mismo modo, un carácter de dígrafo `pattern` entre corchetes (por sí solo, en una lista o en un intervalo) coincide con la secuencia de dos caracteres equivalente en `string` .</span><span class="sxs-lookup"><span data-stu-id="5d27d-164">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="5d27d-165">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="5d27d-165">Overloading</span></span>  
 <span data-ttu-id="5d27d-166">El `Like` operador se puede *sobrecargar*, lo que significa que una clase o estructura puede volver a definir su comportamiento cuando un operando tiene el tipo de esa clase o estructura.</span><span class="sxs-lookup"><span data-stu-id="5d27d-166">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="5d27d-167">Si el código usa este operador en una clase o estructura de este tipo, asegúrese de entender su comportamiento redefinido.</span><span class="sxs-lookup"><span data-stu-id="5d27d-167">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="5d27d-168">Para obtener más información, consulta [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5d27d-168">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d27d-169">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="5d27d-169">Example</span></span>  
 <span data-ttu-id="5d27d-170">En este ejemplo se usa el `Like` operador para comparar cadenas con varios patrones.</span><span class="sxs-lookup"><span data-stu-id="5d27d-170">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="5d27d-171">Los resultados se incluyen en una `Boolean` variable que indica si cada cadena satisface el modelo.</span><span class="sxs-lookup"><span data-stu-id="5d27d-171">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="5d27d-172">Consulte también</span><span class="sxs-lookup"><span data-stu-id="5d27d-172">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="5d27d-173">Operadores de comparación</span><span class="sxs-lookup"><span data-stu-id="5d27d-173">Comparison Operators</span></span>](comparison-operators.md)
- [<span data-ttu-id="5d27d-174">Prioridad de operador en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d27d-174">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="5d27d-175">Lista de operadores según funcionalidad</span><span class="sxs-lookup"><span data-stu-id="5d27d-175">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="5d27d-176">Option Compare (instrucción)</span><span class="sxs-lookup"><span data-stu-id="5d27d-176">Option Compare Statement</span></span>](../statements/option-compare-statement.md)
- [<span data-ttu-id="5d27d-177">Operadores y expresiones</span><span class="sxs-lookup"><span data-stu-id="5d27d-177">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="5d27d-178">Procedimiento para comprobar si una cadena coincide con un patrón</span><span class="sxs-lookup"><span data-stu-id="5d27d-178">How to: Match a String against a Pattern</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)

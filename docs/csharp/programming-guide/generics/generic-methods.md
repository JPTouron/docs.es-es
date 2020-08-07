---
title: 'Métodos genéricos: Guía de programación de C#'
description: Aprenda sobre los métodos declarados con parámetros de tipo, conocidos como métodos genéricos. Vea ejemplos de código y examine los recursos adicionales disponibles.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 77b81de26961a8b59644643bf043ed723dbf374f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301884"
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="ea951-104">Métodos genéricos (Guía de programación de C#)</span><span class="sxs-lookup"><span data-stu-id="ea951-104">Generic Methods (C# Programming Guide)</span></span>
<span data-ttu-id="ea951-105">Un método genérico es un método que se declara con parámetros de tipo, de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="ea951-105">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 <span data-ttu-id="ea951-106">En el siguiente ejemplo de código se muestra una manera de llamar al método con `int` para el argumento de tipo:</span><span class="sxs-lookup"><span data-stu-id="ea951-106">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 <span data-ttu-id="ea951-107">También puede omitir el argumento de tipo y el compilador lo deducirá.</span><span class="sxs-lookup"><span data-stu-id="ea951-107">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="ea951-108">La siguiente llamada a `Swap` es equivalente a la llamada anterior:</span><span class="sxs-lookup"><span data-stu-id="ea951-108">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 <span data-ttu-id="ea951-109">Las mismas reglas para la inferencia de tipos se aplican a los métodos estáticos y a los métodos de instancia.</span><span class="sxs-lookup"><span data-stu-id="ea951-109">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="ea951-110">El compilador puede deducir los parámetros de tipo basados en los argumentos de método que se pasan; no puede deducir los parámetros de tipo solo desde un valor devuelto o una restricción.</span><span class="sxs-lookup"><span data-stu-id="ea951-110">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="ea951-111">Por lo tanto, la inferencia de tipos no funciona con métodos que no tienen parámetros.</span><span class="sxs-lookup"><span data-stu-id="ea951-111">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="ea951-112">La inferencia de tipos se produce en tiempo de compilación antes de que el compilador intente resolver las firmas de método sobrecargadas.</span><span class="sxs-lookup"><span data-stu-id="ea951-112">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="ea951-113">El compilador aplica la lógica de inferencia de tipos a todos los métodos genéricos que comparten el mismo nombre.</span><span class="sxs-lookup"><span data-stu-id="ea951-113">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="ea951-114">En el paso de resolución de sobrecarga, el compilador incluye solo esos métodos genéricos en los que la inferencia de tipos se ha realizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="ea951-114">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="ea951-115">Dentro de una clase genérica, los métodos no genéricos pueden tener acceso a los parámetros de tipo de nivel de clase, de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="ea951-115">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 <span data-ttu-id="ea951-116">Si define un método genérico que toma los mismos parámetros de tipo que la clase contenedora, el compilador genera la advertencia [CS0693](../../misc/cs0693.md) porque, dentro del ámbito del método, el argumento que se ha proporcionado para el `T` interno oculta el argumento que se ha proporcionado para el `T` externo.</span><span class="sxs-lookup"><span data-stu-id="ea951-116">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning [CS0693](../../misc/cs0693.md) because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="ea951-117">Si necesita la flexibilidad de llamar a un método de la clase genérica con argumentos de tipo diferentes de los que se han proporcionado cuando se ha creado una instancia de la clase, considere la posibilidad de proporcionar otro identificador para el parámetro de tipo del método, como se muestra en `GenericList2<T>` en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="ea951-117">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 <span data-ttu-id="ea951-118">Use restricciones para permitir operaciones más especializadas en parámetros de tipo de métodos.</span><span class="sxs-lookup"><span data-stu-id="ea951-118">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="ea951-119">Esta versión de `Swap<T>`, ahora denominada `SwapIfGreater<T>`, solo puede usarse con argumentos de tipo que implementan <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="ea951-119">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 <span data-ttu-id="ea951-120">Los métodos genéricos pueden sobrecargarse en varios parámetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="ea951-120">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="ea951-121">Por ejemplo, todos los métodos siguientes pueden ubicarse en la misma clase:</span><span class="sxs-lookup"><span data-stu-id="ea951-121">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="ea951-122">Especificación del lenguaje C#</span><span class="sxs-lookup"><span data-stu-id="ea951-122">C# Language Specification</span></span>  
 <span data-ttu-id="ea951-123">Para obtener más información, consulte la [Especificación del lenguaje C#](~/_csharplang/spec/classes.md#methods).</span><span class="sxs-lookup"><span data-stu-id="ea951-123">For more information, see the [C# Language Specification](~/_csharplang/spec/classes.md#methods).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea951-124">Vea también</span><span class="sxs-lookup"><span data-stu-id="ea951-124">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="ea951-125">Guía de programación de C#</span><span class="sxs-lookup"><span data-stu-id="ea951-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ea951-126">Introducción a los genéricos</span><span class="sxs-lookup"><span data-stu-id="ea951-126">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="ea951-127">Métodos</span><span class="sxs-lookup"><span data-stu-id="ea951-127">Methods</span></span>](../classes-and-structs/methods.md)

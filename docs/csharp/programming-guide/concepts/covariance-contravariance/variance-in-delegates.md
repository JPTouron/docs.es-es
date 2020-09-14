---
title: Varianza en delegados (C#)
description: Obtenga información sobre cómo la compatibilidad de la varianza en .NET permite hacer coincidir firmas de método con tipos de delegados en todos los delegados.
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: 02b59dd97cedc6ab35c3122912ee528f7ca29238
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2020
ms.locfileid: "89466136"
---
# <a name="variance-in-delegates-c"></a><span data-ttu-id="4ebf9-103">Varianza en delegados (C#)</span><span class="sxs-lookup"><span data-stu-id="4ebf9-103">Variance in Delegates (C#)</span></span>
<span data-ttu-id="4ebf9-104">En .NET Framework 3.5 se presentó por primera vez la compatibilidad con la varianza para hacer coincidir firmas de método con tipos de delegados en todos los delegados en C#.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-104">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C#.</span></span> <span data-ttu-id="4ebf9-105">Esto significa que puede asignar a los delegados no solo métodos con firmas coincidentes, sino métodos que devuelven tipos más derivados (covarianza) o que aceptan parámetros con tipos menos derivados (contravarianza) que el especificado por el tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-105">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="4ebf9-106">Esto incluye delegados genéricos y no genéricos.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-106">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="4ebf9-107">Por ejemplo, consideremos el siguiente código, que tiene dos clases y dos delegados: genéricos y no genéricos.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-107">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 <span data-ttu-id="4ebf9-108">Al crear delegados de los tipos `SampleDelegate` o `SampleGenericDelegate<A, R>`, puede asignar uno de los métodos siguientes a dichos delegados.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-108">When you create delegates of the `SampleDelegate` or `SampleGenericDelegate<A, R>` types, you can assign any one of the following methods to those delegates.</span></span>  
  
```csharp  
// Matching signature.  
public static First ASecondRFirst(Second second)  
{ return new First(); }  
  
// The return type is more derived.  
public static Second ASecondRSecond(Second second)  
{ return new Second(); }  
  
// The argument type is less derived.  
public static First AFirstRFirst(First first)  
{ return new First(); }  
  
// The return type is more derived
// and the argument type is less derived.  
public static Second AFirstRSecond(First first)  
{ return new Second(); }  
```  
  
 <span data-ttu-id="4ebf9-109">En el ejemplo de código siguiente se ilustra la conversión implícita entre la firma del método y el tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-109">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
```csharp  
// Assigning a method with a matching signature
// to a non-generic delegate. No conversion is necessary.  
SampleDelegate dNonGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type
// and less derived argument type to a non-generic delegate.  
// The implicit conversion is used.  
SampleDelegate dNonGenericConversion = AFirstRSecond;  
  
// Assigning a method with a matching signature to a generic delegate.  
// No conversion is necessary.  
SampleGenericDelegate<Second, First> dGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type
// and less derived argument type to a generic delegate.  
// The implicit conversion is used.  
SampleGenericDelegate<Second, First> dGenericConversion = AFirstRSecond;  
```  
  
 <span data-ttu-id="4ebf9-110">Para obtener más ejemplos, vea [Usar varianza en delegados (C#)](./using-variance-in-delegates.md) y [Usar la varianza para los delegados genéricos Func y Action (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="4ebf9-110">For more examples, see [Using Variance in Delegates (C#)](./using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="4ebf9-111">Varianza en parámetros de tipo genérico</span><span class="sxs-lookup"><span data-stu-id="4ebf9-111">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="4ebf9-112">En .NET Framework 4 o posterior puede habilitar la conversión implícita entre los delegados, de modo que los delegados genéricos con tipos diferentes especificados por parámetros de tipo genérico se puedan asignar entre sí, en el caso de que los tipos se hereden entre sí, como requiere la varianza.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-112">In .NET Framework 4 or later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="4ebf9-113">Para habilitar la conversión implícita, debe declarar explícitamente parámetros genéricos en un delegado como covariante o contravariante mediante la palabra clave `in` o `out`.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-113">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="4ebf9-114">En el ejemplo de código siguiente se muestra cómo se crea un delegado que tiene un parámetro de tipo genérico covariante.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-114">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
```csharp  
// Type T is declared covariant by using the out keyword.  
public delegate T SampleGenericDelegate <out T>();  
  
public static void Test()  
{  
    SampleGenericDelegate <String> dString = () => " ";  
  
    // You can assign delegates to each other,  
    // because the type T is declared covariant.  
    SampleGenericDelegate <Object> dObject = dString;
}  
```  
  
 <span data-ttu-id="4ebf9-115">Si usa solo la compatibilidad con la varianza para hacer coincidir firmas de método con tipos de delegados y no usa las palabras clave `in` y `out`, es posible que en algunas ocasiones pueda crear instancias de delegados con métodos o expresiones lambda idénticos, pero no pueda asignar un delegado a otro.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-115">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="4ebf9-116">En el ejemplo de código siguiente, `SampleGenericDelegate<String>` no se puede convertir explícitamente a `SampleGenericDelegate<Object>`, aunque `String` hereda `Object`.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-116">In the following code example, `SampleGenericDelegate<String>` cannot be explicitly converted to `SampleGenericDelegate<Object>`, although `String` inherits `Object`.</span></span> <span data-ttu-id="4ebf9-117">Para solucionar este problema, marque el parámetro genérico `T` con la palabra clave `out`.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-117">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
```csharp  
public delegate T SampleGenericDelegate<T>();  
  
public static void Test()  
{  
    SampleGenericDelegate<String> dString = () => " ";  
  
    // You can assign the dObject delegate  
    // to the same lambda expression as dString delegate  
    // because of the variance support for
    // matching method signatures with delegate types.  
    SampleGenericDelegate<Object> dObject = () => " ";  
  
    // The following statement generates a compiler error  
    // because the generic type T is not marked as covariant.  
    // SampleGenericDelegate <Object> dObject = dString;  
  
}  
```  
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-net"></a><span data-ttu-id="4ebf9-118">Delegados genéricos con parámetros de tipo variante en .NET</span><span class="sxs-lookup"><span data-stu-id="4ebf9-118">Generic Delegates That Have Variant Type Parameters in .NET</span></span>

<span data-ttu-id="4ebf9-119">En .NET Framework 4 se presentó por primera vez la compatibilidad con la varianza para los parámetros de tipo genérico en varios delegados genéricos existentes:</span><span class="sxs-lookup"><span data-stu-id="4ebf9-119">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
- <span data-ttu-id="4ebf9-120">`Action` delega del espacio de nombres <xref:System>, por ejemplo, <xref:System.Action%601> y <xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="4ebf9-120">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
- <span data-ttu-id="4ebf9-121">`Func` delega del espacio de nombres <xref:System>, por ejemplo, <xref:System.Func%601> y <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="4ebf9-121">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
- <span data-ttu-id="4ebf9-122">Delegado <xref:System.Predicate%601>.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-122">The <xref:System.Predicate%601> delegate</span></span>  
  
- <span data-ttu-id="4ebf9-123">Delegado <xref:System.Comparison%601>.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-123">The <xref:System.Comparison%601> delegate</span></span>  
  
- <span data-ttu-id="4ebf9-124">Delegado <xref:System.Converter%602>.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-124">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="4ebf9-125">Para obtener más información y ejemplos, vea [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md) (Usar varianza para delegados genéricos Func y Action (C#)).</span><span class="sxs-lookup"><span data-stu-id="4ebf9-125">For more information and examples, see [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="4ebf9-126">Declarar parámetros de tipo variante en delegados genéricos</span><span class="sxs-lookup"><span data-stu-id="4ebf9-126">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="4ebf9-127">Si un delegado genérico tiene parámetros de tipo genérico covariante o contravariante, se puede hacer referencia a él como un *delegado genérico variante*.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-127">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="4ebf9-128">Puede declarar un parámetro de tipo genérico covariante en un delegado genérico mediante la palabra clave `out`.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-128">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="4ebf9-129">El tipo covariante puede usarse solo como un tipo de valor devuelto de método, y no como un tipo de argumentos de método.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-129">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="4ebf9-130">En el siguiente ejemplo de código se muestra cómo declarar un delegado genérico covariante.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-130">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 <span data-ttu-id="4ebf9-131">Puede declarar un parámetro de tipo genérico contravariante en un delegado genérico mediante la palabra clave `in`.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-131">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="4ebf9-132">El tipo contravariante puede usarse solo como un tipo de argumentos de método, y no como un tipo de valor devuelto de método.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-132">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="4ebf9-133">En el siguiente ejemplo de código se muestra cómo declarar un delegado genérico contravariante.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-133">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="4ebf9-134">Los parámetros `ref`, `in` y `out` de C# no se pueden marcar como variantes.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-134">`ref`, `in`, and `out` parameters in C# can't be marked as variant.</span></span>  
  
 <span data-ttu-id="4ebf9-135">También es posible admitir la varianza y la covarianza en el mismo delegado, pero para parámetros de tipo diferentes.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-135">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="4ebf9-136">Esta implementación se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-136">This is shown in the following example.</span></span>  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="4ebf9-137">Crear instancias de delegados genéricos variantes e invocarlos</span><span class="sxs-lookup"><span data-stu-id="4ebf9-137">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="4ebf9-138">Puede crear instancias de delegados variantes e invocarlos del mismo modo que crea instancias de delegados invariables y los invoca.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-138">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="4ebf9-139">En el ejemplo siguiente, se crea una instancia del delegado mediante una expresión lambda.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-139">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="4ebf9-140">Combinar delegados genéricos variantes</span><span class="sxs-lookup"><span data-stu-id="4ebf9-140">Combining Variant Generic Delegates</span></span>  

<span data-ttu-id="4ebf9-141">No combine delegados variantes.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-141">Don't combine variant delegates.</span></span> <span data-ttu-id="4ebf9-142">El método <xref:System.Delegate.Combine%2A> no admite la conversión de delegados variantes y espera que los delegados sean exactamente del mismo tipo.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-142">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="4ebf9-143">Esto puede provocar una excepción en tiempo de ejecución cuando se combinan delegados mediante el método <xref:System.Delegate.Combine%2A> o mediante el operador `+`, como se muestra en el ejemplo de código siguiente.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-143">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method or by using the `+` operator, as shown in the following code example.</span></span>  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="4ebf9-144">Varianza en parámetros de tipo genérico para los tipos de referencia y valor</span><span class="sxs-lookup"><span data-stu-id="4ebf9-144">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="4ebf9-145">La varianza para parámetros de tipo genérico solo es compatible con tipos de referencia.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-145">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="4ebf9-146">Por ejemplo, `DVariant<int>` no se puede convertir implícitamente en `DVariant<Object>` o `DVariant<long>`, porque un entero es un tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-146">For example, `DVariant<int>` can't be implicitly converted to `DVariant<Object>` or `DVariant<long>`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="4ebf9-147">En el ejemplo siguiente se muestra que la varianza en parámetros de tipo genérico no se admite para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="4ebf9-147">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
```csharp  
// The type T is covariant.  
public delegate T DVariant<out T>();  
  
// The type T is invariant.  
public delegate T DInvariant<T>();  
  
public static void Test()  
{  
    int i = 0;  
    DInvariant<int> dInt = () => i;  
    DVariant<int> dVariantInt = () => i;  
  
    // All of the following statements generate a compiler error  
    // because type variance in generic parameters is not supported  
    // for value types, even if generic type parameters are declared variant.  
    // DInvariant<Object> dObject = dInt;  
    // DInvariant<long> dLong = dInt;  
    // DVariant<Object> dVariantObject = dVariantInt;  
    // DVariant<long> dVariantLong = dVariantInt;
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ebf9-148">Vea también</span><span class="sxs-lookup"><span data-stu-id="4ebf9-148">See also</span></span>

- [<span data-ttu-id="4ebf9-149">Genéricos</span><span class="sxs-lookup"><span data-stu-id="4ebf9-149">Generics</span></span>](../../../../standard/generics/index.md)
- [<span data-ttu-id="4ebf9-150">Usar varianza para los delegados genéricos Func y Action (C#)</span><span class="sxs-lookup"><span data-stu-id="4ebf9-150">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
- [<span data-ttu-id="4ebf9-151">Procedimiento para combinar delegados (delegados de multidifusión)</span><span class="sxs-lookup"><span data-stu-id="4ebf9-151">How to combine delegates (Multicast Delegates)</span></span>](../../delegates/how-to-combine-delegates-multicast-delegates.md)

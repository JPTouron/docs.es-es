---
title: 'Personalización de la serialización de estructuras: .NET'
description: Obtenga información sobre cómo personalizar la forma en que .NET serializa las estructuras de una representación nativa.
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 8248ca589f41967a9112ba61c09599b337814de7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003898"
---
# <a name="customizing-structure-marshaling"></a><span data-ttu-id="1b062-103">Personalización de la serialización de estructuras</span><span class="sxs-lookup"><span data-stu-id="1b062-103">Customizing structure marshaling</span></span>

<span data-ttu-id="1b062-104">A veces, las reglas de serialización predeterminadas para las estructuras no es exactamente lo que necesita.</span><span class="sxs-lookup"><span data-stu-id="1b062-104">Sometimes the default marshaling rules for structures aren't exactly what you need.</span></span> <span data-ttu-id="1b062-105">Los entornos de ejecución de .NET proporcionan unos puntos de extensión que permiten personalizar el diseño de la estructura y cómo se serializan los campos.</span><span class="sxs-lookup"><span data-stu-id="1b062-105">The .NET runtimes provide a few extension points for you to customize your structure's layout and how fields are marshaled.</span></span>

## <a name="customizing-structure-layout"></a><span data-ttu-id="1b062-106">Personalización del diseño de estructuras</span><span class="sxs-lookup"><span data-stu-id="1b062-106">Customizing structure layout</span></span>

<span data-ttu-id="1b062-107">.NET proporciona el atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> y la enumeración <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> para poder personalizar cómo se colocan los campos en la memoria.</span><span class="sxs-lookup"><span data-stu-id="1b062-107">.NET provides the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> attribute and the <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> enumeration to allow you to customize how fields are placed in memory.</span></span> <span data-ttu-id="1b062-108">Las siguientes instrucciones lo ayudarán a evitar problemas comunes.</span><span class="sxs-lookup"><span data-stu-id="1b062-108">The following guidance will help you avoid common issues.</span></span>

<span data-ttu-id="1b062-109">✔️ PLANTÉESE usar `LayoutKind.Sequential` siempre que sea posible.</span><span class="sxs-lookup"><span data-stu-id="1b062-109">✔️ CONSIDER using `LayoutKind.Sequential` whenever possible.</span></span>

<span data-ttu-id="1b062-110">✔️ USE solo `LayoutKind.Explicit` en la serialización cuando la estructura nativa tenga un diseño explícito, como una unión.</span><span class="sxs-lookup"><span data-stu-id="1b062-110">✔️ DO only use `LayoutKind.Explicit` in marshaling when your native struct also has an explicit layout, such as a union.</span></span>

<span data-ttu-id="1b062-111">❌ EVITE usar `LayoutKind.Explicit` al serializar estructuras en plataformas que no son de Windows si tiene como destino runtimes anteriores a .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="1b062-111">❌ AVOID using `LayoutKind.Explicit` when marshaling structures on non-Windows platforms if you need to target runtimes before .NET Core 3.0.</span></span> <span data-ttu-id="1b062-112">El runtime de .NET Core anterior a 3.0 no admite pasar estructuras explícitas por valor a funciones nativas en sistemas que no sean Windows Intel o AMD de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="1b062-112">The .NET Core runtime before 3.0 doesn't support passing explicit structures by value to native functions on Intel or AMD 64-bit non-Windows systems.</span></span> <span data-ttu-id="1b062-113">Sin embargo, el entorno de ejecución admite pasar estructuras explícitas por referencia en todas las plataformas.</span><span class="sxs-lookup"><span data-stu-id="1b062-113">However, the runtime supports passing explicit structures by reference on all platforms.</span></span>

## <a name="customizing-boolean-field-marshaling"></a><span data-ttu-id="1b062-114">Personalización de la serialización de campos booleanos</span><span class="sxs-lookup"><span data-stu-id="1b062-114">Customizing boolean field marshaling</span></span>

<span data-ttu-id="1b062-115">El código nativo tiene muchas representaciones booleanas diferentes.</span><span class="sxs-lookup"><span data-stu-id="1b062-115">Native code has many different boolean representations.</span></span> <span data-ttu-id="1b062-116">En Windows, hay tres formas de representar valores booleanos.</span><span class="sxs-lookup"><span data-stu-id="1b062-116">On Windows alone, there are three ways to represent boolean values.</span></span> <span data-ttu-id="1b062-117">El entorno de ejecución no sabe la definición nativa de la estructura, por lo que se recomienda realizar una estimación sobre cómo serializar los valores booleanos.</span><span class="sxs-lookup"><span data-stu-id="1b062-117">The runtime doesn't know the native definition of your structure, so the best it can do is make a guess on how to marshal your boolean values.</span></span> <span data-ttu-id="1b062-118">El entorno de ejecución de .NET proporciona una manera de indicar cómo serializar el campo booleano.</span><span class="sxs-lookup"><span data-stu-id="1b062-118">The .NET runtime provides a way to indicate how to marshal your boolean field.</span></span> <span data-ttu-id="1b062-119">En los ejemplos siguientes se muestra cómo serializar el tipo `bool` de .NET a diferentes tipos nativos booleanos.</span><span class="sxs-lookup"><span data-stu-id="1b062-119">The following examples show how to marshal .NET `bool` to different native boolean types.</span></span>

<span data-ttu-id="1b062-120">Los valores booleanos predeterminados se ordenan como un valor nativo de 4 bytes de Win32 [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) como se muestra en el siguiente ejemplo:</span><span class="sxs-lookup"><span data-stu-id="1b062-120">Boolean values default to marshaling as a native 4-byte Win32 [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) value as shown in the following example:</span></span>

```csharp
public struct WinBool
{
    public bool b;
}
```

```cpp
struct WinBool
{
    public BOOL b;
};
```

<span data-ttu-id="1b062-121">Si desea ser explícito, puede usar el valor <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> para obtener el mismo comportamiento que el anterior:</span><span class="sxs-lookup"><span data-stu-id="1b062-121">If you want to be explicit, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> value to get the same behavior as above:</span></span>

```csharp
public struct WinBool
{
    [MarshalAs(UnmanagedType.Bool)]
    public bool b;
}
```

```cpp
struct WinBool
{
    public BOOL b;
};
```

<span data-ttu-id="1b062-122">Mediante los valores `UnmanagedType.U1` o `UnmanagedType.I1`, puede indicar el entorno de ejecución para serializar el campo `b` como un tipo `bool` nativo de 1 byte.</span><span class="sxs-lookup"><span data-stu-id="1b062-122">Using the `UnmanagedType.U1` or `UnmanagedType.I1` values below, you can tell the runtime to marshal the `b` field as a 1-byte native `bool` type.</span></span>

```csharp
public struct CBool
{
    [MarshalAs(UnmanagedType.U1)]
    public bool b;
}
```

```cpp
struct CBool
{
    public bool b;
};
```

<span data-ttu-id="1b062-123">En Windows, puede usar el valor <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> para indicar al entorno de ejecución que serialice el valor booleano a un valor `VARIANT_BOOL` de 2 bytes:</span><span class="sxs-lookup"><span data-stu-id="1b062-123">On Windows, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> value to tell the runtime to marshal your boolean value to a 2-byte `VARIANT_BOOL` value:</span></span>

```csharp
public struct VariantBool
{
    [MarshalAs(UnmanagedType.VariantBool)]
    public bool b;
}
```

```cpp
struct VariantBool
{
    public VARIANT_BOOL b;
};
```

> [!NOTE]
> <span data-ttu-id="1b062-124">`VARIANT_BOOL` es diferente de la mayoría de los tipos booleanos de `VARIANT_TRUE = -1` y `VARIANT_FALSE = 0`.</span><span class="sxs-lookup"><span data-stu-id="1b062-124">`VARIANT_BOOL` is different than most bool types in that `VARIANT_TRUE = -1` and `VARIANT_FALSE = 0`.</span></span> <span data-ttu-id="1b062-125">Además, todos los valores que no son iguales a `VARIANT_TRUE` se consideran false.</span><span class="sxs-lookup"><span data-stu-id="1b062-125">Additionally, all values that aren't equal to `VARIANT_TRUE` are considered false.</span></span>

## <a name="customizing-array-field-marshaling"></a><span data-ttu-id="1b062-126">Personalización de la serialización de campos de matriz</span><span class="sxs-lookup"><span data-stu-id="1b062-126">Customizing array field marshaling</span></span>

<span data-ttu-id="1b062-127">.NET también incluye algunos ejemplos de cómo personalizar la serialización de matrices.</span><span class="sxs-lookup"><span data-stu-id="1b062-127">.NET also includes a few ways to customize array marshaling.</span></span>

<span data-ttu-id="1b062-128">De forma predeterminada, .NET serializa las matrices como un puntero a una lista contigua de elementos:</span><span class="sxs-lookup"><span data-stu-id="1b062-128">By default, .NET marshals arrays as a pointer to a contiguous list of the elements:</span></span>

```csharp
public struct DefaultArray
{
    public int[] values;
}
```

```cpp
struct DefaultArray
{
    int* values;
};
```

<span data-ttu-id="1b062-129">Si está interactuando con API de COM, es posible que deba serializar las matrices como objetos `SAFEARRAY*`.</span><span class="sxs-lookup"><span data-stu-id="1b062-129">If you're interfacing with COM APIs, you may have to marshal arrays as `SAFEARRAY*` objects.</span></span> <span data-ttu-id="1b062-130">Puede usar <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> y el valor <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> para indicar al entorno de ejecución que serialice una matriz como `SAFEARRAY*`:</span><span class="sxs-lookup"><span data-stu-id="1b062-130">You can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> and the <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> value to tell the runtime to marshal an array as a `SAFEARRAY*`:</span></span>

```csharp
public struct SafeArrayExample
{
    [MarshalAs(UnmanagedType.SafeArray)]
    public int[] values;
}
```

```cpp
struct SafeArrayExample
{
    SAFEARRAY* values;
};
```

<span data-ttu-id="1b062-131">Si necesita personalizar qué tipo de elemento se encuentra en `SAFEARRAY`, puede usar los campos <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> y <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> para personalizar el elemento exacto de `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="1b062-131">If you need to customize what type of element is in the `SAFEARRAY`, then you can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> fields to customize the exact element type of the `SAFEARRAY`.</span></span>

<span data-ttu-id="1b062-132">Si necesita serializar la matriz en contexto, puede usar el valor <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> para indicar el serializador con el fin de serializar la matriz en contexto.</span><span class="sxs-lookup"><span data-stu-id="1b062-132">If you need to marshal the array in-place, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> value to tell the marshaler to marshal the array in-place.</span></span> <span data-ttu-id="1b062-133">Cuando se usa esta serialización, también se debe proporcionar un valor al campo <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> del número de elementos de la matriz para que el entorno de ejecución pueda asignar correctamente espacio para la estructura.</span><span class="sxs-lookup"><span data-stu-id="1b062-133">When you're using this marshaling, you also must supply a value to the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field  for the number of elements in the array so the runtime can correctly allocate space for the structure.</span></span>

```csharp
public struct InPlaceArray
{
    [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
    public int[] values;
}
```

```cpp
struct InPlaceArray
{
    int values[4];
};
```

> [!NOTE]
> <span data-ttu-id="1b062-134">.NET no admite la serialización de un campo de matriz de longitud variable como un miembro de matriz flexible C99.</span><span class="sxs-lookup"><span data-stu-id="1b062-134">.NET doesn't support marshaling a variable length array field as a C99 Flexible Array Member.</span></span>

## <a name="customizing-string-field-marshaling"></a><span data-ttu-id="1b062-135">Personalización de la serialización de campos de cadena</span><span class="sxs-lookup"><span data-stu-id="1b062-135">Customizing string field marshaling</span></span>

<span data-ttu-id="1b062-136">.NET también proporciona una amplia variedad de personalizaciones para serializar los campos de cadena.</span><span class="sxs-lookup"><span data-stu-id="1b062-136">.NET also provides a wide variety of customizations for marshaling string fields.</span></span>

<span data-ttu-id="1b062-137">De forma predeterminada, .NET serializa una cadena como un puntero a una cadena terminada en un valor NULL.</span><span class="sxs-lookup"><span data-stu-id="1b062-137">By default, .NET marshals a string as a pointer to a null-terminated string.</span></span> <span data-ttu-id="1b062-138">La codificación depende del valor del campo <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> en <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1b062-138">The encoding depends on the value of the <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> field in the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1b062-139">Si no se especifica ningún atributo, la codificación predeterminada es una codificación ANSI.</span><span class="sxs-lookup"><span data-stu-id="1b062-139">If no attribute is specified, the encoding defaults to an ANSI encoding.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
public struct DefaultString
{
    public string str;
}
```

```cpp
struct DefaultString
{
    char* str;
};
```

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct DefaultString
{
    public string str;
}
```

```cpp
struct DefaultString
{
    char16_t* str; // Could also be wchar_t* on Windows.
};
```

<span data-ttu-id="1b062-140">Si necesita utilizar codificaciones diferentes para los distintos campos o simplemente prefiere ser más explícito en la definición de estructuras, puede usar los valores <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> o <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> en un atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1b062-140">If you need to use different encodings for different fields or just prefer to be more explicit in your struct definition, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> values on a <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> attribute.</span></span>

```csharp
public struct AnsiString
{
    [MarshalAs(UnmanagedType.LPStr)]
    public string str;
}
```

```cpp
struct AnsiString
{
    char* str;
};
```

```csharp
public struct UnicodeString
{
    [MarshalAs(UnmanagedType.LPWStr)]
    public string str;
}
```

```cpp
struct UnicodeString
{
    char16_t* str; // Could also be wchar_t* on Windows.
};
```

<span data-ttu-id="1b062-141">Si desea serializar las cadenas mediante la codificación UTF-8, puede usar el valor <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> en <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1b062-141">If you want to marshal your strings using the UTF-8 encoding, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> value in your <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

```csharp
public struct UTF8String
{
    [MarshalAs(UnmanagedType.LPUTF8Str)]
    public string str;
}
```

```cpp
struct UTF8String
{
    char* str;
};
```

> [!NOTE]
> <span data-ttu-id="1b062-142">El uso de <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> requiere .NET Framework 4.7 (o versiones posteriores) o .NET Core 1.1 (o versiones posteriores).</span><span class="sxs-lookup"><span data-stu-id="1b062-142">Using <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> requires either .NET Framework 4.7 (or later versions) or .NET Core 1.1 (or later versions).</span></span> <span data-ttu-id="1b062-143">No está disponible en .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="1b062-143">It isn't available in .NET Standard 2.0.</span></span>

<span data-ttu-id="1b062-144">Si está trabajando con API de COM, es posible que deba serializar una cadena como `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="1b062-144">If you're working with COM APIs, you may need to marshal a string as a `BSTR`.</span></span> <span data-ttu-id="1b062-145">Mediante el valor <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType>, se puede serializar una cadena como `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="1b062-145">Using the <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> value, you can marshal a string as a `BSTR`.</span></span>

```csharp
public struct BString
{
    [MarshalAs(UnmanagedType.BStr)]
    public string str;
}
```

```cpp
struct BString
{
    BSTR str;
};
```

<span data-ttu-id="1b062-146">Cuando se usa una API basada en WinRT, es posible que deba serializar una cadena como `HSTRING`.</span><span class="sxs-lookup"><span data-stu-id="1b062-146">When using a WinRT-based API, you may need to marshal a string as an `HSTRING`.</span></span>  <span data-ttu-id="1b062-147">Mediante el valor <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType>, se puede serializar una cadena como `HSTRING`.</span><span class="sxs-lookup"><span data-stu-id="1b062-147">Using the <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> value, you can marshal a string as a `HSTRING`.</span></span>

```csharp
public struct HString
{
    [MarshalAs(UnmanagedType.HString)]
    public string str;
}
```

```cpp
struct BString
{
    HSTRING str;
};
```

<span data-ttu-id="1b062-148">Si la API requiere que se pase la cadena en contexto en la estructura, puede usar el valor <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1b062-148">If your API requires you to pass the string in-place in the structure, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="1b062-149">Tenga en cuenta que la codificación de una cadena serializada por `ByValTStr` viene determinada por el atributo `CharSet`.</span><span class="sxs-lookup"><span data-stu-id="1b062-149">Do note that the encoding for a string marshaled by `ByValTStr` is determined from the `CharSet` attribute.</span></span> <span data-ttu-id="1b062-150">Además, requiere que una longitud de cadena se pasa por el campo <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1b062-150">Additionally, it requires that a string length is passed by the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
public struct DefaultString
{
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 4)]
    public string str;
}
```

```cpp
struct DefaultString
{
    char str[4];
};
```

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct DefaultString
{
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 4)]
    public string str;
}
```

```cpp
struct DefaultString
{
    char16_t str[4]; // Could also be wchar_t[4] on Windows.
};
```

## <a name="customizing-decimal-field-marshaling"></a><span data-ttu-id="1b062-151">Personalización de la serialización de campos de decimal</span><span class="sxs-lookup"><span data-stu-id="1b062-151">Customizing decimal field marshaling</span></span>

<span data-ttu-id="1b062-152">Si está trabajando en Windows, puede encontrar algunas API que usan la estructura [`CY` o `CURRENCY`](/windows/win32/api/wtypes/ns-wtypes-cy~r1) nativa.</span><span class="sxs-lookup"><span data-stu-id="1b062-152">If you're working on Windows, you might encounter some APIs that use the native [`CY` or `CURRENCY`](/windows/win32/api/wtypes/ns-wtypes-cy~r1) structure.</span></span> <span data-ttu-id="1b062-153">De forma predeterminada, el tipo `decimal` de .NET serializa a la estructura [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) nativa.</span><span class="sxs-lookup"><span data-stu-id="1b062-153">By default, the .NET `decimal` type marshals to the native [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) structure.</span></span> <span data-ttu-id="1b062-154">Sin embargo, puede usar <xref:System.Runtime.InteropServices.MarshalAsAttribute> con el valor <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> para indicar al serializador que convierta un valor `decimal` al valor `CY` nativo.</span><span class="sxs-lookup"><span data-stu-id="1b062-154">However, you can use a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> value to instruct the marshaler to convert a `decimal` value to a native `CY` value.</span></span>

```csharp
public struct Currency
{
    [MarshalAs(UnmanagedType.Currency)]
    public decimal dec;
}
```

```cpp
struct Currency
{
    CY dec;
};
```

## <a name="marshaling-systemobjects"></a><span data-ttu-id="1b062-155">Serialización de `System.Object`</span><span class="sxs-lookup"><span data-stu-id="1b062-155">Marshaling `System.Object`s</span></span>

<span data-ttu-id="1b062-156">En Windows, puede serializar campos con tipo `object` al código nativo.</span><span class="sxs-lookup"><span data-stu-id="1b062-156">On Windows, you can marshal `object`-typed fields to native code.</span></span> <span data-ttu-id="1b062-157">Puede serializar estos campos a uno de los tres tipos:</span><span class="sxs-lookup"><span data-stu-id="1b062-157">You can marshal these fields to one of three types:</span></span>

- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

<span data-ttu-id="1b062-158">De forma predeterminada, un campo con tipo `object` se serializará a uno de tipo `IUnknown*` que encapsula el objeto.</span><span class="sxs-lookup"><span data-stu-id="1b062-158">By default, an `object`-typed field will be marshaled to an `IUnknown*` that wraps the object.</span></span>

```csharp
public struct ObjectDefault
{
    public object obj;
}
```

```cpp
struct ObjectDefault
{
    IUnknown* obj;
};
```

<span data-ttu-id="1b062-159">Si desea serializar un campo de objeto a `IDispatch*`, agregue <xref:System.Runtime.InteropServices.MarshalAsAttribute> con el valor <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1b062-159">If you want to marshal an object field to an `IDispatch*`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> value.</span></span>

```csharp
public struct ObjectDispatch
{
    [MarshalAs(UnmanagedType.IDispatch)]
    public object obj;
}
```

```cpp
struct ObjectDispatch
{
    IDispatch* obj;
};
```

<span data-ttu-id="1b062-160">Si quiere serializarlo como `VARIANT`, agregue <xref:System.Runtime.InteropServices.MarshalAsAttribute> con el valor <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1b062-160">If you want to marshal it as a `VARIANT`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> value.</span></span>

```csharp
public struct ObjectVariant
{
    [MarshalAs(UnmanagedType.Struct)]
    public object obj;
}
```

```cpp
struct ObjectVariant
{
    VARIANT obj;
};
```

<span data-ttu-id="1b062-161">En la tabla siguiente se describen los diferentes tipos en tiempo de ejecución del campo `obj` se asignan a los distintos tipos que se almacenan en `VARIANT`:</span><span class="sxs-lookup"><span data-stu-id="1b062-161">The following table describes how different runtime types of the `obj` field map to the various types stored in a `VARIANT`:</span></span>

| <span data-ttu-id="1b062-162">Tipo de .NET</span><span class="sxs-lookup"><span data-stu-id="1b062-162">.NET Type</span></span> | <span data-ttu-id="1b062-163">Tipo de VARIANTE</span><span class="sxs-lookup"><span data-stu-id="1b062-163">VARIANT Type</span></span> | | <span data-ttu-id="1b062-164">Tipo de .NET</span><span class="sxs-lookup"><span data-stu-id="1b062-164">.NET Type</span></span> | <span data-ttu-id="1b062-165">Tipo de VARIANTE</span><span class="sxs-lookup"><span data-stu-id="1b062-165">VARIANT Type</span></span> |
|------------|--------------|-|----------|--------------|
|  `byte`  | `VT_UI1` |     | `System.Runtime.InteropServices.BStrWrapper` | `VT_BSTR` |
| `sbyte`  | `VT_I1`  |     | `object`  | `VT_DISPATCH` |
| `short`  | `VT_I2`  |     | `System.Runtime.InteropServices.UnknownWrapper` | `VT_UNKNOWN` |
| `ushort` | `VT_UI2` |     | `System.Runtime.InteropServices.DispatchWrapper` | `VT_DISPATCH` |
| `int`    | `VT_I4`  |     | `System.Reflection.Missing` | `VT_ERROR` |
| `uint`   | `VT_UI4` |     | `(object)null` | `VT_EMPTY` |
| `long`   | `VT_I8`  |     | `bool` | `VT_BOOL` |
| `ulong`  | `VT_UI8` |     | `System.DateTime` | `VT_DATE` |
| `float`  | `VT_R4`  |     | `decimal` | `VT_DECIMAL` |
| `double` | `VT_R8`  |     | `System.Runtime.InteropServices.CurrencyWrapper` | `VT_CURRENCY` |
| `char`   | `VT_UI2` |     | `System.DBNull` | `VT_NULL` |
| `string` | `VT_BSTR`|

---
title: Cómo buscar cadenas (Guía de C#)
description: Obtenga información sobre dos estrategias para buscar texto en cadenas en C#. Los métodos de clase string buscan un texto concreto. Las expresiones regulares buscan patrones en el texto.
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: b6a2ab25efa64b2bbf33ea234dba07cdf9582e66
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465135"
---
# <a name="how-to-search-strings"></a>Cómo buscar cadenas

Puede usar dos estrategias principales para buscar texto en cadenas. Los métodos de la clase <xref:System.String> buscan un texto concreto. Las expresiones regulares buscan patrones en el texto.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

El tipo [string](../language-reference/builtin-types/reference-types.md#the-string-type), que es un alias de la clase <xref:System.String?displayProperty=nameWithType>, proporciona una serie de métodos útiles para buscar el contenido de una cadena. Entre ellos se encuentran <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A>, <xref:System.String.IndexOf%2A> y <xref:System.String.LastIndexOf%2A>. La clase <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> proporciona un vocabulario completo para buscar patrones en el texto. En este artículo, aprenderá estas técnicas y a elegir el mejor método para sus necesidades.

## <a name="does-a-string-contain-text"></a>¿Una cadena contiene texto?

Los métodos <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> y <xref:System.String.EndsWith%2A?displayProperty=nameWithType> buscan texto concreto en una cadena. En el ejemplo siguiente, se muestra cada uno de estos métodos y una variación que usa una búsqueda que no distingue mayúsculas de minúsculas:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet1":::

En el ejemplo anterior, se muestra un aspecto importante del uso de estos métodos. De manera predeterminada, las búsquedas **distinguen mayúsculas de minúsculas**. El valor de enumeración <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> se usa para especificar que se trata de una búsqueda que no distingue mayúsculas de minúsculas.

## <a name="where-does-the-sought-text-occur-in-a-string"></a>¿Dónde se encuentra el texto buscado en una cadena?

Los métodos <xref:System.String.IndexOf%2A> y <xref:System.String.LastIndexOf%2A> también buscan texto en cadenas. Estos métodos devuelven la ubicación del texto que se busca. Si no se encuentra el texto, devuelven `-1`. En el ejemplo siguiente, se muestra una búsqueda de la primera y última aparición de la palabra "methods" y muestra el texto que hay en medio.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet2":::

## <a name="finding-specific-text-using-regular-expressions"></a>Buscar texto concreto mediante expresiones regulares

La clase <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> se puede usar para buscar cadenas. Estas búsquedas pueden abarcar una complejidad que va desde patrones de texto simples hasta otros complejos.

En el ejemplo de código siguiente, se busca la palabra "the" o "their" en una oración, sin distinción entre mayúsculas y minúsculas. El método estático <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> realiza la búsqueda. Se proporciona la cadena de búsqueda y un patrón de búsqueda. En este caso, un tercer argumento especifica que la búsqueda no distingue mayúsculas de minúsculas. Para obtener más información, vea <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.

El patrón de búsqueda describe el texto que se busca. En la tabla siguiente, se describe cada elemento del patrón de búsqueda. (En la tabla siguiente se usa un único símbolo `\`, que en una cadena de C# debe escribirse como `\\`).

| Modelo  | Significado                          |
|----------|----------------------------------|
| `the`    | busca coincidencias con el texto "the"             |
| `(eir)?` | busca coincidencias con 0 o 1 apariciones de "eir" |
| `\s`     | busca coincidencias con un carácter de espacio en blanco    |

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet3":::

> [!TIP]
> Los métodos `string` suelen ser mejores opciones cuando se busca una cadena exacta. Las expresiones regulares son más adecuadas cuando se busca algún patrón en una cadena de origen.

## <a name="does-a-string-follow-a-pattern"></a>¿Una cadena sigue un patrón?

El código siguiente usa expresiones regulares para validar el formato de cada cadena de una matriz. La validación requiere que cada cadena tenga la forma de un número de teléfono en el que tres grupos de dígitos se separan por guiones. Los dos primeros grupos contienen tres dígitos y el tercero, cuatro. El patrón de búsqueda usa la expresión regular `^\\d{3}-\\d{3}-\\d{4}$`. Para obtener más información, consulte [Lenguaje de expresiones regulares: Referencia rápida](../../standard/base-types/regular-expression-language-quick-reference.md).

| Modelo | Significado                             |
|---------|-------------------------------------|
| `^`     | busca coincidencias con el principio de la cadena |
| `\d{3}` | busca coincidencias con exactamente 3 caracteres de dígitos  |
| `-`     | busca coincidencias con el carácter “-”           |
| `\d{3}` | busca coincidencias con exactamente 3 caracteres de dígitos  |
| `-`     | busca coincidencias con el carácter “-”           |
| `\d{4}` | busca coincidencias con exactamente 4 caracteres de dígitos  |
| `$`     | busca coincidencias con el final de la cadena       |

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet4":::

Este patrón de búsqueda sencillo coincide con muchas cadenas válidas. Las expresiones regulares son mejores para buscar o validar con respecto a un patrón, en lugar de una cadena de texto sencilla.

## <a name="see-also"></a>Vea también

- [Guía de programación de C#](../programming-guide/index.md)
- [Cadenas](../programming-guide/strings/index.md)
- [LINQ y cadenas](../programming-guide/concepts/linq/linq-and-strings.md)
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [Expresiones regulares de .NET](../../standard/base-types/regular-expressions.md)
- [Lenguaje de expresiones regulares: referencia rápida](../../standard/base-types/regular-expression-language-quick-reference.md)
- [Procedimientos recomendados para el uso de cadenas en .NET](../../standard/base-types/best-practices-strings.md)

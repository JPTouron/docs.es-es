---
title: 'Parámetros de tipos genéricos: Guía de programación de C#'
description: Aprenda sobre la definición de tipo genérico en C#, donde un parámetro de tipo es un marcador de posición para un tipo que un cliente especifica para una instancia del tipo genérico.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: dc37029378ac1e9ec194d95b561787761d69a9fd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299258"
---
# <a name="generic-type-parameters-c-programming-guide"></a>Parámetros de tipos genéricos (Guía de programación de C#)

En un tipo genérico o en una definición de método, un parámetro de tipo es un marcador de posición para un tipo específico que un cliente especifica cuando crean instancias de una variable del tipo genérico. Una clase genérica, como `GenericList<T>` que se muestra en [Introducción a los genéricos](./index.md), no puede usarse como está porque no es realmente un tipo; es más parecida a un plano para un tipo. Para usar `GenericList<T>`, el código cliente debe declarar y crear instancias de un tipo construido especificando un argumento de tipo dentro de corchetes angulares. El argumento de tipo de esta clase determinada puede ser cualquier tipo reconocido por el compilador. Puede crearse cualquier número de instancias de tipo construidas, usando cada una un argumento de tipo diferente, de la manera siguiente:  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
En cada una de estas instancias de `GenericList<T>`, cada aparición de `T` en la clase se sustituye en tiempo de ejecución con el argumento de tipo. Mediante esta sustitución, hemos creado tres objetos eficaces y con seguridad de tipos independientes con una definición de clase única. Para obtener más información sobre cómo se realiza esta sustitución mediante CLR, vea [Genéricos en tiempo de ejecución](./generics-in-the-run-time.md).  
  
## <a name="type-parameter-naming-guidelines"></a>Instrucciones de nomenclatura de los parámetros de tipo  
  
- **Asigne** nombres descriptivos a los parámetros de tipo genérico, a no ser que un nombre de una sola letra sea completamente claro y un nombre descriptivo no agregue ningún valor.  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- **Considere** el uso de T como el nombre del parámetro de tipo para los tipos con un parámetro de tipo de una sola letra.  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- **Establezca** el prefijo "T" a los nombres de parámetro de tipo descriptivos.  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- **Considere** la posibilidad de indicar restricciones que se encuentran en un parámetro de tipo en el nombre del parámetro. Por ejemplo, un parámetro restringido a `ISession` puede llamarse `TSession`.

La regla de análisis de código [CA1715](/visualstudio/code-quality/ca1715) puede usarse para asegurarse de que los parámetros de tipo se denominan apropiadamente.
  
## <a name="see-also"></a>Consulte también

- <xref:System.Collections.Generic>
- [Guía de programación de C#](../index.md)
- [Genéricos](./index.md)
- [Diferencias entre plantillas de C++ y tipos genéricos de C#](./differences-between-cpp-templates-and-csharp-generics.md)

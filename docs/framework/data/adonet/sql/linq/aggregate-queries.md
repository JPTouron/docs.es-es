---
title: Consultas de agregado
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: 2085808d631d1d9f97573c557e9e66e07113df52
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554226"
---
# <a name="aggregate-queries"></a>Consultas de agregado
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] admite los operadores de agregado `Average`, `Count`, `Max`, `Min` y `Sum`. Tener en cuenta las características siguientes de los operadores de agregado en [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:  
  
- Las consultas de funciones agregadas se ejecutan inmediatamente.  
  
     Para obtener más información, vea [Introducción a las consultas LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
- Las consultas de funciones agregadas normalmente devuelven un número en lugar de una colección.  
  
     Para obtener más información, vea [operaciones de agregación](/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).  
  
- No se puede llamar a funciones de agregado en tipos anónimos.  
  
 Los ejemplos de los temas siguientes se derivan de la base de datos de ejemplo Northwind. Para obtener más información, consulte [Descargar bases de datos de ejemplo](downloading-sample-databases.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Devolver el valor medio de una secuencia numérica](return-the-average-value-from-a-numeric-sequence.md)  
 Muestra cómo utilizar el operador <xref:System.Linq.Enumerable.Average%2A>.  
  
 [Contar el número de elementos de una secuencia](count-the-number-of-elements-in-a-sequence.md)  
 Muestra cómo utilizar el operador <xref:System.Linq.Enumerable.Count%2A>.  
  
 [Buscar el valor máximo de una secuencia numérica](find-the-maximum-value-in-a-numeric-sequence.md)  
 Muestra cómo utilizar el operador <xref:System.Linq.Enumerable.Max%2A>.  
  
 [Buscar el valor mínimo de una secuencia numérica](find-the-minimum-value-in-a-numeric-sequence.md)  
 Muestra cómo utilizar el operador <xref:System.Linq.Enumerable.Min%2A>.  
  
 [Calcular la suma de valores de una secuencia numérica](compute-the-sum-of-values-in-a-numeric-sequence.md)  
 Muestra cómo utilizar el operador <xref:System.Linq.Enumerable.Sum%2A>.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Ejemplos de consultas](query-examples.md)  
 Proporciona vínculos a consultas [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] en Visual Basic y C#.  
  
 [Conceptos sobre consultas](query-concepts.md)  
 Proporciona vínculos a temas que explican los conceptos para diseñar consultas LINQ en [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
 [Introducción a las consultas LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 Explica cómo funcionan las consultas en LINQ.

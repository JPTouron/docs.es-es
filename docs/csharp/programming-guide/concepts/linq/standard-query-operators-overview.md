---
title: Información general sobre operadores de consulta estándar (C#)
description: Los operadores de consulta estándar de LINQ ofrecen funcionalidades de consulta, como filtrado, proyección, agregación y ordenación en C#.
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 8a399f52881e10f8d94263843b5992101f96a5ea
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302326"
---
# <a name="standard-query-operators-overview-c"></a>Información general sobre operadores de consulta estándar (C#)
Los *operadores de consulta estándar* son los métodos que constituyen el modelo LINQ. La mayoría de estos métodos funciona en secuencias; donde una secuencia es un objeto cuyo tipo implementa la interfaz <xref:System.Collections.Generic.IEnumerable%601> o la interfaz <xref:System.Linq.IQueryable%601>. Los operadores de consulta estándar ofrecen funcionalidades de consulta, como las funciones de filtrado, proyección, agregación y ordenación, entre otras.  
  
 Hay dos conjuntos de operadores de consulta estándar de LINQ: uno que actúa sobre objetos de tipo <xref:System.Collections.Generic.IEnumerable%601> y otro sobre objetos de tipo <xref:System.Linq.IQueryable%601>. Los métodos que forman cada conjunto son miembros estáticos de las clases <xref:System.Linq.Enumerable> y <xref:System.Linq.Queryable>, respectivamente. Se definen como *métodos de extensión* del tipo en el que actúan. Se puede llamar a los métodos de extensión mediante sintaxis de método estático o sintaxis de método de instancia.  
  
 Además, varios métodos de operador de consulta estándar funcionan en tipos distintos de los que se basan en <xref:System.Collections.Generic.IEnumerable%601> o <xref:System.Linq.IQueryable%601>. El tipo <xref:System.Linq.Enumerable> define dos métodos que funcionan en objetos de tipo <xref:System.Collections.IEnumerable>. Estos métodos, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> y <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, le permiten habilitar una colección no genérica o no parametrizada para consultarse en el patrón LINQ. Para ello, se crea una colección de objetos fuertemente tipados. La clase <xref:System.Linq.Queryable> define dos métodos similares, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> y <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, que funcionan en objetos de tipo <xref:System.Linq.Queryable>.  
  
 Los operadores de consulta estándar difieren en sus intervalos de ejecución, dependiendo de que devuelvan un valor singleton o una secuencia de valores. Esos métodos que devuelven un valor singleton (por ejemplo, <xref:System.Linq.Enumerable.Average%2A> y <xref:System.Linq.Enumerable.Sum%2A>) se ejecutan inmediatamente. Los métodos que devuelven una secuencia aplazan la ejecución de la consulta y devuelven un objeto enumerable.  
  
 En el caso de los métodos que actúan en colecciones en memoria, es decir, los métodos que extienden <xref:System.Collections.Generic.IEnumerable%601>, el objeto enumerable devuelto captura los argumentos que se han pasado al método. Cuando se enumera ese objeto, se emplea la lógica del operador de consulta y se devuelven los resultados de la consulta.  
  
 En cambio, los métodos que extienden <xref:System.Linq.IQueryable%601> no implementan ningún comportamiento de realización de consultas. Compilan un árbol de expresión que representa la consulta que se va a realizar. El procesamiento de consultas se controla mediante el objeto <xref:System.Linq.IQueryable%601> de origen.  
  
 Las llamadas a métodos de consulta se pueden encadenar juntas en una consulta, lo que permite que las consultas se conviertan en complejas de forma arbitraria.  
  
 En el ejemplo de código siguiente se muestra el uso de los operadores de consulta estándar para obtener información sobre una secuencia.  
  
```csharp  
string sentence = "the quick brown fox jumps over the lazy dog";  
// Split the string into individual words to create a collection.  
string[] words = sentence.Split(' ');  
  
// Using query expression syntax.  
var query = from word in words  
            group word.ToUpper() by word.Length into gr  
            orderby gr.Key  
            select new { Length = gr.Key, Words = gr };  
  
// Using method-based query syntax.  
var query2 = words.  
    GroupBy(w => w.Length, w => w.ToUpper()).  
    Select(g => new { Length = g.Key, Words = g }).  
    OrderBy(o => o.Length);  
  
foreach (var obj in query)  
{  
    Console.WriteLine("Words of length {0}:", obj.Length);  
    foreach (string word in obj.Words)  
        Console.WriteLine(word);  
}  
  
// This code example produces the following output:  
//  
// Words of length 3:  
// THE  
// FOX  
// THE  
// DOG  
// Words of length 4:  
// OVER  
// LAZY  
// Words of length 5:  
// QUICK  
// BROWN  
// JUMPS
```  
  
## <a name="query-expression-syntax"></a>Sintaxis de expresiones de consulta  
 Algunos de los operadores de consulta estándar que se usan con más frecuencia tienen una sintaxis especial de palabras clave dedicadas de lenguaje C# y Visual Basic para que se puedan invocar como parte de una *expresión* *de consulta*. Para obtener más información sobre los operadores de consulta estándar que incluyen palabras clave dedicadas y sus sintaxis correspondientes, vea [Sintaxis de las expresiones de consulta para operadores de consulta estándar (C#)](./query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Extender los operadores de consulta estándar  
 Puede aumentar el conjunto de operadores de consulta estándar creando métodos específicos de dominio que sean adecuados para su tecnología o dominio de destino. También puede reemplazar los operadores de consulta estándar con sus propias implementaciones que proporcionen otros servicios tales como evaluación remota, traducción de consultas y optimización. Vea <xref:System.Linq.Enumerable.AsEnumerable%2A> para obtener un ejemplo.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 Los vínculos siguientes llevan a artículos que ofrecen información adicional sobre los distintos operadores de consulta estándar según la funcionalidad.  
  
 [Ordenación de datos [C#]](./sorting-data.md)  
  
 [Operaciones set [C#]](./set-operations.md)  
  
 [Filtrado de datos [C#]](./filtering-data.md)  
  
 [Operaciones cuantificadoras [C#]](./quantifier-operations.md)  
  
 [Operaciones de proyección [C#]](./projection-operations.md)  
  
 [Realizar particiones de datos [C#]](./partitioning-data.md)  
  
 [Operaciones de combinación [C#]](./join-operations.md)  
  
 [Agrupar datos [C#]](./grouping-data.md)  
  
 [Operaciones de generación [C#]](./generation-operations.md)  
  
 [Operaciones de igualdad [C#]](./equality-operations.md)  
  
 [Operaciones de elementos [C#]](./element-operations.md)  
  
 [Convertir tipos de datos [C#]](./converting-data-types.md)  
  
 [Operaciones de concatenación [C#]](./concatenation-operations.md)  
  
 [Operaciones de agregación [C#]](./aggregation-operations.md)  
  
## <a name="see-also"></a>Vea también

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Introducción a las consultas LINQ (C#)](./introduction-to-linq-queries.md)
- [Sintaxis de las expresiones de consulta para operadores de consulta estándar (C#)](./query-expression-syntax-for-standard-query-operators.md)
- [Clasificación de operadores de consulta estándar por modo de ejecución (C#)](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [Métodos de extensión](../../classes-and-structs/extension-methods.md)

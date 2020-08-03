---
title: Procedimiento para rellenar colecciones de objetos de varios orígenes (LINQ) (C#)
description: Obtenga información sobre cómo combinar datos de orígenes diferentes en una secuencia de tipos nuevos mediante LINQ en C#. En estos ejemplos se usan tipos anónimos y con nombre.
ms.date: 06/12/2018
ms.assetid: 8ad7d480-b46c-4ccc-8c57-76f2d04ccc6d
ms.openlocfilehash: 9dc9f98ae09e0fe3437b5d2ccab32b3dbcd93714
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104722"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-c"></a>Procedimiento para rellenar colecciones de objetos de varios orígenes (LINQ) (C#)

En este ejemplo se muestra cómo combinar datos de orígenes diferentes en una secuencia de tipos nuevos.

> [!NOTE]
> No intente unir datos en memoria o datos del sistema de archivos con datos que todavía están en una base de datos. Dichas combinaciones entre dominios pueden producir resultados indefinidos porque hay diferentes maneras de definir las operaciones de combinación para las consultas de base de datos y otros tipos de orígenes. Además, existe el riesgo de que esta operación produzca una excepción de memoria insuficiente si la cantidad de datos existente en la base de datos es considerable. Para combinar datos de una base de datos con datos en memoria, primero debe llamar a `ToList` o a `ToArray` en la base de datos de consulta y, luego, debe efectuar la combinación en la colección devuelta.

## <a name="to-create-the-data-file"></a>Para crear el archivo de datos

Copie los archivos names.csv y scores.csv en la carpeta del proyecto, como se describe en [Procedimiento para combinar contenido de archivos no similares (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar un tipo `Student` con nombre para almacenar los datos combinados de dos colecciones de cadenas en memoria que simulan datos de hoja de cálculo en formato .csv. La primera colección de cadenas representa los nombres y los identificadores de los estudiantes, mientras que la segunda colección representa el identificador de los estudiantes (en la primera columna) y cuatro notas de exámenes. El identificador se usa como clave externa.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

class Student
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public int ID { get; set; }
    public List<int> ExamScores { get; set; }
}

class PopulateCollection
{
    static void Main()
    {
        // These data files are defined in How to join content from
        // dissimilar files (LINQ).

        // Each line of names.csv consists of a last name, a first name, and an
        // ID number, separated by commas. For example, Omelchenko,Svetlana,111
        string[] names = System.IO.File.ReadAllLines(@"../../../names.csv");

        // Each line of scores.csv consists of an ID number and four test
        // scores, separated by commas. For example, 111, 97, 92, 81, 60
        string[] scores = System.IO.File.ReadAllLines(@"../../../scores.csv");

        // Merge the data sources using a named type.
        // var could be used instead of an explicit type. Note the dynamic
        // creation of a list of ints for the ExamScores member. The first item
        // is skipped in the split string because it is the student ID,
        // not an exam score.
        IEnumerable<Student> queryNamesScores =
            from nameLine in names
            let splitName = nameLine.Split(',')
            from scoreLine in scores
            let splitScoreLine = scoreLine.Split(',')
            where Convert.ToInt32(splitName[2]) == Convert.ToInt32(splitScoreLine[0])
            select new Student()
            {
                FirstName = splitName[0],
                LastName = splitName[1],
                ID = Convert.ToInt32(splitName[2]),
                ExamScores = (from scoreAsText in splitScoreLine.Skip(1)
                              select Convert.ToInt32(scoreAsText)).
                              ToList()
            };

        // Optional. Store the newly created student objects in memory
        // for faster access in future queries. This could be useful with
        // very large data files.
        List<Student> students = queryNamesScores.ToList();

        // Display each student's name and exam score average.
        foreach (var student in students)
        {
            Console.WriteLine("The average score of {0} {1} is {2}.",
                student.FirstName, student.LastName,
                student.ExamScores.Average());
        }

        //Keep console window open in debug mode
        Console.WriteLine("Press any key to exit.");
        Console.ReadKey();
    }
}
/* Output:
    The average score of Omelchenko Svetlana is 82.5.
    The average score of O'Donnell Claire is 72.25.
    The average score of Mortensen Sven is 84.5.
    The average score of Garcia Cesar is 88.25.
    The average score of Garcia Debra is 67.
    The average score of Fakhouri Fadi is 92.25.
    The average score of Feng Hanying is 88.
    The average score of Garcia Hugo is 85.75.
    The average score of Tucker Lance is 81.75.
    The average score of Adams Terry is 85.25.
    The average score of Zabokritski Eugene is 83.
    The average score of Tucker Michael is 92.
 */
```

En la cláusula [select](../../../language-reference/keywords/select-clause.md) se usa un inicializador de objeto para crear una instancia de cada objeto `Student` nuevo usando los datos de los dos orígenes.

Si no tiene que almacenar los resultados de una consulta, los tipos anónimos pueden ser más convenientes que los tipos con nombre. Los tipos con nombre son necesarios si pasa los resultados de la consulta fuera del método en el que se ejecuta la consulta. En el ejemplo siguiente se ejecuta la misma tarea que en el ejemplo anterior, con la diferencia de que se usan tipos anónimos en lugar de tipos con nombre:

```csharp
// Merge the data sources by using an anonymous type.
// Note the dynamic creation of a list of ints for the
// ExamScores member. We skip 1 because the first string
// in the array is the student ID, not an exam score.
var queryNamesScores2 =
    from nameLine in names
    let splitName = nameLine.Split(',')
    from scoreLine in scores
    let splitScoreLine = scoreLine.Split(',')
    where Convert.ToInt32(splitName[2]) == Convert.ToInt32(splitScoreLine[0])
    select new
    {
        First = splitName[0],
        Last = splitName[1],
        ExamScores = (from scoreAsText in splitScoreLine.Skip(1)
                      select Convert.ToInt32(scoreAsText))
                      .ToList()
    };

// Display each student's name and exam score average.
foreach (var student in queryNamesScores2)
{
    Console.WriteLine("The average score of {0} {1} is {2}.",
        student.First, student.Last, student.ExamScores.Average());
}
```

## <a name="see-also"></a>Consulte también

- [LINQ y cadenas (C#)](./linq-and-strings.md)
- [Inicializadores de objeto y colección](../../classes-and-structs/object-and-collection-initializers.md)
- [Tipos anónimos](../../classes-and-structs/anonymous-types.md)

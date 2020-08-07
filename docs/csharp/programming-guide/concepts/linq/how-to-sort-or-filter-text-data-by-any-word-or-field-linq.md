---
title: Procedimiento para ordenar o filtrar datos de texto por palabra o campo (LINQ) (C#)
description: Aprenda a ordenar o filtrar datos de texto por cualquier palabra o campo. Vea un ejemplo para ordenar líneas de texto estructurado por cualquier campo de la línea.
ms.date: 07/20/2015
ms.assetid: 7c04d42f-4a78-42c8-9ec8-57ef18fe13a9
ms.openlocfilehash: f27ce44f4b0b05bc9094b7e108af8f65170bb58a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301325"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a><span data-ttu-id="a6091-104">Procedimiento para ordenar o filtrar datos de texto por palabra o campo (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a6091-104">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>
<span data-ttu-id="a6091-105">En el ejemplo siguiente se muestra cómo ordenar líneas de texto estructurado, como valores separados por comas, por cualquier campo de la línea.</span><span class="sxs-lookup"><span data-stu-id="a6091-105">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="a6091-106">El campo se puede especificar dinámicamente en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="a6091-106">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="a6091-107">Supongamos que los campos de scores.csv representan el número de identificación de un alumno, seguido de una serie de cuatro calificaciones.</span><span class="sxs-lookup"><span data-stu-id="a6091-107">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="a6091-108">Para crear un archivo que contenga datos</span><span class="sxs-lookup"><span data-stu-id="a6091-108">To create a file that contains data</span></span>  
  
1. <span data-ttu-id="a6091-109">Copie los datos de scores.csv del tema [Procedimiento para combinar contenido de archivos no similares (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md).</span><span class="sxs-lookup"><span data-stu-id="a6091-109">Copy the scores.csv data from the topic [How to join content from dissimilar files (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6091-110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a6091-110">Example</span></span>  
  
```csharp  
public class SortLines  
{  
    static void Main()  
    {  
        // Create an IEnumerable data source  
        string[] scores = System.IO.File.ReadAllLines(@"../../../scores.csv");  
  
        // Change this to any value from 0 to 4.  
        int sortField = 1;  
  
        Console.WriteLine("Sorted highest to lowest by field [{0}]:", sortField);  
  
        // Demonstrates how to return query from a method.  
        // The query is executed here.  
        foreach (string str in RunQuery(scores, sortField))  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Returns the query variable, not query results!  
    static IEnumerable<string> RunQuery(IEnumerable<string> source, int num)  
    {  
        // Split the string and sort on field[num]  
        var scoreQuery = from line in source  
                         let fields = line.Split(',')  
                         orderby fields[num] descending  
                         select line;  
  
        return scoreQuery;  
    }  
}  
/* Output (if sortField == 1):  
   Sorted highest to lowest by field [1]:  
    116, 99, 86, 90, 94  
    120, 99, 82, 81, 79  
    111, 97, 92, 81, 60  
    114, 97, 89, 85, 82  
    121, 96, 85, 91, 60  
    122, 94, 92, 91, 91  
    117, 93, 92, 80, 87  
    118, 92, 90, 83, 78  
    113, 88, 94, 65, 91  
    112, 75, 84, 91, 39  
    119, 68, 79, 88, 92  
    115, 35, 72, 91, 70  
 */  
```  
  
 <span data-ttu-id="a6091-111">En este ejemplo también se muestra cómo devolver una variable de consulta desde un método.</span><span class="sxs-lookup"><span data-stu-id="a6091-111">This example also demonstrates how to return a query variable from a method.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a6091-112">Compilar el código</span><span class="sxs-lookup"><span data-stu-id="a6091-112">Compiling the Code</span></span>  

<span data-ttu-id="a6091-113">Cree un proyecto de aplicación de consola de C# con directivas `using` para los espacios de nombres System.Linq y System.IO.</span><span class="sxs-lookup"><span data-stu-id="a6091-113">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a6091-114">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a6091-114">See also</span></span>

- [<span data-ttu-id="a6091-115">LINQ y cadenas (C#)</span><span class="sxs-lookup"><span data-stu-id="a6091-115">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)

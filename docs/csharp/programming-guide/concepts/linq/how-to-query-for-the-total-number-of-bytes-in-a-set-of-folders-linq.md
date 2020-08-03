---
title: Procedimiento para buscar el número total de bytes de un conjunto de carpetas (LINQ) (C#)
description: Aprenda a usar LINQ en C# para buscar el número total de bytes usados por todos los archivos de una carpeta especificada y sus subcarpetas.
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: 964d92a55599d60388f7add937c7f7338f697817
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104288"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a><span data-ttu-id="70ef2-103">Procedimiento para buscar el número total de bytes de un conjunto de carpetas (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="70ef2-103">How to query for the total number of bytes in a set of folders (LINQ) (C#)</span></span>
<span data-ttu-id="70ef2-104">En este ejemplo se muestra cómo recuperar el número total de bytes usados por todos los archivos en una carpeta especificada y en todas sus subcarpetas.</span><span class="sxs-lookup"><span data-stu-id="70ef2-104">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70ef2-105">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="70ef2-105">Example</span></span>  
 <span data-ttu-id="70ef2-106">El método <xref:System.Linq.Enumerable.Sum%2A> agrega los valores de todos los elementos seleccionados en la cláusula `select`.</span><span class="sxs-lookup"><span data-stu-id="70ef2-106">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="70ef2-107">Puede modificar fácilmente esta consulta para recuperar el archivo más grande y más pequeño en el árbol de directorio especificado llamando al método <xref:System.Linq.Enumerable.Min%2A> o <xref:System.Linq.Enumerable.Max%2A> en lugar de <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="70ef2-107">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
```csharp  
class QuerySize  
{  
    public static void Main()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\VC#";  
  
        // Take a snapshot of the file system.  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<string> fileList = System.IO.Directory.GetFiles(startFolder, "*.*", System.IO.SearchOption.AllDirectories);  
  
        var fileQuery = from file in fileList  
                        select GetFileLength(file);  
  
        // Cache the results to avoid multiple trips to the file system.  
        long[] fileLengths = fileQuery.ToArray();  
  
        // Return the size of the largest file  
        long largestFile = fileLengths.Max();  
  
        // Return the total number of bytes in all the files under the specified folder.  
        long totalBytes = fileLengths.Sum();  
  
        Console.WriteLine("There are {0} bytes in {1} files under {2}",  
            totalBytes, fileList.Count(), startFolder);  
        Console.WriteLine("The largest files is {0} bytes.", largestFile);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.");  
        Console.ReadKey();  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the System.IO.FileInfo.Length property.  
    static long GetFileLength(string filename)  
    {  
        long retval;  
        try  
        {  
            System.IO.FileInfo fi = new System.IO.FileInfo(filename);  
            retval = fi.Length;  
        }  
        catch (System.IO.FileNotFoundException)  
        {  
            // If a file is no longer present,  
            // just add zero bytes to the total.  
            retval = 0;  
        }  
        return retval;  
    }  
}  
```  
  
 <span data-ttu-id="70ef2-108">Si solo tiene que contar el número de bytes en un árbol de directorio especificado, puede hacerlo de forma más eficaz sin crear una consulta LINQ, ya que conlleva la sobrecarga de crear la colección de listas como un origen de datos.</span><span class="sxs-lookup"><span data-stu-id="70ef2-108">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="70ef2-109">La utilidad del enfoque de LINQ aumenta a medida que la consulta se vuelve más compleja, o cuando se tienen que ejecutar varias consultas en el mismo origen de datos.</span><span class="sxs-lookup"><span data-stu-id="70ef2-109">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="70ef2-110">La consulta llama a un método independiente para obtener la longitud del archivo.</span><span class="sxs-lookup"><span data-stu-id="70ef2-110">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="70ef2-111">Lo hace para consumir la excepción que probablemente se producirá si el archivo se ha eliminado en otro subproceso después de que se creara el objeto <xref:System.IO.FileInfo> en la llamada a `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="70ef2-111">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="70ef2-112">Aunque ya se haya creado el objeto <xref:System.IO.FileInfo>, puede producirse una excepción porque un objeto <xref:System.IO.FileInfo> intentará actualizar su propiedad <xref:System.IO.FileInfo.Length%2A> con la longitud más actual la primera vez que se tenga acceso a la propiedad.</span><span class="sxs-lookup"><span data-stu-id="70ef2-112">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="70ef2-113">Al incluir esta operación en un bloque try-catch fuera de la consulta, el código sigue la regla de evitar las operaciones en las consultas que pueden producir efectos secundarios.</span><span class="sxs-lookup"><span data-stu-id="70ef2-113">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="70ef2-114">En general, debe tener mucho cuidado al consumir excepciones para asegurarse de que no deja una aplicación en un estado desconocido.</span><span class="sxs-lookup"><span data-stu-id="70ef2-114">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="70ef2-115">Compilar el código</span><span class="sxs-lookup"><span data-stu-id="70ef2-115">Compiling the Code</span></span>  
<span data-ttu-id="70ef2-116">Cree un proyecto de aplicación de consola de C# con directivas `using` para los espacios de nombres System.Linq y System.IO.</span><span class="sxs-lookup"><span data-stu-id="70ef2-116">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="70ef2-117">Vea también</span><span class="sxs-lookup"><span data-stu-id="70ef2-117">See also</span></span>

- [<span data-ttu-id="70ef2-118">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="70ef2-118">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="70ef2-119">LINQ y directorios de archivos (C#)</span><span class="sxs-lookup"><span data-stu-id="70ef2-119">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)

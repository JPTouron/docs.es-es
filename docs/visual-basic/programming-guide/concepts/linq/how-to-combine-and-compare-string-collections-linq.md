---
title: Procedimiento para combinar y comparar colecciones de cadenas (LINQ)
ms.date: 07/20/2015
ms.assetid: 243cfafc-9eaa-4354-a9df-d329f1d39913
ms.openlocfilehash: 271ef7805cd2285fa2d8796a31257c0f31bb9a76
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374867"
---
# <a name="how-to-combine-and-compare-string-collections-linq-visual-basic"></a><span data-ttu-id="92082-102">Cómo: combinar y comparar colecciones de cadenas (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92082-102">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="92082-103">En este ejemplo se muestra cómo combinar archivos que contienen líneas de texto y después ordenar los resultados.</span><span class="sxs-lookup"><span data-stu-id="92082-103">This example shows how to merge files that contain lines of text and then sort the results.</span></span> <span data-ttu-id="92082-104">En concreto, se muestra cómo realizar una concatenación simple, una unión y una intersección en los dos conjuntos de líneas de texto.</span><span class="sxs-lookup"><span data-stu-id="92082-104">Specifically, it shows how to perform a simple concatenation, a union, and an intersection on the two sets of text lines.</span></span>

## <a name="set-up-the-project-and-the-text-files"></a><span data-ttu-id="92082-105">Configurar el proyecto y los archivos de texto</span><span class="sxs-lookup"><span data-stu-id="92082-105">Set up the project and the text files</span></span>

1. <span data-ttu-id="92082-106">Copie estos nombres en un archivo de texto denominado names1.txt y guárdelo en la carpeta del proyecto:</span><span class="sxs-lookup"><span data-stu-id="92082-106">Copy these names into a text file that is named names1.txt and save it in your project folder:</span></span>

    ```text
    Bankov, Peter
    Holm, Michael
    Garcia, Hugo
    Potra, Cristina
    Noriega, Fabricio
    Aw, Kam Foo
    Beebe, Ann
    Toyoshima, Tim
    Guy, Wey Yuan
    Garcia, Debra
    ```

2. <span data-ttu-id="92082-107">Copie estos nombres en un archivo de texto denominado names2.txt y guárdelo en la carpeta del proyecto.</span><span class="sxs-lookup"><span data-stu-id="92082-107">Copy these names into a text file that is named names2.txt and save it in your project folder.</span></span> <span data-ttu-id="92082-108">Tenga en cuenta que los dos archivos tienen algunos nombres en común.</span><span class="sxs-lookup"><span data-stu-id="92082-108">Note that the two files have some names in common.</span></span>

    ```text
    Liu, Jinghao
    Bankov, Peter
    Holm, Michael
    Garcia, Hugo
    Beebe, Ann
    Gilchrist, Beth
    Myrcha, Jacek
    Giakoumakis, Leo
    McLin, Nkenge
    El Yassir, Mehdi
    ```

## <a name="example"></a><span data-ttu-id="92082-109">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="92082-109">Example</span></span>

```vb
Class ConcatenateStrings
    Shared Sub Main()

        ' Create the IEnumerable data sources.
        Dim fileA As String() = System.IO.File.ReadAllLines("../../../names1.txt")
        Dim fileB As String() = System.IO.File.ReadAllLines("../../../names2.txt")

        ' Simple concatenation and sort.
        Dim concatQuery = fileA.Concat(fileB).OrderBy(Function(name) name)

        ' Pass the query variable to another function for execution
        OutputQueryResults(concatQuery, "Simple concatenation and sort. Duplicates are preserved:")

        ' New query. Concatenate files and remove duplicates
        Dim uniqueNamesQuery = fileA.Union(fileB).OrderBy(Function(name) name)
        OutputQueryResults(uniqueNamesQuery, "Union removes duplicate names:")

        ' New query. Find the names that occur in both files.
        Dim commonNamesQuery = fileA.Intersect(fileB)
        OutputQueryResults(commonNamesQuery, "Merge based on intersect: ")

        ' New query in three steps for better readability
        ' First filter each list separately

        Dim nameToSearch As String = "Garcia"
        Dim mergeQueryA As IEnumerable(Of String) = From name In fileA
                          Let n = name.Split(New Char() {","})
                          Where n(0) = nameToSearch
                          Select name

        Dim mergeQueryB = From name In fileB
                          Let n = name.Split(New Char() {","})
                          Where n(0) = nameToSearch
                          Select name

        ' Create a new query to concatenate and sort results. Duplicates are removed in Union.
        ' Note that none of the queries actually executed until the call to OutputQueryResults.
        Dim mergeSortQuery = mergeQueryA.Union(mergeQueryB).OrderBy(Function(str) str)

        ' Now execute mergeSortQuery
        OutputQueryResults(mergeSortQuery, "Concat based on partial name match """ & nameToSearch & """ from each list:")

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()

    End Sub

    Shared Sub OutputQueryResults(ByVal query As IEnumerable(Of String), ByVal message As String)

        Console.WriteLine(System.Environment.NewLine & message)
        For Each item As String In query
            Console.WriteLine(item)
        Next
        Console.WriteLine(query.Count & " total names in list")

    End Sub
End Class
' Output:

' Simple concatenation and sort. Duplicates are preserved:
' Aw, Kam Foo
' Bankov, Peter
' Bankov, Peter
' Beebe, Ann
' Beebe, Ann
' El Yassir, Mehdi
' Garcia, Debra
' Garcia, Hugo
' Garcia, Hugo
' Giakoumakis, Leo
' Gilchrist, Beth
' Guy, Wey Yuan
' Holm, Michael
' Holm, Michael
' Liu, Jinghao
' McLin, Nkenge
' Myrcha, Jacek
' Noriega, Fabricio
' Potra, Cristina
' Toyoshima, Tim
' 20 total names in list

' Union removes duplicate names:
' Aw, Kam Foo
' Bankov, Peter
' Beebe, Ann
' El Yassir, Mehdi
' Garcia, Debra
' Garcia, Hugo
' Giakoumakis, Leo
' Gilchrist, Beth
' Guy, Wey Yuan
' Holm, Michael
' Liu, Jinghao
' McLin, Nkenge
' Myrcha, Jacek
' Noriega, Fabricio
' Potra, Cristina
' Toyoshima, Tim
' 16 total names in list

' Merge based on intersect:
' Bankov, Peter
' Holm, Michael
' Garcia, Hugo
' Beebe, Ann
' 4 total names in list

' Concat based on partial name match "Garcia" from each list:
' Garcia, Debra
' Garcia, Hugo
' 2 total names in list
```

## <a name="compile-the-code"></a><span data-ttu-id="92082-110">Compilar el código</span><span class="sxs-lookup"><span data-stu-id="92082-110">Compile the code</span></span>

<span data-ttu-id="92082-111">Cree un proyecto de aplicación de consola de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="92082-111">Create a Visual Basic console application project.</span></span> <span data-ttu-id="92082-112">Agregue una `Imports` instrucción para el espacio de nombres System. Linq.</span><span class="sxs-lookup"><span data-stu-id="92082-112">Add an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="92082-113">Consulte también</span><span class="sxs-lookup"><span data-stu-id="92082-113">See also</span></span>

- [<span data-ttu-id="92082-114">LINQ y cadenas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92082-114">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="92082-115">LINQ y directorios de archivos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92082-115">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)

---
title: 'Procedimiento para leer un archivo de texto de línea en línea: guía de programación de C#'
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: b54d072ce9837f9b15694f2d7100817de62e9762
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241778"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a><span data-ttu-id="ed9a1-102">Procedimiento para leer un archivo de texto de línea en línea (guía de programación de C#)</span><span class="sxs-lookup"><span data-stu-id="ed9a1-102">How to read a text file one line at a time (C# Programming Guide)</span></span>
<span data-ttu-id="ed9a1-103">En este ejemplo se lee el contenido de un archivo de texto línea a línea en una cadena mediante el método `ReadLine` de la clase `StreamReader`.</span><span class="sxs-lookup"><span data-stu-id="ed9a1-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="ed9a1-104">Cada línea de texto se almacena en la cadena `line` y se muestra en la pantalla.</span><span class="sxs-lookup"><span data-stu-id="ed9a1-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed9a1-105">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ed9a1-105">Example</span></span>  
  
```csharp
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine(line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ed9a1-106">Compilar el código</span><span class="sxs-lookup"><span data-stu-id="ed9a1-106">Compiling the Code</span></span>  
 <span data-ttu-id="ed9a1-107">Copie el código y péguelo en el método `Main` de una aplicación de consola.</span><span class="sxs-lookup"><span data-stu-id="ed9a1-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="ed9a1-108">Reemplace `"c:\test.txt"` por el nombre de archivo real.</span><span class="sxs-lookup"><span data-stu-id="ed9a1-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ed9a1-109">Programación sólida</span><span class="sxs-lookup"><span data-stu-id="ed9a1-109">Robust Programming</span></span>  
 <span data-ttu-id="ed9a1-110">Las condiciones siguientes pueden provocar una excepción:</span><span class="sxs-lookup"><span data-stu-id="ed9a1-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="ed9a1-111">El archivo podría no existir.</span><span class="sxs-lookup"><span data-stu-id="ed9a1-111">The file may not exist.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="ed9a1-112">Seguridad de .NET</span><span class="sxs-lookup"><span data-stu-id="ed9a1-112">.NET Security</span></span>  
 <span data-ttu-id="ed9a1-113">No tome ninguna decisión sobre el contenido del archivo basándose en su nombre.</span><span class="sxs-lookup"><span data-stu-id="ed9a1-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="ed9a1-114">Por ejemplo, es posible que el archivo `myFile.cs` no sea un archivo de código fuente de C#.</span><span class="sxs-lookup"><span data-stu-id="ed9a1-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed9a1-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="ed9a1-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="ed9a1-116">Guía de programación de C#</span><span class="sxs-lookup"><span data-stu-id="ed9a1-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ed9a1-117">Registro y sistema de archivos (Guía de programación de C#)</span><span class="sxs-lookup"><span data-stu-id="ed9a1-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)

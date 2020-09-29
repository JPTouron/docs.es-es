---
title: 'Procedimiento Crear archivos o carpetas: Guía de programación de C#'
description: Aprenda a crear archivos o carpetas mediante programación. Puede crear una carpeta, una subcarpeta, un archivo en la subcarpeta y escribir datos en ese archivo.
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: 4d60b8c6c0f9d4ea66125374327f5e1ad2098694
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167449"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="19cbf-104">Procedimiento Crear archivos o carpetas (Guía de programación de C#)</span><span class="sxs-lookup"><span data-stu-id="19cbf-104">How to create a file or folder (C# Programming Guide)</span></span>

<span data-ttu-id="19cbf-105">Puede crear una carpeta en el equipo mediante programación, crear una subcarpeta, crear un archivo en la subcarpeta y escribir datos en el archivo.</span><span class="sxs-lookup"><span data-stu-id="19cbf-105">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19cbf-106">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="19cbf-106">Example</span></span>  

 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 <span data-ttu-id="19cbf-107">Si la carpeta ya existe, <xref:System.IO.Directory.CreateDirectory%2A> no efectúa ninguna acción y no se devuelve ninguna excepción.</span><span class="sxs-lookup"><span data-stu-id="19cbf-107">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="19cbf-108">Sin embargo, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> reemplaza un archivo existente por otro nuevo.</span><span class="sxs-lookup"><span data-stu-id="19cbf-108">However, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> replaces an existing file with a new file.</span></span> <span data-ttu-id="19cbf-109">En el ejemplo se usa una instrucción `if`-`else` para evitar que se sustituya un archivo existente.</span><span class="sxs-lookup"><span data-stu-id="19cbf-109">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="19cbf-110">Al realizar los siguientes cambios en el ejemplo, puede especificar diferentes resultados en función de si ya existe un archivo con un nombre determinado.</span><span class="sxs-lookup"><span data-stu-id="19cbf-110">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="19cbf-111">Si no existe ese archivo, el código crea uno.</span><span class="sxs-lookup"><span data-stu-id="19cbf-111">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="19cbf-112">Si ese archivo ya existe, el código anexa datos a ese archivo.</span><span class="sxs-lookup"><span data-stu-id="19cbf-112">If such a file exists, the code appends data to that file.</span></span>  
  
- <span data-ttu-id="19cbf-113">Especifique un nombre de archivo no aleatorio.</span><span class="sxs-lookup"><span data-stu-id="19cbf-113">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- <span data-ttu-id="19cbf-114">Sustituya la instrucción `if`-`else` por la instrucción `using` en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="19cbf-114">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="19cbf-115">Ejecute el ejemplo varias veces para comprobar que los datos se agreguen al archivo cada vez.</span><span class="sxs-lookup"><span data-stu-id="19cbf-115">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="19cbf-116">Para obtener más valores `FileMode` que puede probar, consulte <xref:System.IO.FileMode>.</span><span class="sxs-lookup"><span data-stu-id="19cbf-116">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="19cbf-117">Las condiciones siguientes pueden provocar una excepción:</span><span class="sxs-lookup"><span data-stu-id="19cbf-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="19cbf-118">El nombre de la carpeta tiene un formato incorrecto.</span><span class="sxs-lookup"><span data-stu-id="19cbf-118">The folder name is malformed.</span></span> <span data-ttu-id="19cbf-119">Por ejemplo, contiene caracteres no válidos o solo tiene espacios en blanco (clase <xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="19cbf-119">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="19cbf-120">Use la clase <xref:System.IO.Path> para crear nombres de ruta válidos.</span><span class="sxs-lookup"><span data-stu-id="19cbf-120">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
- <span data-ttu-id="19cbf-121">La carpeta principal de la que se va a crear es de solo lectura (clase <xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="19cbf-121">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="19cbf-122">El nombre de la carpeta es `null` (clase <xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="19cbf-122">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="19cbf-123">El nombre de la carpeta es demasiado largo (clase <xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="19cbf-123">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="19cbf-124">El nombre de la carpeta es solo un carácter de dos puntos, ":" (clase <xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="19cbf-124">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="19cbf-125">Seguridad de .NET</span><span class="sxs-lookup"><span data-stu-id="19cbf-125">.NET Security</span></span>  

 <span data-ttu-id="19cbf-126">En los casos de confiabilidad parcial, es posible que se devuelva una instancia de la clase <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="19cbf-126">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="19cbf-127">Si no tiene permiso para crear la carpeta, el ejemplo devuelve una instancia de la clase <xref:System.UnauthorizedAccessException>.</span><span class="sxs-lookup"><span data-stu-id="19cbf-127">If you don't have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19cbf-128">Vea también</span><span class="sxs-lookup"><span data-stu-id="19cbf-128">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="19cbf-129">Guía de programación de C#</span><span class="sxs-lookup"><span data-stu-id="19cbf-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="19cbf-130">Registro y sistema de archivos (Guía de programación de C#)</span><span class="sxs-lookup"><span data-stu-id="19cbf-130">File System and the Registry (C# Programming Guide)</span></span>](./index.md)

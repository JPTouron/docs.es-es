---
title: Acceso a archivos
ms.date: 07/20/2015
helpviewer_keywords:
- file access
- files [Visual Basic], input and output
- file access, Visual Basic
- files [Visual Basic], I/O
- file I/O classes
- data [Visual Basic], accessing from files
- files [Visual Basic], accessing
- file access, using components
- My.Computer.FileSystem object, accessing files
- I/O [Visual Basic]
- sequential access
ms.assetid: 231533bf-d049-4345-befa-3fb78fe6517d
ms.openlocfilehash: 3b2042862ae81a52d62374e35a456766ed47edc9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401737"
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="0e20f-102">Acceso a archivos con Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0e20f-102">File Access with Visual Basic</span></span>

<span data-ttu-id="0e20f-103">El objeto `My.Computer.FileSystem` proporciona herramientas para trabajar con archivos y carpetas.</span><span class="sxs-lookup"><span data-stu-id="0e20f-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="0e20f-104">Sus propiedades, métodos y eventos permiten crear, copiar, mover, investigar y eliminar archivos y carpetas.</span><span class="sxs-lookup"><span data-stu-id="0e20f-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="0e20f-105">`My.Computer.FileSystem` ofrece un mejor rendimiento que las funciones heredadas (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) proporcionadas por Visual Basic para la compatibilidad con versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="0e20f-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by Visual Basic for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0e20f-106">En esta sección</span><span class="sxs-lookup"><span data-stu-id="0e20f-106">In This Section</span></span>  

 [<span data-ttu-id="0e20f-107">Leer archivos</span><span class="sxs-lookup"><span data-stu-id="0e20f-107">Reading from Files</span></span>](reading-from-files.md)  
 <span data-ttu-id="0e20f-108">Enumera temas que tratan sobre el uso del objeto `My.Computer.FileSystem` para leer desde archivos</span><span class="sxs-lookup"><span data-stu-id="0e20f-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="0e20f-109">Escritura en archivos</span><span class="sxs-lookup"><span data-stu-id="0e20f-109">Writing to Files</span></span>](writing-to-files.md)  
 <span data-ttu-id="0e20f-110">Enumera temas que tratan sobre el uso del objeto `My.Computer.FileSystem` para escribir en archivos</span><span class="sxs-lookup"><span data-stu-id="0e20f-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="0e20f-111">Creación, eliminación y movimiento de archivos y directorios</span><span class="sxs-lookup"><span data-stu-id="0e20f-111">Creating, Deleting, and Moving Files and Directories</span></span>](creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="0e20f-112">Enumera temas que tratan sobre el uso del objeto `My.Computer.FileSystem` para crear, copiar, eliminar y mover archivos y carpetas.</span><span class="sxs-lookup"><span data-stu-id="0e20f-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="0e20f-113">Análisis de archivos de texto con el objeto TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="0e20f-113">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="0e20f-114">Explica cómo usar `TextFieldReader` para analizar archivos de texto como los registros.</span><span class="sxs-lookup"><span data-stu-id="0e20f-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="0e20f-115">Codificaciones de archivos</span><span class="sxs-lookup"><span data-stu-id="0e20f-115">File Encodings</span></span>](file-encodings.md)  
 <span data-ttu-id="0e20f-116">Explica codificaciones de archivos y su uso.</span><span class="sxs-lookup"><span data-stu-id="0e20f-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="0e20f-117">Tutorial: Manipular archivos y directorios en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0e20f-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="0e20f-118">Muestra cómo crear una utilidad que presenta información sobre archivos y carpetas.</span><span class="sxs-lookup"><span data-stu-id="0e20f-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="0e20f-119">Solución de problemas: Leer y escribir en archivos de texto</span><span class="sxs-lookup"><span data-stu-id="0e20f-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="0e20f-120">Enumera problemas habituales detectados al leer y escribir en archivos de texto y sugiere soluciones para cada uno.</span><span class="sxs-lookup"><span data-stu-id="0e20f-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>

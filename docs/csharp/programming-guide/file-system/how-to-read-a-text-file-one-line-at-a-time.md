---
title: 'Procedimiento para leer un archivo de texto de línea en línea: guía de programación de C#'
description: Aprenda a leer un archivo de texto línea a línea. Vea un ejemplo de código y examine los recursos adicionales disponibles.
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: 93645ef78f1ceb3cc4cf1d20ac73112e86957293
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178520"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a>Procedimiento para leer un archivo de texto de línea en línea (guía de programación de C#)

En este ejemplo se lee el contenido de un archivo de texto línea a línea en una cadena mediante el método `ReadLine` de la clase `StreamReader`. Cada línea de texto se almacena en la cadena `line` y se muestra en la pantalla.  
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="compiling-the-code"></a>Compilar el código  

 Copie el código y péguelo en el método `Main` de una aplicación de consola.  
  
 Reemplace `"c:\test.txt"` por el nombre de archivo real.  
  
## <a name="robust-programming"></a>Programación sólida  

 Las condiciones siguientes pueden provocar una excepción:  
  
- El archivo podría no existir.  
  
## <a name="net-security"></a>Seguridad de .NET  

 No tome ninguna decisión sobre el contenido del archivo basándose en su nombre. Por ejemplo, es posible que el archivo `myFile.cs` no sea un archivo de código fuente de C#.  
  
## <a name="see-also"></a>Vea también

- <xref:System.IO?displayProperty=nameWithType>
- [Guía de programación de C#](../index.md)
- [Registro y sistema de archivos (Guía de programación de C#)](./index.md)

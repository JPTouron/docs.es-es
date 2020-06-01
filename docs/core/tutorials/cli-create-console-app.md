---
title: Introducción a .NET Core con la CLI
description: Un tutorial paso a paso que muestra cómo empezar a trabajar con .NET Core en Windows, Linux o macOS con la CLI de .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: 7658f2498b87a90b3925d83628f6ea9247a2fc15
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/26/2020
ms.locfileid: "83840876"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a>Introducción a .NET Core mediante la CLI de .NET Core

En este artículo se muestra cómo empezar a desarrollar aplicaciones de .NET Core que funcionan en Windows, Linux y macOS mediante la CLI de .NET Core.

Si no está familiarizado con la CLI de .NET Core, consulte la [información general de la CLI de .NET Core](../tools/index.md).

## <a name="prerequisites"></a>Requisitos previos

- [SDK 3.1 de NET Core](https://dotnet.microsoft.com/download) o versiones posteriores.
- Un editor de texto o un editor de código de su elección.

## <a name="hello-console-app"></a>Hola, aplicación de consola

Puede [ver o descargar el código de ejemplo](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) del repositorio dotnet/samples de GitHub. Para obtener instrucciones de descarga, vea [Ejemplos y tutoriales](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Abra un símbolo del sistema y cree una carpeta denominada *Hello*. Vaya a la carpeta que ha creado y escriba lo siguiente.

```dotnetcli
dotnet new console
dotnet run
```

Veamos un tutorial rápido:

01. `dotnet new console`

    [dotnet new](../tools/dotnet-new.md) crea un archivo de proyecto *Hello.csproj* actualizado con las dependencias necesarias para compilar una aplicación de consola. Además, también crea *Program.cs*, un archivo básico que contiene el punto de entrada para la aplicación.

    *Hello.csproj*:

    [!code-xml[Hello.csproj](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Hello.csproj)]

    El archivo de proyecto especifica todo lo que es necesario para restaurar las dependencias y compilar el programa.

    - El elemento `<OutputType>` especifica que estamos creando un archivo ejecutable, es decir, una aplicación de consola.
    - El elemento `<TargetFramework>` especifica el destino de la implementación de .NET. En un escenario avanzado, con una sola operación puede especificar varios marcos de destino y compilar en todos ellos. En este tutorial, nos centraremos en compilar únicamente para .NET Core 3.1.

    *Program.cs*:

    [!code-csharp[Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Program.cs)]

    El programa se inicia mediante `using System`, lo que significa "llevar cada cosa del espacio de nombres `System` al ámbito de este archivo". El espacio de nombres `System` incluye la clase `Console`.

    Después, definimos un espacio de nombres denominado `Hello`. Puede cambiar esto por cualquier cosa que desee. Se define una clase denominada `Program` dentro del espacio de nombres, con un método `Main` que toma una matriz de cadenas llamada `args`. Esta matriz contiene la lista de argumentos que se han pasado cuando se ejecuta el programa. Esta matriz no se usa tal cual y el programa escribe simplemente el texto "¡Hola mundo!". en la consola. Después, realizaremos cambios en el código que usará este argumento.

    `dotnet new` llama a [dotnet restore](../tools/dotnet-restore.md) de forma implícita. `dotnet restore` llama a [NuGet](https://www.nuget.org/) (el administrador de paquetes de .NET) para restaurar el árbol de dependencias. NuGet analiza el archivo *Hello.csproj*, descarga las dependencias descritas en el archivo (o las toma de la memoria caché del equipo) y escribe el archivo *obj/project.assets.json*, que es necesario para compilar y ejecutar el ejemplo.

02. `dotnet run`

    [dotnet run](../tools/dotnet-run.md) llama a [dotnet build](../tools/dotnet-build.md) para garantizar que se han creado los destinos de compilación y, luego, llama a `dotnet <assembly.dll>` para ejecutar la aplicación de destino.

    ```dotnetcli
    dotnet run
    ```

    Obtendrá la siguiente salida.

    ```console
    Hello World!
    ```

    También puede ejecutar `dotnet build` para compilar el código sin ejecutar las aplicaciones de consola de compilación. El resultado es una aplicación compilada, como un archivo DLL, basada en el nombre del proyecto. En este caso, el archivo creado se llama *Hello.dll*. Esta aplicación se puede ejecutar con `dotnet bin\Debug\netcoreapp3.1\Hello.dll` en Windows (use `/` con sistemas que no son Windows).

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    Obtendrá la siguiente salida.

    ```console
    Hello World!
    ```

    Cuando se compila la aplicación, se crea un archivo ejecutable específico del sistema operativo junto con `Hello.dll`. En Windows, sería `Hello.exe`; en Linux o macOS, sería `hello`. Con el ejemplo anterior, el archivo se designa con `Hello.exe` o `Hello`. Puede ejecutar ese archivo ejecutable directamente.

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a>Modificación del programa

Cambiemos un poco el programa. Los números Fibonacci son divertidos, así que vamos a agregarlos y a usar además el argumento para saludar a la persona que ejecuta la aplicación.

01. Reemplace el contenido de su archivo *Program.cs* por el código siguiente:

    [!code-csharp[Fibonacci](~/samples/snippets/core/tutorials/cli-create-console-app/fibonacci-msbuild/csharp/Program.cs)]

02. Ejecute [dotnet build](../tools/dotnet-build.md) para compilar los cambios.

03. Para ejecutar el programa, pase un parámetro a la aplicación. Cuando use el comando `dotnet` para ejecutar una aplicación, agregue `--` al final. Todo lo que quede a la derecha de `--` se pasará como un parámetro a la aplicación. En el ejemplo siguiente, el valor `John` se pasa a la aplicación.

    ```dotnetcli
    dotnet run -- John
    ```

    Obtendrá la siguiente salida.

    ```console
    Hello John!
    Fibonacci Numbers 1-15:
    1: 0
    2: 1
    3: 1
    4: 2
    5: 3
    6: 5
    7: 8
    8: 13
    9: 21
    10: 34
    11: 55
    12: 89
    13: 144
    14: 233
    15: 377
    ```

Y listo. Puede modificar *Program.cs* como prefiera.

## <a name="working-with-multiple-files"></a>Trabajar con varios archivos

Los archivos únicos son adecuados para programas sencillos de uso único, pero, si va a crear una aplicación más compleja, probablemente llegue a tener varios archivos de código en el proyecto. Se compilará sobre el ejemplo de Fibonacci anterior mediante el almacenamiento en caché de algunos valores de Fibonacci y la adición de varias características recursivas.

01. Agregue un archivo nuevo dentro del directorio *Hello* denominado *FibonacciGenerator.cs* con el código siguiente:

    [!code-csharp[Fibonacci Generator](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/FibonacciGenerator.cs)]

02. Cambie el método `Main` en su archivo *Program.cs* para crear una instancia de la nueva clase y llamar a su método como se muestra en el ejemplo siguiente:

    [!code-csharp[New Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/Program.cs)]

03. Ejecute [dotnet build](../tools/dotnet-build.md) para compilar los cambios.

04. Ejecute su aplicación mediante la ejecución de [dotnet run](../tools/dotnet-run.md).

    ```dotnetcli
    dotnet run
    ```

    Obtendrá la siguiente salida.

    ```console
    0
    1
    1
    2
    3
    5
    8
    13
    21
    34
    55
    89
    144
    233
    377
    ```

## <a name="publish-your-app"></a>Publicar la aplicación

Cuando esté listo para distribuir la aplicación, use el comando [dotnet publish](../tools/dotnet-publish.md)_para generar la carpeta_publish _en \\bin\\debug\\netcoreapp3.1\\publish_`/` (para sistemas que no son Windows). Puede distribuir el contenido de la carpeta _publish_ en otras plataformas siempre y cuando ya haya instalado el entorno de ejecución de dotnet.

```dotnetcli
dotnet publish
```

Verá un resultado similar al siguiente.

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

Puede que la salida anterior no sea igual por la carpeta y el sistema operativo actuales, pero el resultado será parecido.

Puede ejecutar la aplicación publicada con el comando [dotnet](../tools/dotnet.md):

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

Obtendrá la siguiente salida.

```console
0
1
1
2
3
5
8
13
21
34
55
89
144
233
377
```

Como se ha mencionado al comienzo de este artículo, se ha creado un archivo ejecutable específico del sistema operativo junto con `Hello.dll`. En Windows, sería `Hello.exe`; en Linux o macOS, sería `hello`. Con el ejemplo anterior, el archivo se designa con `Hello.exe` o `Hello`. Puede ejecutar este archivo ejecutable publicado directamente.

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

0
1
1
2
3
5
8
13
21
34
55
89
144
233
377
```

## <a name="conclusion"></a>Conclusión

Y listo. Ahora, puede empezar a usar los conceptos básicos que ha aprendido aquí para crear sus propios programas.

## <a name="see-also"></a>Vea también

- [Organización y prueba de proyectos con la CLI de .NET Core](testing-with-cli.md)
- [Publicación de aplicaciones .NET Core con la CLI de .NET Core](../deploying/deploy-with-cli.md)
- [Implementación de aplicaciones .NET Core](../deploying/index.md)

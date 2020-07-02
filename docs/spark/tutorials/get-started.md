---
title: Introducción a .NET para Apache Spark
description: Descubra cómo ejecutar una aplicación .NET para Apache Spark con .NET Core en Windows, MacOS y Ubuntu.
ms.date: 06/25/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: be150bcef0029f69136e21c35791c863220af244
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617657"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Tutorial: Introducción a .NET para Apache Spark

En este tutorial aprenderá a ejecutar una aplicación .NET para Apache Spark con .NET Core en Windows, MacOS y Ubuntu.

En este tutorial aprenderá a:

> [!div class="checklist"]
>
> * Preparar el entorno de .NET para Apache Spark
> * Implementar la primer aplicación .NET para Apache Spark
> * Compilar y ejecutar una aplicación .NET para Apache Spark sencilla

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prepare-your-environment"></a>Preparación del entorno

Antes de comenzar a escribir la aplicación, debe configurar algunas dependencias de requisitos previos. Si puede ejecutar `dotnet`, `java`, `mvn`, `spark-shell` desde el entorno de línea de comandos, el entorno ya está preparado y puede ir directamente a la sección siguiente. Si no puede ejecutar alguno o ninguno de los comandos, siga estos pasos.

### <a name="1-install-net"></a>1. Instalación de .NET

Para empezar a compilar aplicaciones .NET, debe descargar e instalar el SDK (kit de desarrollo de software) de .NET.

Descargue e instale el [SDK de .NET Core](https://dotnet.microsoft.com/download/dotnet-core/3.1). Al instalar el SDK, se agrega la cadena de herramientas `dotnet` a la variable de entorno PATH.

Una vez instalado el SDK de .NET Core, abra un símbolo del sistema o terminal nuevo y ejecute `dotnet`.

Si el comando se ejecuta e imprime información sobre cómo usar dotnet, puede pasar al paso siguiente. Si recibe un error `'dotnet' is not recognized as an internal or external command`, asegúrese de que ha abierto un símbolo del sistema o terminal **nuevo** antes de ejecutar el comando.

### <a name="2-install-java"></a>2. Instalación de Java

Instale [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) para Windows y MacOS, o [OpenJDK 8](https://openjdk.java.net/install/) para Ubuntu.

Seleccione la versión adecuada según su sistema operativo. Por ejemplo, seleccione **jdk-8u201-windows-x64.exe** para una máquina Windows x64 (tal como se muestra debajo) o **jdk-8u231-macosx-x64.dmg** para MacOS. Después, use el comando `java` para comprobar la instalación.

![Descarga de Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a>3. Instalación de software de compresión

Apache Spark se descarga como un archivo .tgz comprimido. Use un programa de extracción, como[7-Zip](https://www.7-zip.org/) o [WinZip](https://www.winzip.com/), para extraer el archivo.

### <a name="4-install-apache-spark"></a>4. Instalación de Apache Spark

[Descargue e instale](https://spark.apache.org/downloads.html) Apache Spark. Tendrá que seleccionar entre la versión 2.3.* o 2.4.0, 2.4.1, 2.4.3, o bien 2.4.4 (.NET para Apache Spark no es compatible con otras versiones de Apache Spark).

En los comandos que se usan en los pasos siguientes se supone que ha [descargado e instalado Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz). Si prefiere usar otra versión, reemplace **2.4.1** por el número de versión adecuado. Después, extraiga el archivo **.tar** y los archivos de Apache Spark.

Para extraer el archivo **.tar** anidado:

* Busque el archivo **spark-2.4.1-bin-hadoop2.7.tgz** que ha descargado.
* Haga clic con el botón derecho en el archivo y seleccione **7-Zip -> Extraer aquí**.
* Se creará **spark-2.4.1-bin-hadoop2.7.tar** junto con el archivo **.tgz** que ha descargado.

Para extraer los archivos de Apache Spark:

* Haga clic con el botón derecho en **spark-2.4.1-bin-hadoop2.7.tar** y seleccione **7-Zip -> Extraer archivos...**
* Escriba **C:\bin** en el campo **Extraer en**.
* Desactive la casilla situada debajo del campo **Extraer en**.
* Seleccione **Aceptar**.
* Los archivos de Apache Spark se extraen en C:\bin\spark-2.4.1-bin-hadoop2.7\.

![Instalación de Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

Ejecute los comandos siguientes para establecer las variables de entorno que se usan para buscar Apache Spark en **Windows**:

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

Ejecute los comandos siguientes para establecer las variables de entorno que se usan para buscar Apache Spark en **MacOS** y **Ubuntu**:

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

Una vez que se haya instalado todo y establecido las variables de entorno, abra un símbolo del sistema o terminal **nuevo** y ejecute el comando siguiente:

`%SPARK_HOME%\bin\spark-submit --version`

Si el comando se ejecuta e imprime la información de versión, puede pasar al paso siguiente.

Si recibe un error `'spark-submit' is not recognized as an internal or external command`, asegúrese de que ha abierto un símbolo del sistema **nuevo**.

### <a name="5-install-net-for-apache-spark"></a>5. Instalación de .NET para Apache Spark

Descargue la versión [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) de la página de .NET para Apache Spark en GitHub. Por ejemplo, si se encuentra en una máquina Windows y planea usar .NET Core, [descargue la versión Windows x64 netcoreapp3.1](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).

Para extraer Microsoft.Spark.Worker:

* Busque el archivo **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** que ha descargado.
* Haga clic con el botón derecho y seleccione **7-Zip -> Extraer archivos...** .
* Escriba **C:\bin** en el campo **Extraer en**.
* Desactive la casilla situada debajo del campo **Extraer en**.
* Seleccione **Aceptar**.

![Instalación de .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a>6. Instalación de WinUtils (solo Windows)

.NET para Apache Spark requiere que se instale WinUtils junto a Apache Spark. [Descargue winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe). Después, copie WinUtils en **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.

> [!NOTE]
> Si usa otra versión de Hadoop (anotada al final del nombre de la carpeta de instalación de Spark) [seleccione la versión de WinUtils](https://github.com/steveloughran/winutils) que sea compatible con la versión de Hadoop.

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a>7. Establecimiento de DOTNET_WORKER_DIR y comprobación de las dependencias

Ejecute uno de los comandos siguientes para establecer la Variable de entorno `DOTNET_WORKER_DIR`, que las aplicaciones .NET usan con el fin de buscar .NET para Apache Spark.

En **Windows**, cree una [variable de entorno nueva](https://www.java.com/en/download/help/path.xml) llamada `DOTNET_WORKER_DIR` y establézcala en el directorio donde se ha descargado y extraído Microsoft.Spark.Worker (por ejemplo, `C:\bin\Microsoft.Spark.Worker\`).

En **MacOS**, cree una variable de entorno nueva mediante `export DOTNET_WORKER_DIR <your_path>` y establézcala en el directorio donde se ha descargado y extraído Microsoft.Spark.Worker (por ejemplo, *~/bin/Microsoft.Spark.Worker/* ).

En **Ubuntu**, cree una [variable de entorno nueva](https://help.ubuntu.com/community/EnvironmentVariables) llamada `DOTNET_WORKER_DIR` y establézcala en el directorio donde se ha descargado y extraído Microsoft.Spark.Worker (por ejemplo, *~/bin/Microsoft.Spark.Worker*).

Por último, confirme que puede ejecutar `dotnet`, `java`, `mvn`, `spark-shell` desde la línea de comandos antes de pasar a la sección siguiente.

## <a name="write-a-net-for-apache-spark-app"></a>Escritura de una aplicación de .NET para Apache Spark

### <a name="1-create-a-console-app"></a>1. Crear una aplicación de consola

En el símbolo del sistema o terminal, ejecute los comandos siguientes para crear una aplicación de consola nueva:

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

El comando `dotnet` crea una aplicación `new` de tipo `console` de forma automática. El parámetro `-o` crea un directorio denominado *mySparkApp* donde se almacena la aplicación y lo rellena con los archivos necesarios. El comando `cd mySparkApp` cambia el directorio al directorio de la aplicación que acaba de crear.

### <a name="2-install-nuget-package"></a>2. Instalación del paquete NuGet

Para usar .NET para Apache Spark en una aplicación, instale el paquete Microsoft.Spark. En el símbolo del sistema o terminal, ejecute el comando siguiente:

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a>3. Diseño del código de la aplicación

Abra *Program.cs* en Visual Studio Code o cualquier editor de texto, y reemplace todo el código por lo siguiente:

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            SparkSession spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            DataFrame words = dataFrame
                .Select(Functions.Split(Functions.Col("value"), " ").Alias("words"))
                .Select(Functions.Explode(Functions.Col("words"))
                .Alias("word"))
                .GroupBy("word")
                .Count()
                .OrderBy(Functions.Col("count").Desc());

            // Show results.
            words.Show();

            // Stop Spark session.
            spark.Stop();
        }
    }
}
```

### <a name="4-create-and-add-a-data-file"></a>4. Creación y adición de un archivo de datos

Abra el símbolo del sistema o terminal y vaya a la carpeta de la aplicación.

```bash
cd <your-app-output-directory>
```

La aplicación procesa un archivo que contiene líneas de texto. Cree un archivo *input.txt* en el directorio *mySparkApp*, con el texto siguiente:

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a>Ejecución de la aplicación de .NET para Apache Spark

1. Ejecute el comando siguiente para compilar la aplicación:

   ```dotnetcli
   dotnet build
   ```

2. Ejecute el comando siguiente para enviar la aplicación para que se ejecute en Apache Spark:

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > Este comando asume que se ha descargado Apache Spark y se ha agregado a la variable de entorno PATH para poder usar `spark-submit`. De lo contrario, tendría que usar la ruta de acceso completa (por ejemplo, *C:\bin\apache-spark\bin\spark-submit* o *~/spark/bin/spark-submit*).

3. Cuando la aplicación se ejecuta, los datos de recuento de palabras del archivo *input.txt* se escriben en la consola.

¡Enhorabuena! Ha creado y ejecutado correctamente una aplicación de .NET para Apache Spark.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial ha aprendido a:
> [!div class="checklist"]
>
> * Preparar el entorno de Windows para .NET para Apache Spark
> * Implementar la primer aplicación .NET para Apache Spark
> * Compilar y ejecutar una aplicación .NET para Apache Spark sencilla

Para ver un vídeo en el que se explican los pasos anteriores, consulte la [serie de vídeos .NET para Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).

Eche un vistazo a la página de recursos para obtener más información.
> [!div class="nextstepaction"]
> [Recursos de .NET para Apache Spark](../resources/index.md)

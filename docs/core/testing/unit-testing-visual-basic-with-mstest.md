---
title: Prueba unitaria de Visual Basic en .NET Core con dotnet test y MSTest
description: 'Aprenda los conceptos de pruebas unitarias en .NET Core: cree una solución de Visual Basic de ejemplo paso a paso mediante MSTest.'
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.openlocfilehash: 9654d05754b83033bcaef6d8b8f24e3ba1d8bb2f
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656454"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a><span data-ttu-id="aca94-103">Bibliotecas de .NET Core de prueba unitaria de Visual Basic con pruebas de dotnet y MSTest</span><span class="sxs-lookup"><span data-stu-id="aca94-103">Unit testing Visual Basic .NET Core libraries using dotnet test and MSTest</span></span>

<span data-ttu-id="aca94-104">Este tutorial le guía por una experiencia interactiva de creación de una solución de ejemplo paso a paso para aprender los conceptos de pruebas unitarias.</span><span class="sxs-lookup"><span data-stu-id="aca94-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="aca94-105">Si prefiere seguir el tutorial con una solución precompilada, [vea o descargue el código de ejemplo](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) antes de comenzar.</span><span class="sxs-lookup"><span data-stu-id="aca94-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) before you begin.</span></span> <span data-ttu-id="aca94-106">Para obtener instrucciones de descarga, vea [Ejemplos y tutoriales](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="aca94-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="aca94-107">Crear el proyecto de origen</span><span class="sxs-lookup"><span data-stu-id="aca94-107">Creating the source project</span></span>

<span data-ttu-id="aca94-108">Abra una ventana del Shell.</span><span class="sxs-lookup"><span data-stu-id="aca94-108">Open a shell window.</span></span> <span data-ttu-id="aca94-109">Cree un directorio llamado *unit-testing-vb-mstest* que contenga la solución.</span><span class="sxs-lookup"><span data-stu-id="aca94-109">Create a directory called *unit-testing-vb-mstest* to hold the solution.</span></span>
<span data-ttu-id="aca94-110">En este directorio nuevo, ejecute [`dotnet new sln`](../tools/dotnet-new.md) para crear una solución nueva.</span><span class="sxs-lookup"><span data-stu-id="aca94-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="aca94-111">Esta práctica permite facilitar la administración de la biblioteca de clases y del proyecto de prueba unitaria.</span><span class="sxs-lookup"><span data-stu-id="aca94-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="aca94-112">En el directorio de la solución, cree un directorio *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="aca94-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="aca94-113">Hasta el momento, esta es la estructura de directorios y archivos:</span><span class="sxs-lookup"><span data-stu-id="aca94-113">You have the following directory and file structure thus far:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

<span data-ttu-id="aca94-114">Convierta *PrimeService* en el directorio actual y ejecute [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) para crear el proyecto de origen.</span><span class="sxs-lookup"><span data-stu-id="aca94-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="aca94-115">Cambie el nombre de *Class1.VB* a *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="aca94-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="aca94-116">Creará una implementación de errores de la clase `PrimeService`:</span><span class="sxs-lookup"><span data-stu-id="aca94-116">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="aca94-117">Cambien nuevamente el directorio al directorio *unit-testing-vb-using-mstest*.</span><span class="sxs-lookup"><span data-stu-id="aca94-117">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="aca94-118">Ejecute [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) para agregar el proyecto de biblioteca de clases a la solución.</span><span class="sxs-lookup"><span data-stu-id="aca94-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="aca94-119">Crear el proyecto de prueba</span><span class="sxs-lookup"><span data-stu-id="aca94-119">Creating the test project</span></span>

<span data-ttu-id="aca94-120">A continuación, cree el directorio *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="aca94-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="aca94-121">En el esquema siguiente se muestra la estructura de directorios:</span><span class="sxs-lookup"><span data-stu-id="aca94-121">The following outline shows the directory structure:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="aca94-122">Convierta el directorio *PrimeService.Tests* en el directorio actual y cree un proyecto nuevo con [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="aca94-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="aca94-123">Este comando crea un proyecto de prueba que usa MSTest como biblioteca de pruebas.</span><span class="sxs-lookup"><span data-stu-id="aca94-123">This command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="aca94-124">La plantilla generada ha configurado el ejecutor de pruebas en *PrimeServiceTests.vbproj*:</span><span class="sxs-lookup"><span data-stu-id="aca94-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="aca94-125">El proyecto de prueba requiere otros paquetes para crear y ejecutar pruebas unitarias.</span><span class="sxs-lookup"><span data-stu-id="aca94-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="aca94-126">`dotnet new` en el paso anterior agregó MSTest y el ejecutor de MSTest.</span><span class="sxs-lookup"><span data-stu-id="aca94-126">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="aca94-127">Ahora, agregue la biblioteca de clases `PrimeService` como otra dependencia al proyecto.</span><span class="sxs-lookup"><span data-stu-id="aca94-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="aca94-128">Use el comando [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="aca94-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="aca94-129">Puede ver todo el archivo en el [repositorio de muestras](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) en GitHub.</span><span class="sxs-lookup"><span data-stu-id="aca94-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="aca94-130">Tiene el diseño de solución final siguiente:</span><span class="sxs-lookup"><span data-stu-id="aca94-130">You have the following final solution layout:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="aca94-131">Ejecute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) en el directorio *unit-testing-vb-mstest*.</span><span class="sxs-lookup"><span data-stu-id="aca94-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-mstest* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="aca94-132">Crear la primera prueba</span><span class="sxs-lookup"><span data-stu-id="aca94-132">Creating the first test</span></span>

<span data-ttu-id="aca94-133">Escribirá una prueba de errores, la aprobará y, luego, repetirá el proceso.</span><span class="sxs-lookup"><span data-stu-id="aca94-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="aca94-134">Quite *UnitTest1.vb* del directorio *PrimeService.Tests* y cree un archivo de Visual Basic nuevo denominado *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="aca94-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="aca94-135">Agregue el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="aca94-135">Add the following code:</span></span>

```vb
Imports Microsoft.VisualStudio.TestTools.UnitTesting

Namespace PrimeService.Tests
    <TestClass>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <TestMethod>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.IsFalse(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="aca94-136">El atributo `<TestClass>` indica una clase que contiene pruebas.</span><span class="sxs-lookup"><span data-stu-id="aca94-136">The `<TestClass>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="aca94-137">El atributo `<TestMethod>` indica un método que el ejecutor de pruebas ejecuta.</span><span class="sxs-lookup"><span data-stu-id="aca94-137">The `<TestMethod>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="aca94-138">En *unit-testing-vb-mstest*, ejecute [`dotnet test`](../tools/dotnet-test.md) para compilar las pruebas y la biblioteca de clases y luego ejecutar las pruebas.</span><span class="sxs-lookup"><span data-stu-id="aca94-138">From the *unit-testing-vb-mstest*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="aca94-139">El ejecutor de pruebas de MSTest tiene el punto de entrada del programa para ejecutar las pruebas desde la consola.</span><span class="sxs-lookup"><span data-stu-id="aca94-139">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="aca94-140">`dotnet test` inicia el ejecutor de pruebas con el proyecto de prueba unitaria que creó.</span><span class="sxs-lookup"><span data-stu-id="aca94-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="aca94-141">La prueba produce un error.</span><span class="sxs-lookup"><span data-stu-id="aca94-141">Your test fails.</span></span> <span data-ttu-id="aca94-142">Todavía no ha creado la implementación.</span><span class="sxs-lookup"><span data-stu-id="aca94-142">You haven't created the implementation yet.</span></span> <span data-ttu-id="aca94-143">Cree esta prueba que se supera escribiendo el código más simple en la clase `PrimeService` que funciona:</span><span class="sxs-lookup"><span data-stu-id="aca94-143">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="aca94-144">En el directorio *unit-testing-vb-mstest*, vuelva a ejecutar `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="aca94-144">In the *unit-testing-vb-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="aca94-145">El comando `dotnet test` ejecuta una compilación del proyecto `PrimeService` y luego del proyecto `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="aca94-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="aca94-146">Después de compilar ambos proyectos, se ejecuta esta única prueba.</span><span class="sxs-lookup"><span data-stu-id="aca94-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="aca94-147">Pasa.</span><span class="sxs-lookup"><span data-stu-id="aca94-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="aca94-148">Agregar más características</span><span class="sxs-lookup"><span data-stu-id="aca94-148">Adding more features</span></span>

<span data-ttu-id="aca94-149">Ahora que la prueba se ha superado, es el momento de escribir más.</span><span class="sxs-lookup"><span data-stu-id="aca94-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="aca94-150">Hay algunos otros casos simples para números primos: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="aca94-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="aca94-151">Puede agregar esos casos como nuevas pruebas con el atributo `<TestMethod>`, pero enseguida este proceso se hace tedioso.</span><span class="sxs-lookup"><span data-stu-id="aca94-151">You could add those cases as new tests with the `<TestMethod>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="aca94-152">Hay otros atributos de MSTest que le permiten escribir un conjunto de pruebas similares.</span><span class="sxs-lookup"><span data-stu-id="aca94-152">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="aca94-153">Un atributo `<DataTestMethod>` representa un conjunto de pruebas que ejecutan el mismo código, pero tienen diferentes argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="aca94-153">A `<DataTestMethod>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="aca94-154">Puede usar el atributo `<DataRow>` para especificar valores para esas entradas.</span><span class="sxs-lookup"><span data-stu-id="aca94-154">You can use the `<DataRow>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="aca94-155">En lugar de crear pruebas nuevas, aplique estos dos atributos para crear una sola teoría.</span><span class="sxs-lookup"><span data-stu-id="aca94-155">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="aca94-156">La teoría es un método que prueba varios valores menores que dos, que es el número primo menor:</span><span class="sxs-lookup"><span data-stu-id="aca94-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-mstest/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="aca94-157">Ejecute `dotnet test`, y dos de estas pruebas no se superarán.</span><span class="sxs-lookup"><span data-stu-id="aca94-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="aca94-158">Para superar todas las pruebas, cambie la cláusula `if` al principio del método:</span><span class="sxs-lookup"><span data-stu-id="aca94-158">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="aca94-159">Puede continuar recorriendo en iteración agregando más pruebas, más teorías y más código en la biblioteca principal.</span><span class="sxs-lookup"><span data-stu-id="aca94-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="aca94-160">Ya tiene la [versión terminada de las pruebas](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) y la [implementación completa de la biblioteca](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="aca94-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="aca94-161">Ha creado una biblioteca pequeña y un conjunto de pruebas unitarias para esa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="aca94-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="aca94-162">Ha estructurado la solución, por lo que agregar pruebas y paquetes nuevos es parte del flujo de trabajo normal.</span><span class="sxs-lookup"><span data-stu-id="aca94-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="aca94-163">Ha centrado la mayor parte del tiempo y del esfuerzo en resolver los objetivos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="aca94-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

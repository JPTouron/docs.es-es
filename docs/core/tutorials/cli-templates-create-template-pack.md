---
title: Creación de un paquete de plantillas para dotnet new
description: Obtenga información sobre cómo crear un archivo csproj que compilará un paquete de plantillas para el comando dotnet new.
author: adegeo
ms.date: 12/10/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 25264fff42c47f5bb660f68f85dbb123b5b2608c
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324342"
---
# <a name="tutorial-create-a-template-pack"></a><span data-ttu-id="61533-103">Tutorial: Creación de un paquete de plantillas</span><span class="sxs-lookup"><span data-stu-id="61533-103">Tutorial: Create a template pack</span></span>

<span data-ttu-id="61533-104">Con .NET Core, puede crear e implementar plantillas que generan proyectos, archivos e inclusos recursos.</span><span class="sxs-lookup"><span data-stu-id="61533-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="61533-105">Este tutorial es el tercero de una serie que enseña a crear, instalar y desinstalar plantillas para usarlas con el comando `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="61533-105">This tutorial is part three of a series that teaches you how to create, install, and uninstall templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="61533-106">En esta parte de la serie, aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="61533-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="61533-107">Crear un proyecto \*.csproj para compilar un paquete de plantillas</span><span class="sxs-lookup"><span data-stu-id="61533-107">Create a \*.csproj project to build a template pack</span></span>
> * <span data-ttu-id="61533-108">Configurar el archivo del proyecto para el empaquetado.</span><span class="sxs-lookup"><span data-stu-id="61533-108">Configure the project file for packing</span></span>
> * <span data-ttu-id="61533-109">Instalar una plantilla a partir de un archivo de paquete de NuGet.</span><span class="sxs-lookup"><span data-stu-id="61533-109">Install a template from a NuGet package file</span></span>
> * <span data-ttu-id="61533-110">Desinstalar una plantilla por el identificador del paquete.</span><span class="sxs-lookup"><span data-stu-id="61533-110">Uninstall a template by package ID</span></span>

## <a name="prerequisites"></a><span data-ttu-id="61533-111">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="61533-111">Prerequisites</span></span>

* <span data-ttu-id="61533-112">Complete la [parte 1](cli-templates-create-item-template.md) y la [parte 2](cli-templates-create-project-template.md) de esta serie de tutoriales.</span><span class="sxs-lookup"><span data-stu-id="61533-112">Complete [part 1](cli-templates-create-item-template.md) and [part 2](cli-templates-create-project-template.md) of this tutorial series.</span></span>

  <span data-ttu-id="61533-113">En este tutorial se usan las dos plantillas que se crearon en las dos primeras partes de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="61533-113">This tutorial uses the two templates created in the first two parts of this tutorial.</span></span> <span data-ttu-id="61533-114">Puede usar otra plantilla siempre que la copie como una carpeta en la carpeta _working\templates\\_ .</span><span class="sxs-lookup"><span data-stu-id="61533-114">You can use a different template as long as you copy the template, as a folder, into the _working\templates\\_ folder.</span></span>

* <span data-ttu-id="61533-115">Abra un terminal y vaya a la carpeta _working\\_ .</span><span class="sxs-lookup"><span data-stu-id="61533-115">Open a terminal and navigate to the _working\\_ folder.</span></span>

## <a name="create-a-template-pack-project"></a><span data-ttu-id="61533-116">Creación de un proyecto de paquete de plantillas</span><span class="sxs-lookup"><span data-stu-id="61533-116">Create a template pack project</span></span>

<span data-ttu-id="61533-117">Cuando se habla un paquete de plantillas, nos referimos a una o más plantillas empaquetadas en un archivo.</span><span class="sxs-lookup"><span data-stu-id="61533-117">A template pack is one or more templates packaged into a file.</span></span> <span data-ttu-id="61533-118">Cuando instala o desinstala un paquete, se agregan o quitan todas las plantillas del paquete, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="61533-118">When you install or uninstall a pack, all templates contained in the pack are added or removed, respectively.</span></span> <span data-ttu-id="61533-119">Las partes anteriores de esta serie de tutoriales solo funcionan con plantillas individuales.</span><span class="sxs-lookup"><span data-stu-id="61533-119">The previous parts of this tutorial series only worked with individual templates.</span></span> <span data-ttu-id="61533-120">Para compartir una plantilla no empaquetada, tiene que copiar la carpeta de plantilla y realizar la instalación mediante esa carpeta.</span><span class="sxs-lookup"><span data-stu-id="61533-120">To share a non-packed template, you have to copy the template folder and install via that folder.</span></span> <span data-ttu-id="61533-121">Como un paquete de plantillas puede tener más de una plantilla y se trata de un solo archivo, compartirlo resulta sencillo.</span><span class="sxs-lookup"><span data-stu-id="61533-121">Because a template pack can have more than one template in it, and is a single file, sharing is easier.</span></span>

<span data-ttu-id="61533-122">Los paquetes de plantillas se representan con un archivo ( _.nupkg_) de paquete de NuGet.</span><span class="sxs-lookup"><span data-stu-id="61533-122">Template packs are represented by a NuGet package (_.nupkg_) file.</span></span> <span data-ttu-id="61533-123">Y, al igual que lo que ocurre con cualquier paquete de NuGet, puede cargar el paquete de plantillas a una fuente NuGet.</span><span class="sxs-lookup"><span data-stu-id="61533-123">And, like any NuGet package, you can upload the template pack to a NuGet feed.</span></span> <span data-ttu-id="61533-124">El comando `dotnet new -i` permite instalar un paquete de plantillas desde una fuente NuGet.</span><span class="sxs-lookup"><span data-stu-id="61533-124">The `dotnet new -i` command supports installing template pack from a NuGet package feed.</span></span> <span data-ttu-id="61533-125">Además, puede instalar un paquete de plantillas directamente desde un archivo _.nupkg_.</span><span class="sxs-lookup"><span data-stu-id="61533-125">Additionally, you can install a template pack from a _.nupkg_ file directly.</span></span>

<span data-ttu-id="61533-126">Por lo general, se usa un archivo del proyecto de C# para compilar el código y generar un archivo binario.</span><span class="sxs-lookup"><span data-stu-id="61533-126">Normally you use a C# project file to compile code and produce a binary.</span></span> <span data-ttu-id="61533-127">Pero el proyecto también se puede usar para generar un paquete de plantillas.</span><span class="sxs-lookup"><span data-stu-id="61533-127">However, the project can also be used to generate a template pack.</span></span> <span data-ttu-id="61533-128">Si cambia la configuración del archivo _.csproj_, puede impedir que compile código y, en su lugar, incluir todos los recursos de las plantillas como recursos.</span><span class="sxs-lookup"><span data-stu-id="61533-128">By changing the settings of the _.csproj_, you can prevent it from compiling any code and instead include all the assets of your templates as resources.</span></span> <span data-ttu-id="61533-129">Cuando se compila este proyecto, genera un paquete de NuGet de paquete de plantillas.</span><span class="sxs-lookup"><span data-stu-id="61533-129">When this project is built, it produces a template pack NuGet package.</span></span>

<span data-ttu-id="61533-130">El paquete que va a crear incluirá la [plantilla de elemento](cli-templates-create-item-template.md) y la [plantilla de paquete](cli-templates-create-project-template.md) que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="61533-130">The pack you'll create will include the [item template](cli-templates-create-item-template.md) and [package template](cli-templates-create-project-template.md) previously created.</span></span> <span data-ttu-id="61533-131">Como agrupamos ambas plantillas en la carpeta _working\templates\\_ , podemos usar la carpeta _working_ para el archivo _.csproj_.</span><span class="sxs-lookup"><span data-stu-id="61533-131">Because we grouped the two templates into the _working\templates\\_ folder, we can use the _working_ folder for the _.csproj_ file.</span></span>

<span data-ttu-id="61533-132">En el terminal, vaya a la carpeta _working_.</span><span class="sxs-lookup"><span data-stu-id="61533-132">In your terminal, navigate to the _working_ folder.</span></span> <span data-ttu-id="61533-133">Cree un proyecto nuevo y establezca el nombre en `templatepack` y la carpeta de salida en la carpeta actual.</span><span class="sxs-lookup"><span data-stu-id="61533-133">Create a new project and set the name to `templatepack` and the output folder to the current folder.</span></span>

```dotnetcli
dotnet new console -n templatepack -o .
```

<span data-ttu-id="61533-134">El parámetro `-n` establece el nombre de archivo _.csproj_ en _templatepack.csproj_.</span><span class="sxs-lookup"><span data-stu-id="61533-134">The `-n` parameter sets the _.csproj_ filename to _templatepack.csproj_.</span></span> <span data-ttu-id="61533-135">El parámetro `-o` crea los archivos en el directorio actual.</span><span class="sxs-lookup"><span data-stu-id="61533-135">The `-o` parameter creates the files in the current directory.</span></span> <span data-ttu-id="61533-136">Verá un resultado similar a la salida siguiente.</span><span class="sxs-lookup"><span data-stu-id="61533-136">You should see a result similar to the following output.</span></span>

```dotnetcli
dotnet new console -n templatepack -o .
```

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

<span data-ttu-id="61533-137">A continuación, abra el archivo _templatepack.csproj_ en su editor favorito y reemplace el contenido por el XML siguiente:</span><span class="sxs-lookup"><span data-stu-id="61533-137">Next, open the _templatepack.csproj_ file in your favorite editor and replace the content with the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <PackageTags>dotnet-new;templates;contoso</PackageTags>

    <TargetFramework>netstandard2.0</TargetFramework>

    <IncludeContentInPack>true</IncludeContentInPack>
    <IncludeBuildOutput>false</IncludeBuildOutput>
    <ContentTargetFolders>content</ContentTargetFolders>
  </PropertyGroup>

  <ItemGroup>
    <Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />
    <Compile Remove="**\*" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="61533-138">El valor `<PropertyGroup>` del XML anterior se divide en tres grupos.</span><span class="sxs-lookup"><span data-stu-id="61533-138">The `<PropertyGroup>` settings in the XML above is broken into three groups.</span></span> <span data-ttu-id="61533-139">El primer grupo trata con las propiedades requeridas para un paquete de NuGet.</span><span class="sxs-lookup"><span data-stu-id="61533-139">The first group deals with properties required for a NuGet package.</span></span> <span data-ttu-id="61533-140">Los tres valores `<Package` están relacionados con las propiedades del paquete de NuGet para identificar el paquete en una fuente NuGet.</span><span class="sxs-lookup"><span data-stu-id="61533-140">The three `<Package` settings have to do with the NuGet package properties to identify your package on a NuGet feed.</span></span> <span data-ttu-id="61533-141">En concreto, el valor `<PackageId>` se usa para desinstalar el paquete de plantillas con un solo nombre en lugar de una ruta de acceso a un directorio.</span><span class="sxs-lookup"><span data-stu-id="61533-141">Specifically the `<PackageId>` value is used to uninstall the template pack with a single name instead of a directory path.</span></span> <span data-ttu-id="61533-142">También se puede usar para instalar el paquete de plantillas desde una fuente NuGet.</span><span class="sxs-lookup"><span data-stu-id="61533-142">It can also be used to install the template pack from a NuGet feed.</span></span> <span data-ttu-id="61533-143">Los valores restantes, como `<Title>` y `<PackageTags>`, están relacionados con los metadatos que aparecen en la fuente NuGet.</span><span class="sxs-lookup"><span data-stu-id="61533-143">The remaining settings such as `<Title>` and `<PackageTags>` have to do with metadata displayed on the NuGet feed.</span></span> <span data-ttu-id="61533-144">Para más información sobre la configuración de NuGet, consulte el artículo sobre [propiedades de NuGet y MSBuild](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="61533-144">For more information about NuGet settings, see [NuGet and MSBuild properties](/nuget/reference/msbuild-targets).</span></span>

<span data-ttu-id="61533-145">La configuración `<TargetFramework>` se debe establecer de manera que MSBuild se ejecute correctamente al ejecutar el comando pack para compilar y empaquetar el proyecto.</span><span class="sxs-lookup"><span data-stu-id="61533-145">The `<TargetFramework>` setting must be set so that MSBuild will run properly when you run the pack command to compile and pack the project.</span></span>

<span data-ttu-id="61533-146">Los tres últimos valores están relacionados con la configuración correcta del proyecto para incluir las plantillas en la carpeta correspondiente del paquete de NuGet cuando se crea.</span><span class="sxs-lookup"><span data-stu-id="61533-146">The last three settings have to do with configuring the project correctly to include the templates in the appropriate folder in the NuGet pack when it's created.</span></span>

<span data-ttu-id="61533-147">`<ItemGroup>` contiene dos valores.</span><span class="sxs-lookup"><span data-stu-id="61533-147">The `<ItemGroup>` contains two settings.</span></span> <span data-ttu-id="61533-148">En primer lugar, el valor `<Content>` incluye todo lo que hay en la carpeta _templates_ como contenido.</span><span class="sxs-lookup"><span data-stu-id="61533-148">First, the `<Content>` setting includes everything in the _templates_ folder as content.</span></span> <span data-ttu-id="61533-149">También se establece para excluir cualquier carpeta _bin_ o carpeta _obj_ para evitar que se incluya cualquier código compilado (si probó y compiló las plantillas).</span><span class="sxs-lookup"><span data-stu-id="61533-149">It's also set to exclude any _bin_ folder or _obj_ folder to prevent any compiled code (if you tested and compiled your templates) from being included.</span></span> <span data-ttu-id="61533-150">En segundo lugar, el valor `<Compile>` excluye todos los archivos de código de la compilación, independientemente de dónde estén ubicados.</span><span class="sxs-lookup"><span data-stu-id="61533-150">Second, the `<Compile>` setting excludes all code files from compiling no matter where they're located.</span></span> <span data-ttu-id="61533-151">Esto evita que el proyecto que se usa para crear un paquete de plantillas intente compilar el código en la jerarquía de carpetas _templates_.</span><span class="sxs-lookup"><span data-stu-id="61533-151">This setting prevents the project being used to create a template pack from trying to compile the code in the _templates_ folder hierarchy.</span></span>

## <a name="build-and-install"></a><span data-ttu-id="61533-152">Compilación e instalación</span><span class="sxs-lookup"><span data-stu-id="61533-152">Build and install</span></span>

<span data-ttu-id="61533-153">Guarde este archivo y, a continuación, ejecute el comando pack.</span><span class="sxs-lookup"><span data-stu-id="61533-153">Save this file and then run the pack command</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="61533-154">Este comando compilará el proyecto y creará un paquete NuGet en la carpeta _working\bin\Debug_.</span><span class="sxs-lookup"><span data-stu-id="61533-154">This command will build your project and create a NuGet package in This should be the _working\bin\Debug_ folder.</span></span>

```dotnetcli
dotnet pack
```

```console
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

<span data-ttu-id="61533-155">A continuación, instale el archivo del paquete de plantillas con el comando `dotnet new -i PATH_TO_NUPKG_FILE`.</span><span class="sxs-lookup"><span data-stu-id="61533-155">Next, install the template pack file with the `dotnet new -i PATH_TO_NUPKG_FILE` command.</span></span>

```console
C:\working> dotnet new -i C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync          [C#]              Common/Console/C#8
Class library                                     classlib              [C#], F#, VB      Common/Library
```

<span data-ttu-id="61533-156">Si cargó el paquete de NuGet en una fuente NuGet, puede usar el comando `dotnet new -i PACKAGEID`, donde `PACKAGEID` es igual que el valor `<PackageId>` del archivo _.csproj_.</span><span class="sxs-lookup"><span data-stu-id="61533-156">If you uploaded the NuGet package to a NuGet feed, you can use the `dotnet new -i PACKAGEID` command where `PACKAGEID` is the same as the `<PackageId>` setting from the _.csproj_ file.</span></span> <span data-ttu-id="61533-157">Este identificador de paquete es igual que el identificador del paquete de NuGet.</span><span class="sxs-lookup"><span data-stu-id="61533-157">This package ID is the same as the NuGet package identifier.</span></span>

## <a name="uninstall-the-template-pack"></a><span data-ttu-id="61533-158">Desinstalación del paquete de plantillas</span><span class="sxs-lookup"><span data-stu-id="61533-158">Uninstall the template pack</span></span>

<span data-ttu-id="61533-159">Independientemente de cómo instaló el paquete de plantillas, ya sea directamente con el archivo _.nupkg_ o mediante la fuente NuGet, el proceso de quitar un paquete de plantillas es el mismo.</span><span class="sxs-lookup"><span data-stu-id="61533-159">No matter how you installed the template pack, either with the _.nupkg_ file directly or by NuGet feed, removing a template pack is the same.</span></span> <span data-ttu-id="61533-160">Use el `<PackageId>` de la plantilla que quiere desinstalar.</span><span class="sxs-lookup"><span data-stu-id="61533-160">Use the `<PackageId>` of the template you want to uninstall.</span></span> <span data-ttu-id="61533-161">Ejecute el comando `dotnet new -u` para ver una lista de las plantillas que están instaladas.</span><span class="sxs-lookup"><span data-stu-id="61533-161">You can get a list of templates that are installed by running the `dotnet new -u` command.</span></span>

```dotnetcli
dotnet new -u
```

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      dotnet gitignore file (gitignore)
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)

... cut to save space ...

  NUnit3.DotNetNew.Template
    Templates:
      NUnit 3 Test Project (nunit) C#
      NUnit 3 Test Item (nunit-test) C#
      NUnit 3 Test Project (nunit) F#
      NUnit 3 Test Item (nunit-test) F#
      NUnit 3 Test Project (nunit) VB
      NUnit 3 Test Item (nunit-test) VB
  AdatumCorporation.Utility.Templates
    Templates:
      Example templates: async project (consoleasync) C#
      Example templates: string extensions (stringext) C#
```

<span data-ttu-id="61533-162">Ejecute `dotnet new -u AdatumCorporation.Utility.Templates` para desinstalar la plantilla.</span><span class="sxs-lookup"><span data-stu-id="61533-162">Run `dotnet new -u AdatumCorporation.Utility.Templates` to uninstall the template.</span></span> <span data-ttu-id="61533-163">El comando `dotnet new` generará información de ayuda sobre que debe omitir las plantillas que instaló previamente.</span><span class="sxs-lookup"><span data-stu-id="61533-163">The `dotnet new` command will output help information that should omit the templates you previously installed.</span></span>

<span data-ttu-id="61533-164">¡Enhorabuena!</span><span class="sxs-lookup"><span data-stu-id="61533-164">Congratulations!</span></span> <span data-ttu-id="61533-165">Ya instaló y desinstaló un paquete de plantillas.</span><span class="sxs-lookup"><span data-stu-id="61533-165">you've installed and uninstalled a template pack.</span></span>

## <a name="next-steps"></a><span data-ttu-id="61533-166">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="61533-166">Next steps</span></span>

<span data-ttu-id="61533-167">Para más información sobre las plantillas, que en gran parte ya conoce, consulte el artículo [Plantillas personalizadas para dotnet new](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="61533-167">To learn more about templates, most of which you've already learned, see the [Custom templates for dotnet new](../tools/custom-templates.md) article.</span></span>

* [<span data-ttu-id="61533-168">Wiki del repositorio de GitHub dotnet/templating</span><span class="sxs-lookup"><span data-stu-id="61533-168">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
* [<span data-ttu-id="61533-169">Repositorio de GitHub dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="61533-169">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
* [<span data-ttu-id="61533-170">Esquema *template.json* en el Almacenamiento del esquema JSON</span><span class="sxs-lookup"><span data-stu-id="61533-170">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)

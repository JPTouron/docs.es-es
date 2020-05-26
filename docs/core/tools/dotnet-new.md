---
title: Comando dotnet new
description: El comando dotnet new crea proyectos de .NET Core basados en la plantilla especificada.
ms.date: 04/10/2020
ms.openlocfilehash: 1544f519f2a5f6a1a6e042c1db720eff45f5d98c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442246"
---
# <a name="dotnet-new"></a><span data-ttu-id="c6cdc-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="c6cdc-103">dotnet new</span></span>

<span data-ttu-id="c6cdc-104">**Este artículo se aplica a:** ✔️ SDK de .NET Core 2.0 y versiones posteriores</span><span class="sxs-lookup"><span data-stu-id="c6cdc-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c6cdc-105">NOMBRE</span><span class="sxs-lookup"><span data-stu-id="c6cdc-105">Name</span></span>

<span data-ttu-id="c6cdc-106">`dotnet new`: crea un nuevo proyecto, archivo de configuración o solución según la plantilla especificada.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c6cdc-107">Sinopsis</span><span class="sxs-lookup"><span data-stu-id="c6cdc-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="c6cdc-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="c6cdc-108">Description</span></span>

<span data-ttu-id="c6cdc-109">El comando `dotnet new` crea un proyecto de .NET Core u otros artefactos basados en una plantilla.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="c6cdc-110">El comando llama al [motor de plantillas](https://github.com/dotnet/templating) para crear los artefactos en el disco basándose en las opciones y la plantilla especificadas.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="c6cdc-111">Restauración implícita</span><span class="sxs-lookup"><span data-stu-id="c6cdc-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="c6cdc-112">Argumentos</span><span class="sxs-lookup"><span data-stu-id="c6cdc-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="c6cdc-113">La plantilla de la que se va a crear una instancia cuando se invoca el comando.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="c6cdc-114">Cada plantilla puede tener opciones específicas que puede pasar.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="c6cdc-115">Para obtener más información, vea [Opciones de plantilla](#template-options).</span><span class="sxs-lookup"><span data-stu-id="c6cdc-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="c6cdc-116">Puede ejecutar `dotnet new --list` o `dotnet new -l` para ver una lista de todas las plantillas instaladas.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="c6cdc-117">Si el valor `TEMPLATE` no es una coincidencia exacta con el texto de la columna **Plantillas** o **Nombre corto** de la tabla devuelta, se realiza una coincidencia de subcadena con esas dos columnas.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="c6cdc-118">A partir del SDK de .NET Core 3.0, la CLI busca plantillas en NuGet.org al invocar el comando `dotnet new` en las siguientes condiciones:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="c6cdc-119">Si la CLI no encuentra ninguna coincidencia de plantilla al invocar `dotnet new`, ni siquiera parcial.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="c6cdc-120">Si hay disponible una versión más reciente de la plantilla.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="c6cdc-121">En este caso, se crea el proyecto o el artefacto, pero la CLI le advierte de que hay una versión actualizada de la plantilla.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="c6cdc-122">En la tabla siguiente se muestran las plantillas que vienen preinstaladas en el SDK de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="c6cdc-123">El lenguaje predeterminado de la plantilla se muestra entre corchetes.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="c6cdc-124">Haga clic en el vínculo del nombre corto para ver las opciones específicas de la plantilla.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="c6cdc-125">Plantillas</span><span class="sxs-lookup"><span data-stu-id="c6cdc-125">Templates</span></span>                                    | <span data-ttu-id="c6cdc-126">Nombre corto</span><span class="sxs-lookup"><span data-stu-id="c6cdc-126">Short name</span></span>                      | <span data-ttu-id="c6cdc-127">Lenguaje</span><span class="sxs-lookup"><span data-stu-id="c6cdc-127">Language</span></span>     | <span data-ttu-id="c6cdc-128">Etiquetas</span><span class="sxs-lookup"><span data-stu-id="c6cdc-128">Tags</span></span>                                  | <span data-ttu-id="c6cdc-129">Inclusión</span><span class="sxs-lookup"><span data-stu-id="c6cdc-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="c6cdc-130">Aplicación de consola</span><span class="sxs-lookup"><span data-stu-id="c6cdc-130">Console Application</span></span>                          | [<span data-ttu-id="c6cdc-131">console</span><span class="sxs-lookup"><span data-stu-id="c6cdc-131">console</span></span>](#console)             | <span data-ttu-id="c6cdc-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6cdc-132">[C#], F#, VB</span></span> | <span data-ttu-id="c6cdc-133">Común/Consola</span><span class="sxs-lookup"><span data-stu-id="c6cdc-133">Common/Console</span></span>                        | <span data-ttu-id="c6cdc-134">1.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-134">1.0</span></span>        |
| <span data-ttu-id="c6cdc-135">Biblioteca de clases</span><span class="sxs-lookup"><span data-stu-id="c6cdc-135">Class library</span></span>                                | [<span data-ttu-id="c6cdc-136">classlib</span><span class="sxs-lookup"><span data-stu-id="c6cdc-136">classlib</span></span>](#classlib)           | <span data-ttu-id="c6cdc-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6cdc-137">[C#], F#, VB</span></span> | <span data-ttu-id="c6cdc-138">Común/Biblioteca</span><span class="sxs-lookup"><span data-stu-id="c6cdc-138">Common/Library</span></span>                        | <span data-ttu-id="c6cdc-139">1.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-139">1.0</span></span>        |
| <span data-ttu-id="c6cdc-140">Aplicación WPF</span><span class="sxs-lookup"><span data-stu-id="c6cdc-140">WPF Application</span></span>                              | [<span data-ttu-id="c6cdc-141">wpf</span><span class="sxs-lookup"><span data-stu-id="c6cdc-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="c6cdc-142">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6cdc-142">[C#]</span></span>         | <span data-ttu-id="c6cdc-143">Común/WPF</span><span class="sxs-lookup"><span data-stu-id="c6cdc-143">Common/WPF</span></span>                            | <span data-ttu-id="c6cdc-144">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-144">3.0</span></span>        |
| <span data-ttu-id="c6cdc-145">Biblioteca de clases de WPF</span><span class="sxs-lookup"><span data-stu-id="c6cdc-145">WPF Class library</span></span>                            | [<span data-ttu-id="c6cdc-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="c6cdc-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="c6cdc-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6cdc-147">[C#]</span></span>         | <span data-ttu-id="c6cdc-148">Común/WPF</span><span class="sxs-lookup"><span data-stu-id="c6cdc-148">Common/WPF</span></span>                            | <span data-ttu-id="c6cdc-149">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-149">3.0</span></span>        |
| <span data-ttu-id="c6cdc-150">Biblioteca de controles personalizados WPF</span><span class="sxs-lookup"><span data-stu-id="c6cdc-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="c6cdc-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="c6cdc-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="c6cdc-152">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6cdc-152">[C#]</span></span>         | <span data-ttu-id="c6cdc-153">Común/WPF</span><span class="sxs-lookup"><span data-stu-id="c6cdc-153">Common/WPF</span></span>                            | <span data-ttu-id="c6cdc-154">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-154">3.0</span></span>        |
| <span data-ttu-id="c6cdc-155">Biblioteca de controles de usuario de WPF</span><span class="sxs-lookup"><span data-stu-id="c6cdc-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="c6cdc-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="c6cdc-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="c6cdc-157">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6cdc-157">[C#]</span></span>         | <span data-ttu-id="c6cdc-158">Común/WPF</span><span class="sxs-lookup"><span data-stu-id="c6cdc-158">Common/WPF</span></span>                            | <span data-ttu-id="c6cdc-159">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-159">3.0</span></span>        |
| <span data-ttu-id="c6cdc-160">Aplicación de Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="c6cdc-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="c6cdc-161">winforms</span><span class="sxs-lookup"><span data-stu-id="c6cdc-161">winforms</span></span>](#winforms)           | <span data-ttu-id="c6cdc-162">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6cdc-162">[C#]</span></span>         | <span data-ttu-id="c6cdc-163">Común/WinForms</span><span class="sxs-lookup"><span data-stu-id="c6cdc-163">Common/WinForms</span></span>                       | <span data-ttu-id="c6cdc-164">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-164">3.0</span></span>        |
| <span data-ttu-id="c6cdc-165">Biblioteca de clases de Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="c6cdc-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="c6cdc-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="c6cdc-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="c6cdc-167">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6cdc-167">[C#]</span></span>         | <span data-ttu-id="c6cdc-168">Común/WinForms</span><span class="sxs-lookup"><span data-stu-id="c6cdc-168">Common/WinForms</span></span>                       | <span data-ttu-id="c6cdc-169">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-169">3.0</span></span>        |
| <span data-ttu-id="c6cdc-170">Servicio Worker</span><span class="sxs-lookup"><span data-stu-id="c6cdc-170">Worker Service</span></span>                               | [<span data-ttu-id="c6cdc-171">worker</span><span class="sxs-lookup"><span data-stu-id="c6cdc-171">worker</span></span>](#web-others)           | <span data-ttu-id="c6cdc-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6cdc-172">[C#]</span></span>         | <span data-ttu-id="c6cdc-173">Común/Worker/Web</span><span class="sxs-lookup"><span data-stu-id="c6cdc-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="c6cdc-174">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-174">3.0</span></span>        |
| <span data-ttu-id="c6cdc-175">Proyecto de prueba unitaria</span><span class="sxs-lookup"><span data-stu-id="c6cdc-175">Unit Test Project</span></span>                            | [<span data-ttu-id="c6cdc-176">mstest</span><span class="sxs-lookup"><span data-stu-id="c6cdc-176">mstest</span></span>](#test)                 | <span data-ttu-id="c6cdc-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6cdc-177">[C#], F#, VB</span></span> | <span data-ttu-id="c6cdc-178">Prueba/MSTest</span><span class="sxs-lookup"><span data-stu-id="c6cdc-178">Test/MSTest</span></span>                           | <span data-ttu-id="c6cdc-179">1.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-179">1.0</span></span>        |
| <span data-ttu-id="c6cdc-180">Proyecto de prueba de NUnit 3</span><span class="sxs-lookup"><span data-stu-id="c6cdc-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="c6cdc-181">nunit</span><span class="sxs-lookup"><span data-stu-id="c6cdc-181">nunit</span></span>](#nunit)                  | <span data-ttu-id="c6cdc-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6cdc-182">[C#], F#, VB</span></span> | <span data-ttu-id="c6cdc-183">Prueba/NUnit</span><span class="sxs-lookup"><span data-stu-id="c6cdc-183">Test/NUnit</span></span>                            | <span data-ttu-id="c6cdc-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="c6cdc-184">2.1.400</span></span>    |
| <span data-ttu-id="c6cdc-185">Elemento de prueba de NUnit 3</span><span class="sxs-lookup"><span data-stu-id="c6cdc-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="c6cdc-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6cdc-186">[C#], F#, VB</span></span> | <span data-ttu-id="c6cdc-187">Prueba/NUnit</span><span class="sxs-lookup"><span data-stu-id="c6cdc-187">Test/NUnit</span></span>                            | <span data-ttu-id="c6cdc-188">2.2</span><span class="sxs-lookup"><span data-stu-id="c6cdc-188">2.2</span></span>        |
| <span data-ttu-id="c6cdc-189">Proyecto de prueba de xUnit</span><span class="sxs-lookup"><span data-stu-id="c6cdc-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="c6cdc-190">xunit</span><span class="sxs-lookup"><span data-stu-id="c6cdc-190">xunit</span></span>](#test)                  | <span data-ttu-id="c6cdc-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6cdc-191">[C#], F#, VB</span></span> | <span data-ttu-id="c6cdc-192">Prueba/xUnit</span><span class="sxs-lookup"><span data-stu-id="c6cdc-192">Test/xUnit</span></span>                            | <span data-ttu-id="c6cdc-193">1.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-193">1.0</span></span>        |
| <span data-ttu-id="c6cdc-194">Componente Razor</span><span class="sxs-lookup"><span data-stu-id="c6cdc-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="c6cdc-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6cdc-195">[C#]</span></span>         | <span data-ttu-id="c6cdc-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c6cdc-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="c6cdc-197">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-197">3.0</span></span>        |
| <span data-ttu-id="c6cdc-198">Página de Razor</span><span class="sxs-lookup"><span data-stu-id="c6cdc-198">Razor Page</span></span>                                   | [<span data-ttu-id="c6cdc-199">page</span><span class="sxs-lookup"><span data-stu-id="c6cdc-199">page</span></span>](#page)                   | <span data-ttu-id="c6cdc-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6cdc-200">[C#]</span></span>         | <span data-ttu-id="c6cdc-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c6cdc-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="c6cdc-202">2.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-202">2.0</span></span>        |
| <span data-ttu-id="c6cdc-203">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="c6cdc-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="c6cdc-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="c6cdc-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="c6cdc-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6cdc-205">[C#]</span></span>         | <span data-ttu-id="c6cdc-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c6cdc-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="c6cdc-207">2.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-207">2.0</span></span>        |
| <span data-ttu-id="c6cdc-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="c6cdc-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="c6cdc-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6cdc-209">[C#]</span></span>         | <span data-ttu-id="c6cdc-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c6cdc-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="c6cdc-211">2.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-211">2.0</span></span>        |
| <span data-ttu-id="c6cdc-212">Aplicación de servidor Blazor</span><span class="sxs-lookup"><span data-stu-id="c6cdc-212">Blazor Server App</span></span>                            | [<span data-ttu-id="c6cdc-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="c6cdc-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="c6cdc-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6cdc-214">[C#]</span></span>         | <span data-ttu-id="c6cdc-215">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="c6cdc-215">Web/Blazor</span></span>                            | <span data-ttu-id="c6cdc-216">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-216">3.0</span></span>        |
| <span data-ttu-id="c6cdc-217">Vacío de ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c6cdc-217">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="c6cdc-218">web</span><span class="sxs-lookup"><span data-stu-id="c6cdc-218">web</span></span>](#web)                     | <span data-ttu-id="c6cdc-219">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c6cdc-219">[C#], F#</span></span>     | <span data-ttu-id="c6cdc-220">Web/Vacío</span><span class="sxs-lookup"><span data-stu-id="c6cdc-220">Web/Empty</span></span>                             | <span data-ttu-id="c6cdc-221">1.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-221">1.0</span></span>        |
| <span data-ttu-id="c6cdc-222">Aplicación web de ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="c6cdc-222">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="c6cdc-223">mvc</span><span class="sxs-lookup"><span data-stu-id="c6cdc-223">mvc</span></span>](#web-options)             | <span data-ttu-id="c6cdc-224">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c6cdc-224">[C#], F#</span></span>     | <span data-ttu-id="c6cdc-225">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="c6cdc-225">Web/MVC</span></span>                               | <span data-ttu-id="c6cdc-226">1.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-226">1.0</span></span>        |
| <span data-ttu-id="c6cdc-227">Aplicación web de ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c6cdc-227">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="c6cdc-228">webapp, razor</span><span class="sxs-lookup"><span data-stu-id="c6cdc-228">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="c6cdc-229">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6cdc-229">[C#]</span></span>         | <span data-ttu-id="c6cdc-230">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="c6cdc-230">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="c6cdc-231">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-231">2.2, 2.0</span></span>   |
| <span data-ttu-id="c6cdc-232">ASP.NET Core con Angular</span><span class="sxs-lookup"><span data-stu-id="c6cdc-232">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="c6cdc-233">angular</span><span class="sxs-lookup"><span data-stu-id="c6cdc-233">angular</span></span>](#spa)                 | <span data-ttu-id="c6cdc-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6cdc-234">[C#]</span></span>         | <span data-ttu-id="c6cdc-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c6cdc-235">Web/MVC/SPA</span></span>                           | <span data-ttu-id="c6cdc-236">2.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-236">2.0</span></span>        |
| <span data-ttu-id="c6cdc-237">ASP.NET Core con React.js</span><span class="sxs-lookup"><span data-stu-id="c6cdc-237">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="c6cdc-238">react</span><span class="sxs-lookup"><span data-stu-id="c6cdc-238">react</span></span>](#spa)                   | <span data-ttu-id="c6cdc-239">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6cdc-239">[C#]</span></span>         | <span data-ttu-id="c6cdc-240">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c6cdc-240">Web/MVC/SPA</span></span>                           | <span data-ttu-id="c6cdc-241">2.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-241">2.0</span></span>        |
| <span data-ttu-id="c6cdc-242">ASP.NET Core con React.js y Redux</span><span class="sxs-lookup"><span data-stu-id="c6cdc-242">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="c6cdc-243">reactredux</span><span class="sxs-lookup"><span data-stu-id="c6cdc-243">reactredux</span></span>](#reactredux)       | <span data-ttu-id="c6cdc-244">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6cdc-244">[C#]</span></span>         | <span data-ttu-id="c6cdc-245">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c6cdc-245">Web/MVC/SPA</span></span>                           | <span data-ttu-id="c6cdc-246">2.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-246">2.0</span></span>        |
| <span data-ttu-id="c6cdc-247">Biblioteca de clases de Razor</span><span class="sxs-lookup"><span data-stu-id="c6cdc-247">Razor Class Library</span></span>                          | [<span data-ttu-id="c6cdc-248">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="c6cdc-248">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="c6cdc-249">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6cdc-249">[C#]</span></span>         | <span data-ttu-id="c6cdc-250">Web/Razor/Biblioteca/Biblioteca de clases de Razor</span><span class="sxs-lookup"><span data-stu-id="c6cdc-250">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="c6cdc-251">2.1</span><span class="sxs-lookup"><span data-stu-id="c6cdc-251">2.1</span></span>        |
| <span data-ttu-id="c6cdc-252">API web de ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c6cdc-252">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="c6cdc-253">webapi</span><span class="sxs-lookup"><span data-stu-id="c6cdc-253">webapi</span></span>](#webapi)               | <span data-ttu-id="c6cdc-254">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c6cdc-254">[C#], F#</span></span>     | <span data-ttu-id="c6cdc-255">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="c6cdc-255">Web/WebAPI</span></span>                            | <span data-ttu-id="c6cdc-256">1.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-256">1.0</span></span>        |
| <span data-ttu-id="c6cdc-257">Servicio gRPC de ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c6cdc-257">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="c6cdc-258">grpc</span><span class="sxs-lookup"><span data-stu-id="c6cdc-258">grpc</span></span>](#web-others)             | <span data-ttu-id="c6cdc-259">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6cdc-259">[C#]</span></span>         | <span data-ttu-id="c6cdc-260">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="c6cdc-260">Web/gRPC</span></span>                              | <span data-ttu-id="c6cdc-261">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-261">3.0</span></span>        |
| <span data-ttu-id="c6cdc-262">Archivo dotnet gitignore</span><span class="sxs-lookup"><span data-stu-id="c6cdc-262">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="c6cdc-263">Configuración</span><span class="sxs-lookup"><span data-stu-id="c6cdc-263">Config</span></span>                                | <span data-ttu-id="c6cdc-264">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-264">3.0</span></span>        |
| <span data-ttu-id="c6cdc-265">archivo global.json</span><span class="sxs-lookup"><span data-stu-id="c6cdc-265">global.json file</span></span>                             | [<span data-ttu-id="c6cdc-266">globaljson</span><span class="sxs-lookup"><span data-stu-id="c6cdc-266">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="c6cdc-267">Configuración</span><span class="sxs-lookup"><span data-stu-id="c6cdc-267">Config</span></span>                                | <span data-ttu-id="c6cdc-268">2.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-268">2.0</span></span>        |
| <span data-ttu-id="c6cdc-269">Configuración de NuGet</span><span class="sxs-lookup"><span data-stu-id="c6cdc-269">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="c6cdc-270">Configuración</span><span class="sxs-lookup"><span data-stu-id="c6cdc-270">Config</span></span>                                | <span data-ttu-id="c6cdc-271">1.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-271">1.0</span></span>        |
| <span data-ttu-id="c6cdc-272">Archivo de manifiesto de la herramienta local dotnet</span><span class="sxs-lookup"><span data-stu-id="c6cdc-272">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="c6cdc-273">Configuración</span><span class="sxs-lookup"><span data-stu-id="c6cdc-273">Config</span></span>                                | <span data-ttu-id="c6cdc-274">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-274">3.0</span></span>        |
| <span data-ttu-id="c6cdc-275">Configuración web</span><span class="sxs-lookup"><span data-stu-id="c6cdc-275">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="c6cdc-276">Configuración</span><span class="sxs-lookup"><span data-stu-id="c6cdc-276">Config</span></span>                                | <span data-ttu-id="c6cdc-277">1.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-277">1.0</span></span>        |
| <span data-ttu-id="c6cdc-278">Archivo de solución</span><span class="sxs-lookup"><span data-stu-id="c6cdc-278">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="c6cdc-279">Soluciones</span><span class="sxs-lookup"><span data-stu-id="c6cdc-279">Solution</span></span>                              | <span data-ttu-id="c6cdc-280">1.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-280">1.0</span></span>        |
| <span data-ttu-id="c6cdc-281">Archivo de búfer de protocolo</span><span class="sxs-lookup"><span data-stu-id="c6cdc-281">Protocol Buffer File</span></span>                         | [<span data-ttu-id="c6cdc-282">proto</span><span class="sxs-lookup"><span data-stu-id="c6cdc-282">proto</span></span>](#namespace)             |              | <span data-ttu-id="c6cdc-283">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="c6cdc-283">Web/gRPC</span></span>                              | <span data-ttu-id="c6cdc-284">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-284">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="c6cdc-285">Opciones</span><span class="sxs-lookup"><span data-stu-id="c6cdc-285">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="c6cdc-286">Muestra un resumen de lo que sucedería si se ejecutara el comando determinado y el resultado fuera la creación de una plantilla.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-286">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="c6cdc-287">Disponible a partir del SDK de .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-287">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="c6cdc-288">Fuerza la generación de contenido incluso aunque se vayan a cambiar los archivos existentes.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-288">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="c6cdc-289">Es necesario si la plantilla elegida invalidará los archivos existentes en el directorio de salida.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-289">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c6cdc-290">Imprime la ayuda para el comando.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-290">Prints out help for the command.</span></span> <span data-ttu-id="c6cdc-291">Puede invocarse para el propio comando `dotnet new` o para cualquier plantilla.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-291">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="c6cdc-292">Por ejemplo: `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-292">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="c6cdc-293">Instala un paquete de plantillas desde los parámetros `PATH` o `NUGET_ID` proporcionados.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-293">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c6cdc-294">Si quiere instalar una versión preliminar de un paquete de plantilla, tendrá que especificar la versión en el formato de `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-294">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="c6cdc-295">De forma predeterminada, `dotnet new` pasa \* para la versión, que representa la última versión estable del paquete.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-295">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="c6cdc-296">Vea un ejemplo en la sección [Ejemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="c6cdc-296">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="c6cdc-297">Si ya hay instalada una versión de la plantilla al ejecutar este comando, la plantilla se actualizará a la versión especificada o a la versión estable más reciente si no se ha especificado ninguna versión.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-297">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="c6cdc-298">Para obtener información sobre cómo crear plantillas personalizadas, consulte [Plantillas personalizadas para dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="c6cdc-298">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="c6cdc-299">Muestra las plantillas que contienen el nombre especificado.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-299">Lists templates containing the specified name.</span></span> <span data-ttu-id="c6cdc-300">Si no se especifica ningún nombre, enumera todas las plantillas.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-300">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="c6cdc-301">El lenguaje de la plantilla que se va a crear.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-301">The language of the template to create.</span></span> <span data-ttu-id="c6cdc-302">El lenguaje aceptado cambia según la plantilla (vea los valores predeterminados en la sección [argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="c6cdc-302">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c6cdc-303">No es válido para algunas plantillas.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-303">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="c6cdc-304">Algunos shells interpretan `#` como un carácter especial.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-304">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c6cdc-305">En esos casos, incluya el valor del parámetro de lenguaje entre comillas.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-305">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="c6cdc-306">Por ejemplo: `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-306">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="c6cdc-307">El nombre de la salida creada.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-307">The name for the created output.</span></span> <span data-ttu-id="c6cdc-308">Si no se especifica ningún nombre, se usa el nombre del directorio actual.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-308">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="c6cdc-309">Especifica un origen de NuGet para usarlo durante la instalación.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-309">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="c6cdc-310">Disponible a partir del SDK de .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-310">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="c6cdc-311">La ubicación para colocar la salida generada.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-311">Location to place the generated output.</span></span> <span data-ttu-id="c6cdc-312">El valor predeterminado es el directorio actual.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-312">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="c6cdc-313">Filtra plantillas en función de los tipos disponibles.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-313">Filters templates based on available types.</span></span> <span data-ttu-id="c6cdc-314">Los valores predefinidos son `project`, `item` y `other`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-314">Predefined values are `project`, `item`, and `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="c6cdc-315">Desinstala un paquete de plantillas en los parámetros `PATH` o `NUGET_ID` proporcionados.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-315">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c6cdc-316">Si no se especifica el valor `<PATH|NUGET_ID>`, se muestran todos los paquetes de plantillas instalados actualmente y sus plantillas asociadas.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-316">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="c6cdc-317">Al especificar `NUGET_ID`, no incluya el número de versión.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-317">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="c6cdc-318">Si no especifica un parámetro en esta opción, el comando muestra las plantillas instaladas y detalles sobre ellas.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-318">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="c6cdc-319">Para desinstalar una plantilla mediante `PATH`, debe usar el nombre completo de la ruta de acceso.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-319">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="c6cdc-320">Por ejemplo, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, pero *./GarciaSoftware.ConsoleTemplate.CSharp* desde la carpeta contenedora no lo hará.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-320">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="c6cdc-321">No incluya ninguna barra diagonal para finalizar el directorio en la ruta de acceso a la plantilla.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-321">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="c6cdc-322">Comprueba si hay actualizaciones disponibles de los paquetes de plantillas instalados actualmente y las instala.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-322">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="c6cdc-323">Disponible desde el SDK de .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-323">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="c6cdc-324">Comprueba si hay actualizaciones disponibles de los paquetes de plantillas instalados actualmente.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-324">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="c6cdc-325">Disponible desde el SDK de .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-325">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="c6cdc-326">Opciones de plantilla</span><span class="sxs-lookup"><span data-stu-id="c6cdc-326">Template options</span></span>

<span data-ttu-id="c6cdc-327">Cada plantilla de proyecto puede tener opciones adicionales disponibles.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-327">Each project template may have additional options available.</span></span> <span data-ttu-id="c6cdc-328">Las plantillas principales tienen las siguientes opciones adicionales:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-328">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="c6cdc-329">consola</span><span class="sxs-lookup"><span data-stu-id="c6cdc-329">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c6cdc-330">Especifica el [marco](../../standard/frameworks.md) de destino.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-330">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6cdc-331">Disponible desde el SDK de .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-331">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="c6cdc-332">En la tabla siguiente se enumeran los valores predeterminados según el número de versión del SDK que esté usando:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-332">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c6cdc-333">Versión del SDK</span><span class="sxs-lookup"><span data-stu-id="c6cdc-333">SDK version</span></span> | <span data-ttu-id="c6cdc-334">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="c6cdc-334">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c6cdc-335">3.1</span><span class="sxs-lookup"><span data-stu-id="c6cdc-335">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c6cdc-336">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-336">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c6cdc-337">Establece la propiedad `LangVersion` en el archivo del proyecto creado.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-337">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c6cdc-338">Por ejemplo, use `--langVersion 7.3` para emplear C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-338">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="c6cdc-339">No es compatible con F#.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-339">Not supported for F#.</span></span> <span data-ttu-id="c6cdc-340">Disponible a partir del SDK de .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-340">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c6cdc-341">Para obtener una lista de las versiones predeterminadas de C#, vea [Valores predeterminados](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="c6cdc-341">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c6cdc-342">Si se especifica, no se ejecuta ninguna restauración implícita durante la creación del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-342">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="c6cdc-343">Disponible a partir del SDK de .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-343">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="c6cdc-344">classlib</span><span class="sxs-lookup"><span data-stu-id="c6cdc-344">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c6cdc-345">Especifica el [marco](../../standard/frameworks.md) de destino.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-345">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6cdc-346">Valores: `netcoreapp<version>` para crear una biblioteca de clases de .NET Core o `netstandard<version>` para crear una biblioteca de clases de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-346">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="c6cdc-347">El valor predeterminado es `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-347">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c6cdc-348">Establece la propiedad `LangVersion` en el archivo del proyecto creado.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-348">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c6cdc-349">Por ejemplo, use `--langVersion 7.3` para emplear C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-349">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="c6cdc-350">No es compatible con F#.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-350">Not supported for F#.</span></span> <span data-ttu-id="c6cdc-351">Disponible a partir del SDK de .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-351">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c6cdc-352">Para obtener una lista de las versiones predeterminadas de C#, vea [Valores predeterminados](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="c6cdc-352">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c6cdc-353">No se ejecuta ninguna restauración implícita durante la creación del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-353">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="c6cdc-354">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="c6cdc-354">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c6cdc-355">Especifica el [marco](../../standard/frameworks.md) de destino.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-355">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6cdc-356">El valor predeterminado es `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-356">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="c6cdc-357">Disponible a partir del SDK de .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-357">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c6cdc-358">Establece la propiedad `LangVersion` en el archivo del proyecto creado.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-358">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c6cdc-359">Por ejemplo, use `--langVersion 7.3` para emplear C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-359">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="c6cdc-360">Para obtener una lista de las versiones predeterminadas de C#, vea [Valores predeterminados](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="c6cdc-360">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c6cdc-361">No se ejecuta ninguna restauración implícita durante la creación del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-361">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="c6cdc-362">winforms, winformslib</span><span class="sxs-lookup"><span data-stu-id="c6cdc-362">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c6cdc-363">Establece la propiedad `LangVersion` en el archivo del proyecto creado.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-363">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c6cdc-364">Por ejemplo, use `--langVersion 7.3` para emplear C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-364">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="c6cdc-365">Para obtener una lista de las versiones predeterminadas de C#, vea [Valores predeterminados](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="c6cdc-365">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c6cdc-366">No se ejecuta ninguna restauración implícita durante la creación del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-366">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="c6cdc-367">worker, grpc</span><span class="sxs-lookup"><span data-stu-id="c6cdc-367">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c6cdc-368">Especifica el [marco](../../standard/frameworks.md) de destino.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-368">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6cdc-369">El valor predeterminado es `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-369">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="c6cdc-370">Disponible a partir del SDK de .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-370">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c6cdc-371">Excluye *launchSettings.json* de la plantilla generada.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-371">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c6cdc-372">No se ejecuta ninguna restauración implícita durante la creación del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-372">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="c6cdc-373">mstest, xunit</span><span class="sxs-lookup"><span data-stu-id="c6cdc-373">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c6cdc-374">Especifica el [marco](../../standard/frameworks.md) de destino.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-374">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6cdc-375">Opción disponible a partir del SDK de .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-375">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="c6cdc-376">En la tabla siguiente se enumeran los valores predeterminados según el número de versión del SDK que esté usando:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-376">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c6cdc-377">Versión del SDK</span><span class="sxs-lookup"><span data-stu-id="c6cdc-377">SDK version</span></span> | <span data-ttu-id="c6cdc-378">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="c6cdc-378">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c6cdc-379">3.1</span><span class="sxs-lookup"><span data-stu-id="c6cdc-379">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c6cdc-380">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-380">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="c6cdc-381">Habilita el empaquetado del proyecto mediante [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c6cdc-381">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c6cdc-382">No se ejecuta ninguna restauración implícita durante la creación del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-382">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="c6cdc-383">nunit</span><span class="sxs-lookup"><span data-stu-id="c6cdc-383">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c6cdc-384">Especifica el [marco](../../standard/frameworks.md) de destino.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-384">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="c6cdc-385">En la tabla siguiente se enumeran los valores predeterminados según el número de versión del SDK que esté usando:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-385">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c6cdc-386">Versión del SDK</span><span class="sxs-lookup"><span data-stu-id="c6cdc-386">SDK version</span></span> | <span data-ttu-id="c6cdc-387">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="c6cdc-387">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c6cdc-388">3.1</span><span class="sxs-lookup"><span data-stu-id="c6cdc-388">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c6cdc-389">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-389">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c6cdc-390">2.2</span><span class="sxs-lookup"><span data-stu-id="c6cdc-390">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="c6cdc-391">2.1</span><span class="sxs-lookup"><span data-stu-id="c6cdc-391">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="c6cdc-392">Habilita el empaquetado del proyecto mediante [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c6cdc-392">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c6cdc-393">No se ejecuta ninguna restauración implícita durante la creación del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-393">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="c6cdc-394">página</span><span class="sxs-lookup"><span data-stu-id="c6cdc-394">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="c6cdc-395">Espacio de nombres del código generado.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-395">Namespace for the generated code.</span></span> <span data-ttu-id="c6cdc-396">El valor predeterminado es `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-396">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="c6cdc-397">Crea la página sin PageModel.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-397">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="c6cdc-398">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="c6cdc-398">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="c6cdc-399">Espacio de nombres del código generado.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-399">Namespace for the generated code.</span></span> <span data-ttu-id="c6cdc-400">El valor predeterminado es `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-400">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="c6cdc-401">blazorserver</span><span class="sxs-lookup"><span data-stu-id="c6cdc-401">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="c6cdc-402">Tipo de autenticación que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-402">The type of authentication to use.</span></span> <span data-ttu-id="c6cdc-403">Los valores posibles son:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-403">The possible values are:</span></span>

  - <span data-ttu-id="c6cdc-404">`None`: sin autenticación (valor predeterminado).</span><span class="sxs-lookup"><span data-stu-id="c6cdc-404">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c6cdc-405">`Individual`: autenticación individual.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-405">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="c6cdc-406">`IndividualB2C`: autenticación individual con Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-406">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="c6cdc-407">`SingleOrg`: autenticación organizativa para un solo inquilino.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-407">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="c6cdc-408">`MultiOrg`: autenticación organizativa para varios inquilinos.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-408">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="c6cdc-409">`Windows`: autenticación de Windows.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-409">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="c6cdc-410">Instancia de Azure Active Directory B2C con la que se realiza la conexión.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-410">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c6cdc-411">Úsela con la autenticación `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-411">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6cdc-412">El valor predeterminado es `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-412">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="c6cdc-413">Identificador de la directiva de registro e inicio de sesión de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-413">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c6cdc-414">Úsela con la autenticación `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-414">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="c6cdc-415">Identificador de la directiva de restablecimiento de contraseñas de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-415">The reset password policy ID for this project.</span></span> <span data-ttu-id="c6cdc-416">Úsela con la autenticación `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-416">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="c6cdc-417">Identificador de la directiva de edición de perfiles de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-417">The edit profile policy ID for this project.</span></span> <span data-ttu-id="c6cdc-418">Úsela con la autenticación `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-418">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="c6cdc-419">Instancia de Azure Active Directory con la que se realiza la conexión.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-419">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c6cdc-420">Úsela con las autenticaciones `SingleOrg` o `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-420">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c6cdc-421">El valor predeterminado es `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-421">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="c6cdc-422">Identificador de cliente de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-422">The Client ID for this project.</span></span> <span data-ttu-id="c6cdc-423">Úsela con las autenticaciones `IndividualB2C`, `SingleOrg` o `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-423">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c6cdc-424">El valor predeterminado es `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-424">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="c6cdc-425">Dominio del inquilino del directorio.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-425">The domain for the directory tenant.</span></span> <span data-ttu-id="c6cdc-426">Úsela con las autenticaciones `SingleOrg` o `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-426">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6cdc-427">El valor predeterminado es `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-427">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="c6cdc-428">Identificador de inquilino del directorio con el que se realiza la conexión.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-428">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c6cdc-429">Úsela con la autenticación `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-429">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c6cdc-430">El valor predeterminado es `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-430">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="c6cdc-431">Ruta de acceso de solicitud de la ruta de acceso de la base de la aplicación del URI de redirección.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-431">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c6cdc-432">Úsela con las autenticaciones `SingleOrg` o `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-432">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6cdc-433">El valor predeterminado es `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-433">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="c6cdc-434">Concede a esta aplicación acceso de lectura al directorio.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-434">Allows this application read-access to the directory.</span></span> <span data-ttu-id="c6cdc-435">Solo se aplica a las autenticaciones `SingleOrg` y `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-435">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c6cdc-436">Excluye *launchSettings.json* de la plantilla generada.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-436">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="c6cdc-437">Desactiva HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-437">Turns off HTTPS.</span></span> <span data-ttu-id="c6cdc-438">Esta opción solo se aplica si no se usan `Individual`, `IndividualB2C`, `SingleOrg` o `MultiOrg` en `--auth`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-438">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c6cdc-439">Especifica que se debería usar LocalDB en vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-439">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c6cdc-440">Solo se aplica a las autenticaciones `Individual` y `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-440">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c6cdc-441">No se ejecuta ninguna restauración implícita durante la creación del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-441">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="c6cdc-442">web</span><span class="sxs-lookup"><span data-stu-id="c6cdc-442">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c6cdc-443">Excluye *launchSettings.json* de la plantilla generada.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-443">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c6cdc-444">Especifica el [marco](../../standard/frameworks.md) de destino.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-444">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6cdc-445">Opción no disponible en el SDK de .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-445">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c6cdc-446">En la tabla siguiente se enumeran los valores predeterminados según el número de versión del SDK que esté usando:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-446">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c6cdc-447">Versión del SDK</span><span class="sxs-lookup"><span data-stu-id="c6cdc-447">SDK version</span></span> | <span data-ttu-id="c6cdc-448">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="c6cdc-448">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c6cdc-449">3.1</span><span class="sxs-lookup"><span data-stu-id="c6cdc-449">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c6cdc-450">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-450">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c6cdc-451">2.1</span><span class="sxs-lookup"><span data-stu-id="c6cdc-451">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="c6cdc-452">No se ejecuta ninguna restauración implícita durante la creación del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-452">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="c6cdc-453">Desactiva HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-453">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="c6cdc-454">mvc, webapp</span><span class="sxs-lookup"><span data-stu-id="c6cdc-454">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="c6cdc-455">Tipo de autenticación que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-455">The type of authentication to use.</span></span> <span data-ttu-id="c6cdc-456">Los valores posibles son:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-456">The possible values are:</span></span>

  - <span data-ttu-id="c6cdc-457">`None`: sin autenticación (valor predeterminado).</span><span class="sxs-lookup"><span data-stu-id="c6cdc-457">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c6cdc-458">`Individual`: autenticación individual.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-458">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="c6cdc-459">`IndividualB2C`: autenticación individual con Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-459">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="c6cdc-460">`SingleOrg`: autenticación organizativa para un solo inquilino.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-460">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="c6cdc-461">`MultiOrg`: autenticación organizativa para varios inquilinos.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-461">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="c6cdc-462">`Windows`: autenticación de Windows.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-462">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="c6cdc-463">Instancia de Azure Active Directory B2C con la que se realiza la conexión.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-463">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c6cdc-464">Úsela con la autenticación `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-464">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6cdc-465">El valor predeterminado es `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-465">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="c6cdc-466">Identificador de la directiva de registro e inicio de sesión de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-466">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c6cdc-467">Úsela con la autenticación `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-467">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="c6cdc-468">Identificador de la directiva de restablecimiento de contraseñas de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-468">The reset password policy ID for this project.</span></span> <span data-ttu-id="c6cdc-469">Úsela con la autenticación `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-469">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="c6cdc-470">Identificador de la directiva de edición de perfiles de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-470">The edit profile policy ID for this project.</span></span> <span data-ttu-id="c6cdc-471">Úsela con la autenticación `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-471">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="c6cdc-472">Instancia de Azure Active Directory con la que se realiza la conexión.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-472">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c6cdc-473">Úsela con las autenticaciones `SingleOrg` o `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-473">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c6cdc-474">El valor predeterminado es `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-474">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="c6cdc-475">Identificador de cliente de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-475">The Client ID for this project.</span></span> <span data-ttu-id="c6cdc-476">Úsela con las autenticaciones `IndividualB2C`, `SingleOrg` o `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-476">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c6cdc-477">El valor predeterminado es `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-477">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="c6cdc-478">Dominio del inquilino del directorio.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-478">The domain for the directory tenant.</span></span> <span data-ttu-id="c6cdc-479">Úsela con las autenticaciones `SingleOrg` o `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-479">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6cdc-480">El valor predeterminado es `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-480">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="c6cdc-481">Identificador de inquilino del directorio con el que se realiza la conexión.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-481">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c6cdc-482">Úsela con la autenticación `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-482">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c6cdc-483">El valor predeterminado es `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-483">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="c6cdc-484">Ruta de acceso de solicitud de la ruta de acceso de la base de la aplicación del URI de redirección.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-484">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c6cdc-485">Úsela con las autenticaciones `SingleOrg` o `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-485">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6cdc-486">El valor predeterminado es `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-486">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="c6cdc-487">Concede a esta aplicación acceso de lectura al directorio.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-487">Allows this application read-access to the directory.</span></span> <span data-ttu-id="c6cdc-488">Solo se aplica a las autenticaciones `SingleOrg` y `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-488">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c6cdc-489">Excluye *launchSettings.json* de la plantilla generada.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-489">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="c6cdc-490">Desactiva HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-490">Turns off HTTPS.</span></span> <span data-ttu-id="c6cdc-491">Esta opción solo se aplica si no se usan `Individual`, `IndividualB2C`, `SingleOrg` o `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-491">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c6cdc-492">Especifica que se debería usar LocalDB en vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-492">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c6cdc-493">Solo se aplica a las autenticaciones `Individual` y `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-493">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c6cdc-494">Especifica el [marco](../../standard/frameworks.md) de destino.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-494">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6cdc-495">Opción disponible a partir del SDK de .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-495">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="c6cdc-496">En la tabla siguiente se enumeran los valores predeterminados según el número de versión del SDK que esté usando:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-496">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c6cdc-497">Versión del SDK</span><span class="sxs-lookup"><span data-stu-id="c6cdc-497">SDK version</span></span> | <span data-ttu-id="c6cdc-498">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="c6cdc-498">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c6cdc-499">3.1</span><span class="sxs-lookup"><span data-stu-id="c6cdc-499">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c6cdc-500">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-500">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="c6cdc-501">No se ejecuta ninguna restauración implícita durante la creación del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-501">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="c6cdc-502">Incluye BrowserLink en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-502">Includes BrowserLink in the project.</span></span> <span data-ttu-id="c6cdc-503">Opción no disponible en el SDK de .NET Core 2.2 y 3.1.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-503">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="c6cdc-504">Determina si el proyecto está configurado para usar la [compilación en tiempo de ejecución de Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) en las compilaciones de depuración.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-504">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="c6cdc-505">Opción disponible a partir del SDK de .NET Core 3.1.201.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-505">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="c6cdc-506">angular, react</span><span class="sxs-lookup"><span data-stu-id="c6cdc-506">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="c6cdc-507">Tipo de autenticación que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-507">The type of authentication to use.</span></span> <span data-ttu-id="c6cdc-508">Disponible desde el SDK de .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-508">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="c6cdc-509">Los valores posibles son:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-509">The possible values are:</span></span>

  - <span data-ttu-id="c6cdc-510">`None`: sin autenticación (valor predeterminado).</span><span class="sxs-lookup"><span data-stu-id="c6cdc-510">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c6cdc-511">`Individual`: autenticación individual.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-511">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c6cdc-512">Excluye *launchSettings.json* de la plantilla generada.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-512">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c6cdc-513">No se ejecuta ninguna restauración implícita durante la creación del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-513">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="c6cdc-514">Desactiva HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-514">Turns off HTTPS.</span></span> <span data-ttu-id="c6cdc-515">Esta opción solo se aplica si la autenticación es `None`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-515">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c6cdc-516">Especifica que se debería usar LocalDB en vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-516">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c6cdc-517">Solo se aplica a las autenticaciones `Individual` y `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-517">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6cdc-518">Disponible desde el SDK de .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-518">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c6cdc-519">Especifica el [marco](../../standard/frameworks.md) de destino.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-519">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6cdc-520">Opción no disponible en el SDK de .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-520">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c6cdc-521">En la tabla siguiente se enumeran los valores predeterminados según el número de versión del SDK que esté usando:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-521">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c6cdc-522">Versión del SDK</span><span class="sxs-lookup"><span data-stu-id="c6cdc-522">SDK version</span></span> | <span data-ttu-id="c6cdc-523">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="c6cdc-523">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c6cdc-524">3.1</span><span class="sxs-lookup"><span data-stu-id="c6cdc-524">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c6cdc-525">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-525">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c6cdc-526">2.1</span><span class="sxs-lookup"><span data-stu-id="c6cdc-526">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="c6cdc-527">reactredux</span><span class="sxs-lookup"><span data-stu-id="c6cdc-527">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c6cdc-528">Excluye *launchSettings.json* de la plantilla generada.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-528">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c6cdc-529">Especifica el [marco](../../standard/frameworks.md) de destino.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-529">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6cdc-530">Opción no disponible en el SDK de .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-530">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c6cdc-531">En la tabla siguiente se enumeran los valores predeterminados según el número de versión del SDK que esté usando:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-531">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c6cdc-532">Versión del SDK</span><span class="sxs-lookup"><span data-stu-id="c6cdc-532">SDK version</span></span> | <span data-ttu-id="c6cdc-533">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="c6cdc-533">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c6cdc-534">3.1</span><span class="sxs-lookup"><span data-stu-id="c6cdc-534">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c6cdc-535">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-535">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c6cdc-536">2.1</span><span class="sxs-lookup"><span data-stu-id="c6cdc-536">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="c6cdc-537">No se ejecuta ninguna restauración implícita durante la creación del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-537">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="c6cdc-538">Desactiva HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-538">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="c6cdc-539">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="c6cdc-539">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="c6cdc-540">No se ejecuta ninguna restauración implícita durante la creación del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-540">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="c6cdc-541">Permite agregar vistas y páginas de Razor tradicionales además de los componentes a esta biblioteca.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-541">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="c6cdc-542">Disponible desde el SDK de .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-542">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="c6cdc-543">webapi</span><span class="sxs-lookup"><span data-stu-id="c6cdc-543">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="c6cdc-544">Tipo de autenticación que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-544">The type of authentication to use.</span></span> <span data-ttu-id="c6cdc-545">Los valores posibles son:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-545">The possible values are:</span></span>

  - <span data-ttu-id="c6cdc-546">`None`: sin autenticación (valor predeterminado).</span><span class="sxs-lookup"><span data-stu-id="c6cdc-546">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c6cdc-547">`IndividualB2C`: autenticación individual con Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-547">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="c6cdc-548">`SingleOrg`: autenticación organizativa para un solo inquilino.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-548">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="c6cdc-549">`Windows`: autenticación de Windows.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-549">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="c6cdc-550">Instancia de Azure Active Directory B2C con la que se realiza la conexión.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-550">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c6cdc-551">Úsela con la autenticación `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-551">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6cdc-552">El valor predeterminado es `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-552">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="c6cdc-553">Identificador de la directiva de registro e inicio de sesión de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-553">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c6cdc-554">Úsela con la autenticación `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-554">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="c6cdc-555">Instancia de Azure Active Directory con la que se realiza la conexión.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-555">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c6cdc-556">Úsela con la autenticación `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-556">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c6cdc-557">El valor predeterminado es `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-557">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="c6cdc-558">Identificador de cliente de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-558">The Client ID for this project.</span></span> <span data-ttu-id="c6cdc-559">Úsela con las autenticaciones `IndividualB2C` o `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-559">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c6cdc-560">El valor predeterminado es `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-560">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="c6cdc-561">Dominio del inquilino del directorio.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-561">The domain for the directory tenant.</span></span> <span data-ttu-id="c6cdc-562">Úsela con las autenticaciones `IndividualB2C` o `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-562">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c6cdc-563">El valor predeterminado es `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-563">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="c6cdc-564">Identificador de inquilino del directorio con el que se realiza la conexión.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-564">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c6cdc-565">Úsela con la autenticación `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-565">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c6cdc-566">El valor predeterminado es `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-566">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="c6cdc-567">Concede a esta aplicación acceso de lectura al directorio.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-567">Allows this application read-access to the directory.</span></span> <span data-ttu-id="c6cdc-568">Solo se aplica a la autenticación `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-568">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c6cdc-569">Excluye *launchSettings.json* de la plantilla generada.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-569">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="c6cdc-570">Desactiva HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-570">Turns off HTTPS.</span></span> <span data-ttu-id="c6cdc-571">`app.UseHsts` y `app.UseHttpsRedirection` no se agregan a `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-571">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="c6cdc-572">Esta opción solo se aplica si no se usan `IndividualB2C` o `SingleOrg` en la autenticación.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-572">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c6cdc-573">Especifica que se debería usar LocalDB en vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-573">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c6cdc-574">Solo se aplica a la autenticación `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-574">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c6cdc-575">Especifica el [marco](../../standard/frameworks.md) de destino.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-575">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6cdc-576">Opción no disponible en el SDK de .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-576">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c6cdc-577">En la tabla siguiente se enumeran los valores predeterminados según el número de versión del SDK que esté usando:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-577">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c6cdc-578">Versión del SDK</span><span class="sxs-lookup"><span data-stu-id="c6cdc-578">SDK version</span></span> | <span data-ttu-id="c6cdc-579">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="c6cdc-579">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c6cdc-580">3.1</span><span class="sxs-lookup"><span data-stu-id="c6cdc-580">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c6cdc-581">3.0</span><span class="sxs-lookup"><span data-stu-id="c6cdc-581">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c6cdc-582">2.1</span><span class="sxs-lookup"><span data-stu-id="c6cdc-582">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="c6cdc-583">No se ejecuta ninguna restauración implícita durante la creación del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-583">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="c6cdc-584">globaljson</span><span class="sxs-lookup"><span data-stu-id="c6cdc-584">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="c6cdc-585">Especifica la versión del SDK de .NET Core que se usará en el archivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-585">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="c6cdc-586">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="c6cdc-586">Examples</span></span>

- <span data-ttu-id="c6cdc-587">Creación de un proyecto de aplicación de consola de C# mediante la especificación del nombre de plantilla:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-587">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="c6cdc-588">Creación de un proyecto de aplicación de consola con F# en el directorio actual:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-588">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="c6cdc-589">Creación de un proyecto de biblioteca de clases de .NET Standard en el directorio especificado:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-589">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="c6cdc-590">Creación de un proyecto MVC de ASP.NET Core C# en el directorio actual sin autenticación:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-590">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="c6cdc-591">Creación de un proyecto de xUnit:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-591">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="c6cdc-592">Enumeración de todas las plantillas disponibles en las plantillas de aplicación de página única (SPA):</span><span class="sxs-lookup"><span data-stu-id="c6cdc-592">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="c6cdc-593">Enumeración de todas las plantillas que coinciden con la subcadena *we*.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-593">List all templates matching the *we* substring.</span></span> <span data-ttu-id="c6cdc-594">No se encuentra ninguna coincidencia exacta, por lo que se ejecuta la coincidencia de subcadena con las columnas de nombre corto y de nombre.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-594">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="c6cdc-595">Intento de invocar a la plantilla que coincide con *ng*.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-595">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="c6cdc-596">Si no se puede determinar una única coincidencia, se enumeran las plantillas que son coincidencias parciales.</span><span class="sxs-lookup"><span data-stu-id="c6cdc-596">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="c6cdc-597">Instalación de la versión 2.0 de las plantillas de SPA de ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-597">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="c6cdc-598">Enumeración de las plantillas instaladas y detalles sobre ellas, incluido cómo desinstalarlas:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-598">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="c6cdc-599">Creación de un archivo *global.json* en el directorio actual al establecer la versión del SDK en 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="c6cdc-599">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="c6cdc-600">Vea también</span><span class="sxs-lookup"><span data-stu-id="c6cdc-600">See also</span></span>

- [<span data-ttu-id="c6cdc-601">Plantillas personalizadas para dotnet new</span><span class="sxs-lookup"><span data-stu-id="c6cdc-601">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="c6cdc-602">Creación de una plantilla personalizada para dotnet new</span><span class="sxs-lookup"><span data-stu-id="c6cdc-602">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="c6cdc-603">Repositorio de GitHub dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="c6cdc-603">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- <span data-ttu-id="c6cdc-604">[Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) (Plantillas disponibles para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="c6cdc-604">[Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)</span></span>

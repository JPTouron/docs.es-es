---
title: Serializar flujos de trabajo y actividades a y de XAML
description: En este artículo se proporciona información general sobre la serialización de definiciones de flujo de trabajo y el trabajo con definiciones de flujo de trabajo de XAML en Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
ms.openlocfilehash: 168dbc9a36cfa80c15fddc7481e986d1ce383adb
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421350"
---
# <a name="serialize-workflows-and-activities-to-and-from-xaml"></a><span data-ttu-id="53126-103">Serialización de flujos de trabajo y actividades desde y hacia XAML</span><span class="sxs-lookup"><span data-stu-id="53126-103">Serialize Workflows and Activities to and from XAML</span></span>

<span data-ttu-id="53126-104">Además de compilarse en tipos incluidos en ensamblados, las definiciones de flujo de trabajo también se pueden serializar en XAML.</span><span class="sxs-lookup"><span data-stu-id="53126-104">In addition to being compiled into types that are contained in assemblies, workflow definitions can also be serialized to XAML.</span></span> <span data-ttu-id="53126-105">Estas definiciones serializadas se pueden recargar para edición o inspección, pasar a un sistema de compilación para compilación, o bien cargar e invocar.</span><span class="sxs-lookup"><span data-stu-id="53126-105">These serialized definitions can be reloaded for editing or inspection, passed to a build system for compilation, or loaded and invoked.</span></span> <span data-ttu-id="53126-106">En este tema se proporciona información general sobre la serialización de definiciones de flujo de trabajo y el trabajo con definiciones de flujo de trabajo de XAML.</span><span class="sxs-lookup"><span data-stu-id="53126-106">This topic provides an overview of serializing workflow definitions and working with XAML workflow definitions.</span></span>

## <a name="work-with-xaml-workflow-definitions"></a><span data-ttu-id="53126-107">Trabajar con definiciones de flujo de trabajo XAML</span><span class="sxs-lookup"><span data-stu-id="53126-107">Work with XAML Workflow definitions</span></span>

<span data-ttu-id="53126-108">Para crear una definición de flujo de trabajo para la serialización, se utiliza la clase <xref:System.Activities.ActivityBuilder>.</span><span class="sxs-lookup"><span data-stu-id="53126-108">To create a workflow definition for serialization, the <xref:System.Activities.ActivityBuilder> class is used.</span></span> <span data-ttu-id="53126-109">La creación de una clase <xref:System.Activities.ActivityBuilder> es muy similar a la creación de una clase <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="53126-109">Creating an <xref:System.Activities.ActivityBuilder> is very similar to creating a <xref:System.Activities.DynamicActivity>.</span></span> <span data-ttu-id="53126-110">Se especifican los argumento deseados y se configuran las actividades que constituyen el comportamiento.</span><span class="sxs-lookup"><span data-stu-id="53126-110">Any desired arguments are specified, and the activities that constitute the behavior are configured.</span></span> <span data-ttu-id="53126-111">En el siguiente ejemplo, se crea una actividad `Add` que toma dos argumentos de entrada, los suma y devuelve el resultado.</span><span class="sxs-lookup"><span data-stu-id="53126-111">In the following example, an `Add` activity is created that takes two input arguments, adds them together, and returns the result.</span></span> <span data-ttu-id="53126-112">Dado que esta actividad devuelve un resultado, se utiliza la clase <xref:System.Activities.ActivityBuilder%601> la genérica.</span><span class="sxs-lookup"><span data-stu-id="53126-112">Because this activity returns a result, the generic <xref:System.Activities.ActivityBuilder%601> class is used.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#41](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]

<span data-ttu-id="53126-113">Cada una de las instancias de <xref:System.Activities.DynamicActivityProperty> representa uno de los argumentos de entrada al flujo de trabajo y la propiedad <xref:System.Activities.ActivityBuilder.Implementation%2A> contiene las actividades que constituyen la lógica del flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="53126-113">Each of the <xref:System.Activities.DynamicActivityProperty> instances represents one of the input arguments to the workflow, and the <xref:System.Activities.ActivityBuilder.Implementation%2A> contains the activities that make up the logic of the workflow.</span></span> <span data-ttu-id="53126-114">Observe que las expresiones de valor de r de este ejemplo son expresiones de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="53126-114">Note that the r-value expressions in this example are Visual Basic expressions.</span></span> <span data-ttu-id="53126-115">Las expresiones lambda no son serializables en XAML a menos que se use <xref:System.Activities.Expressions.ExpressionServices.Convert%2A>.</span><span class="sxs-lookup"><span data-stu-id="53126-115">Lambda expressions are not serializable to XAML unless <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> is used.</span></span> <span data-ttu-id="53126-116">Si los flujos de trabajo serializados están diseñados para abrirse o editarse en el diseñador de flujo de trabajo, se deben usar Visual Basic expresiones.</span><span class="sxs-lookup"><span data-stu-id="53126-116">If the serialized workflows are intended to be opened or edited in the workflow designer, then Visual Basic expressions should be used.</span></span> <span data-ttu-id="53126-117">Para obtener más información, vea [crear flujos de trabajo, actividades y expresiones mediante código imperativo](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="53126-117">For more information, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>

<span data-ttu-id="53126-118">Para serializar la definición de flujo de trabajo representada por la instancia de <xref:System.Activities.ActivityBuilder> en XAML, use <xref:System.Activities.XamlIntegration.ActivityXamlServices> para crear <xref:System.Xaml.XamlWriter> y use después <xref:System.Xaml.XamlServices> para serializar la definición de flujo de trabajo mediante <xref:System.Xaml.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="53126-118">To serialize the workflow definition represented by the <xref:System.Activities.ActivityBuilder> instance to XAML, use <xref:System.Activities.XamlIntegration.ActivityXamlServices> to create a <xref:System.Xaml.XamlWriter>, and then use <xref:System.Xaml.XamlServices> to serialize the workflow definition by using the <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="53126-119"><xref:System.Activities.XamlIntegration.ActivityXamlServices>tiene métodos para asignar <xref:System.Activities.ActivityBuilder> instancias a y desde XAML, y para cargar flujos de trabajo de XAML y devolver un <xref:System.Activities.DynamicActivity> que se pueda invocar.</span><span class="sxs-lookup"><span data-stu-id="53126-119"><xref:System.Activities.XamlIntegration.ActivityXamlServices> has methods to map <xref:System.Activities.ActivityBuilder> instances to and from XAML and to load XAML workflows and return a <xref:System.Activities.DynamicActivity> that can be invoked.</span></span> <span data-ttu-id="53126-120">En el ejemplo siguiente, la <xref:System.Activities.ActivityBuilder> instancia del ejemplo anterior se serializa en una cadena y se guarda en un archivo.</span><span class="sxs-lookup"><span data-stu-id="53126-120">In the following example, the <xref:System.Activities.ActivityBuilder> instance from the previous example is serialized to a string and saved to a file.</span></span>

```csharp
// Serialize the workflow to XAML and store it in a string.
StringBuilder sb = new StringBuilder();
StringWriter tw = new StringWriter(sb);
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(tw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
string serializedAB = sb.ToString();

// Display the XAML to the console.
Console.WriteLine(serializedAB);

// Serialize the workflow to XAML and save it to a file.
StreamWriter sw = File.CreateText(@"C:\Workflows\add.xaml");
XamlWriter xw2 = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw2, ab);
sw.Close();
```

<span data-ttu-id="53126-121">En el siguiente ejemplo se representa el flujo de trabajo serializado.</span><span class="sxs-lookup"><span data-stu-id="53126-121">The following example represents the serialized workflow.</span></span>

```xaml
<Activity
  x:TypeArguments="x:Int32"
  x:Class="Add"
  xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
  <x:Members>
    <x:Property Name="Operand1" Type="InArgument(x:Int32)" />
    <x:Property Name="Operand2" Type="InArgument(x:Int32)" />
  </x:Members>
  <Sequence>
    <WriteLine Text="[Operand1.ToString() + " + " + Operand2.ToString()]" />
    <Assign x:TypeArguments="x:Int32" Value="[Operand1 + Operand2]">
      <Assign.To>
        <OutArgument x:TypeArguments="x:Int32">
          <ArgumentReference x:TypeArguments="x:Int32" ArgumentName="Result" />
          </OutArgument>
      </Assign.To>
    </Assign>
  </Sequence>
</Activity>
```

<span data-ttu-id="53126-122">Para cargar un flujo de trabajo serializado, use el <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> método.</span><span class="sxs-lookup"><span data-stu-id="53126-122">To load a serialized workflow, use the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="53126-123">Este método toma la definición de flujo de trabajo serializada y devuelve una clase <xref:System.Activities.DynamicActivity> que representa la definición de flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="53126-123">This takes the serialized workflow definition and returns a <xref:System.Activities.DynamicActivity> that represents the workflow definition.</span></span> <span data-ttu-id="53126-124">Observe que el XAML no se deserializa hasta que se llama al método <xref:System.Activities.Activity.CacheMetadata%2A> en el cuerpo de la clase <xref:System.Activities.DynamicActivity> durante el proceso de validación.</span><span class="sxs-lookup"><span data-stu-id="53126-124">Note that the XAML is not deserialized until <xref:System.Activities.Activity.CacheMetadata%2A> is called on the body of the <xref:System.Activities.DynamicActivity> during the validation process.</span></span> <span data-ttu-id="53126-125">Si no se llama a la validación explícitamente, se realiza cuando se invoca el flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="53126-125">If validation is not explicitly called, then it is performed when the workflow is invoked.</span></span> <span data-ttu-id="53126-126">Si la definición de flujo de trabajo de XAML no es válida, se produce una excepción <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="53126-126">If the XAML workflow definition is invalid, then an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="53126-127">Las excepciones que se producen desde el método <xref:System.Activities.Activity.CacheMetadata%2A> escapan de la llamada al método <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> y deben ser administradas por el autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="53126-127">Any exceptions thrown from <xref:System.Activities.Activity.CacheMetadata%2A> escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span> <span data-ttu-id="53126-128">En el siguiente ejemplo, el flujo de trabajo serializado del ejemplo anterior se carga y se invoca utilizando <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="53126-128">In the following example, the serialized workflow from the previous example is loaded and invoked by using <xref:System.Activities.WorkflowInvoker>.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#43](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]

<span data-ttu-id="53126-129">Cuando se invoca este flujo de trabajo, en la consola se muestra el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="53126-129">When this workflow is invoked, the following output is displayed to the console.</span></span>

<span data-ttu-id="53126-130">**25 + 15**</span><span class="sxs-lookup"><span data-stu-id="53126-130">**25 + 15**</span></span>\
<span data-ttu-id="53126-131">**40**</span><span class="sxs-lookup"><span data-stu-id="53126-131">**40**</span></span>

> [!NOTE]
> <span data-ttu-id="53126-132">Para obtener más información sobre cómo invocar flujos de trabajo con argumentos de entrada y salida, vea [usar WorkflowInvoker y WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) y <xref:System.Activities.WorkflowInvoker.Invoke%2A> .</span><span class="sxs-lookup"><span data-stu-id="53126-132">For more information about invoking workflows with input and output arguments, see [Using WorkflowInvoker and WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) and <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span>

<span data-ttu-id="53126-133">Si el flujo de trabajo serializado contiene expresiones de C#, se <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> debe pasar una instancia de con su <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> propiedad establecida en `true` como parámetro a <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType> ; de lo contrario, se <xref:System.NotSupportedException> producirá una con un mensaje similar al siguiente: el **tipo de actividad de expresión ' CSharpValue ' 1 ' requiere compilación para poder ejecutarse.  Asegúrese de que se ha compilado el flujo de trabajo.**</span><span class="sxs-lookup"><span data-stu-id="53126-133">If the serialized workflow contains C# expressions, then an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true` must be passed as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, otherwise a <xref:System.NotSupportedException> will be thrown with a message similar to the following: **Expression Activity type 'CSharpValue\`1' requires compilation in order to run.  Please ensure that the workflow has been compiled.**</span></span>

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

<span data-ttu-id="53126-134">Para obtener más información, vea [expresiones de C#](csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="53126-134">For more information, see [C# Expressions](csharp-expressions.md).</span></span>

<span data-ttu-id="53126-135">También se puede cargar una definición de flujo de trabajo serializada en una <xref:System.Activities.ActivityBuilder> instancia de mediante el <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> método.</span><span class="sxs-lookup"><span data-stu-id="53126-135">A serialized workflow definition can also be loaded into an <xref:System.Activities.ActivityBuilder> instance by using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> method.</span></span> <span data-ttu-id="53126-136">Una vez que un flujo de trabajo serializado se carga en una <xref:System.Activities.ActivityBuilder> instancia de, se puede inspeccionar y modificar.</span><span class="sxs-lookup"><span data-stu-id="53126-136">After a serialized workflow is loaded into an <xref:System.Activities.ActivityBuilder> instance, it can be inspected and modified.</span></span> <span data-ttu-id="53126-137">Esto resulta útil para los autores de diseñadores de flujo de trabajo personalizados y proporciona un mecanismo para guardar y recargar las definiciones de flujo de trabajo durante el proceso del diseño.</span><span class="sxs-lookup"><span data-stu-id="53126-137">This is useful for custom workflow designer authors and provides a mechanism for saving and reloading workflow definitions during the design process.</span></span> <span data-ttu-id="53126-138">En el siguiente ejemplo, se carga la definición de flujo de trabajo serializada del ejemplo anterior y se inspeccionan sus propiedades.</span><span class="sxs-lookup"><span data-stu-id="53126-138">In the following example, the serialized workflow definition from the previous example is loaded and its properties are inspected.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#44](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]

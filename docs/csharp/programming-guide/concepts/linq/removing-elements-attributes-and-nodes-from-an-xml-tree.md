---
title: Quitar elementos, atributos y nodos de un árbol XML (C#)
description: Aprenda a quitar elementos, atributos y nodos de un árbol XML. Vea una lista de métodos de eliminación y un ejemplo de código.
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 4e753c3d96c4cbc050b08076ca8bff8c17b2e252
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300051"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a><span data-ttu-id="4b8f0-104">Quitar elementos, atributos y nodos de un árbol XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4b8f0-104">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>

<span data-ttu-id="4b8f0-105">Puede modificar un árbol XML mediante la eliminación de elementos, atributos y otros tipos de nodos.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-105">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>

<span data-ttu-id="4b8f0-106">Quitar un elemento o un atributo de un documento XML resulta sencillo.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-106">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="4b8f0-107">Sin embargo, al quitar colecciones de elementos o atributos, primero debe materializar una colección en una lista y, a continuación, eliminar los elementos o los atributos de ésta.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-107">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="4b8f0-108">El mejor método consiste en usar el método de extensión <xref:System.Xml.Linq.Extensions.Remove%2A>, que se ocupará de todo esto.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-108">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>

<span data-ttu-id="4b8f0-109">El motivo principal radica en que la mayoría de las colecciones que se recuperan de un árbol XML se producen con una ejecución aplazada.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-109">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="4b8f0-110">Si no las materializa primero en una lista, o bien si no usa los métodos de extensión, es posible que aparezca una clase determinada de errores.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-110">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="4b8f0-111">Para obtener más información, vea [Errores en códigos declarativos/imperativos mixtos (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4b8f0-111">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>

<span data-ttu-id="4b8f0-112">Los siguientes métodos sirven para quitar nodos y atributos de un árbol XML.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-112">The following methods remove nodes and attributes from an XML tree.</span></span>

|<span data-ttu-id="4b8f0-113">Método</span><span class="sxs-lookup"><span data-stu-id="4b8f0-113">Method</span></span>|<span data-ttu-id="4b8f0-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="4b8f0-114">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="4b8f0-115">Quita un elemento <xref:System.Xml.Linq.XAttribute> de su elemento primario.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-115">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="4b8f0-116">Quita los nodos secundarios de un elemento <xref:System.Xml.Linq.XContainer> de la colección.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-116">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="4b8f0-117">Quita el contenido y los atributos de un elemento <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-117">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="4b8f0-118">Quita los atributos de un elemento <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-118">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="4b8f0-119">Si pasa `null` para el valor, quita el atributo.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-119">If you pass `null` for value, then removes the attribute.</span></span>|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="4b8f0-120">Si pasa `null` para el valor, quita el elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-120">If you pass `null` for value, then removes the child element.</span></span>|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="4b8f0-121">Quita un elemento <xref:System.Xml.Linq.XNode> de su elemento primario.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-121">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="4b8f0-122">Quita todos los atributos o elementos de la colección de origen de su elemento primario.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-122">Removes every attribute or element in the source collection from its parent element.</span></span>|

## <a name="example"></a><span data-ttu-id="4b8f0-123">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4b8f0-123">Example</span></span>

### <a name="description"></a><span data-ttu-id="4b8f0-124">Descripción</span><span class="sxs-lookup"><span data-stu-id="4b8f0-124">Description</span></span>

<span data-ttu-id="4b8f0-125">Este ejemplo demuestra tres métodos para quitar elementos.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-125">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="4b8f0-126">Primero, quita un solo elemento.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-126">First, it removes a single element.</span></span> <span data-ttu-id="4b8f0-127">En segundo lugar, recupera una colección de elementos, los materializa con el operador <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> y quita la colección.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-127">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="4b8f0-128">Por último, recupera una colección de elementos y los quita con el método de extensión <xref:System.Xml.Linq.Extensions.Remove%2A>.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-128">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>

<span data-ttu-id="4b8f0-129">Para obtener más información sobre el operador <xref:System.Linq.Enumerable.ToList%2A>, vea [Convertir tipos de datos (C#)](./converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="4b8f0-129">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](./converting-data-types.md).</span></span>

### <a name="code"></a><span data-ttu-id="4b8f0-130">Código</span><span class="sxs-lookup"><span data-stu-id="4b8f0-130">Code</span></span>

```csharp
XElement root = XElement.Parse(@"<Root>
    <Child1>
        <GrandChild1/>
        <GrandChild2/>
        <GrandChild3/>
    </Child1>
    <Child2>
        <GrandChild4/>
        <GrandChild5/>
        <GrandChild6/>
    </Child2>
    <Child3>
        <GrandChild7/>
        <GrandChild8/>
        <GrandChild9/>
    </Child3>
</Root>");
root.Element("Child1").Element("GrandChild1").Remove();
root.Element("Child2").Elements().ToList().Remove();
root.Element("Child3").Elements().Remove();
Console.WriteLine(root);
```

### <a name="comments"></a><span data-ttu-id="4b8f0-131">Comentarios</span><span class="sxs-lookup"><span data-stu-id="4b8f0-131">Comments</span></span>

<span data-ttu-id="4b8f0-132">Este código genera el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="4b8f0-132">This code produces the following output:</span></span>

```xml
<Root>
  <Child1>
    <GrandChild2 />
    <GrandChild3 />
  </Child1>
  <Child2 />
  <Child3 />
</Root>
```

<span data-ttu-id="4b8f0-133">Tenga en cuenta que el primer elemento descendiente del secundario se ha quitado de `Child1`.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-133">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="4b8f0-134">Todos los elementos descendientes del secundario se han quitado de `Child2` y `Child3`.</span><span class="sxs-lookup"><span data-stu-id="4b8f0-134">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>

---
title: Crear árboles XML en C# (LINQ to XML)
description: Obtenga información sobre cómo crear árboles XML en C#, incluida la construcción de elementos y el uso de constructores de XElement.
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 3991f461c4c870a64320853ccd1d45026a8a6bf6
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105476"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="2b582-103">Crear árboles XML en C# (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="2b582-103">Creating XML trees in C# (LINQ to XML)</span></span>
<span data-ttu-id="2b582-104">En esta sección encontrará información acerca de cómo crear árboles XML en C#.</span><span class="sxs-lookup"><span data-stu-id="2b582-104">This section provides information about creating XML trees in C#.</span></span>  
  
 <span data-ttu-id="2b582-105">Para obtener información sobre cómo usar los resultados de las consultas LINQ como contenido de un <xref:System.Xml.Linq.XElement>, vea [Construcción funcional (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2b582-105">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="constructing-elements"></a><span data-ttu-id="2b582-106">Elementos de construcción</span><span class="sxs-lookup"><span data-stu-id="2b582-106">Constructing elements</span></span>
 <span data-ttu-id="2b582-107">Las firmas de los constructores <xref:System.Xml.Linq.XElement> y <xref:System.Xml.Linq.XAttribute> le permiten pasar los contenidos del elemento o atributo como argumentos del constructor.</span><span class="sxs-lookup"><span data-stu-id="2b582-107">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="2b582-108">Dado que uno de los constructores recibe un número variable de argumentos, podrá pasar tantos elementos secundarios como desee.</span><span class="sxs-lookup"><span data-stu-id="2b582-108">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="2b582-109">Por supuesto, cada uno de esos elementos secundarios podrá contener sus propios elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="2b582-109">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="2b582-110">Para cualquier elemento, podrá agregar cuantos atributos desee.</span><span class="sxs-lookup"><span data-stu-id="2b582-110">For any element, you can add any number of attributes.</span></span>  
  
 <span data-ttu-id="2b582-111">Cuando se agregan objetos <xref:System.Xml.Linq.XNode> (incluyendo el objeto <xref:System.Xml.Linq.XElement>) o <xref:System.Xml.Linq.XAttribute>, si el contenido nuevo no tiene un elemento primario, los objetos simplemente se adjuntan al árbol XML.</span><span class="sxs-lookup"><span data-stu-id="2b582-111">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="2b582-112">Si el contenido nuevo ya tiene un elemento primario y forma parte de otro árbol XML, el nuevo contenido se clonará y ese clon se asociará al árbol XML.</span><span class="sxs-lookup"><span data-stu-id="2b582-112">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="2b582-113">El último ejemplo de este tema muestra este comportamiento.</span><span class="sxs-lookup"><span data-stu-id="2b582-113">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="2b582-114">Para crear un `contacts`<xref:System.Xml.Linq.XElement>, podría utilizar el siguiente código:</span><span class="sxs-lookup"><span data-stu-id="2b582-114">To create a `contacts`<xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="2b582-115">Si se aplica correctamente la sangría, el código que construye los objetos <xref:System.Xml.Linq.XElement> se asemeja mucho a la estructura del contenido XML subyacente.</span><span class="sxs-lookup"><span data-stu-id="2b582-115">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>  
  
## <a name="xelement-constructors"></a><span data-ttu-id="2b582-116">Constructores de XElement</span><span class="sxs-lookup"><span data-stu-id="2b582-116">XElement constructors</span></span>  
 <span data-ttu-id="2b582-117">La clase <xref:System.Xml.Linq.XElement> utiliza los siguientes constructores para llevar a cabo una construcción funcional.</span><span class="sxs-lookup"><span data-stu-id="2b582-117">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="2b582-118">Observe que existen algunos constructores más para <xref:System.Xml.Linq.XElement>, pero, dado que no se utilizan para el proceso de construcción funcional, no se detallarán aquí.</span><span class="sxs-lookup"><span data-stu-id="2b582-118">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they are not used for functional construction they are not listed here.</span></span>  
  
|<span data-ttu-id="2b582-119">Constructor</span><span class="sxs-lookup"><span data-stu-id="2b582-119">Constructor</span></span>|<span data-ttu-id="2b582-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="2b582-120">Description</span></span>|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|<span data-ttu-id="2b582-121">Crea una interfaz <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="2b582-121">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="2b582-122">El parámetro `name` especifica el nombre del elemento; `content` especifica el contenido del elemento.</span><span class="sxs-lookup"><span data-stu-id="2b582-122">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|  
|`XElement(XName name)`|<span data-ttu-id="2b582-123">Crea un <xref:System.Xml.Linq.XElement> cuyo <xref:System.Xml.Linq.XName> se inicializa con el nombre especificado.</span><span class="sxs-lookup"><span data-stu-id="2b582-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|  
|`XElement(XName name, params object[] content)`|<span data-ttu-id="2b582-124">Crea un <xref:System.Xml.Linq.XElement> cuyo <xref:System.Xml.Linq.XName> se inicializa con el nombre especificado.</span><span class="sxs-lookup"><span data-stu-id="2b582-124">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="2b582-125">Los atributos y/o elementos secundarios se crean a partir de los contenidos de la lista de parámetros.</span><span class="sxs-lookup"><span data-stu-id="2b582-125">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|  
  
 <span data-ttu-id="2b582-126">El parámetro `content` es extremadamente flexible.</span><span class="sxs-lookup"><span data-stu-id="2b582-126">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="2b582-127">Admite cualquier tipo de objeto que sea un elemento secundario válido de un <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="2b582-127">It supports any type of object that is a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="2b582-128">Se aplicarán las siguientes reglas a los diferentes tipos de objetos pasados en este parámetros:</span><span class="sxs-lookup"><span data-stu-id="2b582-128">The following rules apply to different types of objects passed in this parameter:</span></span>  
  
- <span data-ttu-id="2b582-129">Una cadena se agrega como contenido de tipo texto.</span><span class="sxs-lookup"><span data-stu-id="2b582-129">A string is added as text content.</span></span>  
  
- <span data-ttu-id="2b582-130">Un <xref:System.Xml.Linq.XElement> se agrega como un elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="2b582-130">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>  
  
- <span data-ttu-id="2b582-131">Un <xref:System.Xml.Linq.XAttribute> se agrega como un atributo.</span><span class="sxs-lookup"><span data-stu-id="2b582-131">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>  
  
- <span data-ttu-id="2b582-132">Un <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment> o un <xref:System.Xml.Linq.XText> se agregan como un contenido secundario.</span><span class="sxs-lookup"><span data-stu-id="2b582-132">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>  
  
- <span data-ttu-id="2b582-133">Un <xref:System.Collections.IEnumerable> es un tipo enumerado y se aplicarán estas reglas recursivamente a los resultados.</span><span class="sxs-lookup"><span data-stu-id="2b582-133">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>  
  
- <span data-ttu-id="2b582-134">Para el resto de tipos, se llamará a su método `ToString` y se agregará el resultado como contenido de tipo texto.</span><span class="sxs-lookup"><span data-stu-id="2b582-134">For any other type, its `ToString` method is called and the result is added as text content.</span></span>  
  
### <a name="creating-an-xelement-with-content"></a><span data-ttu-id="2b582-135">Creación de un XElement con contenidos</span><span class="sxs-lookup"><span data-stu-id="2b582-135">Creating an XElement with content</span></span>  
 <span data-ttu-id="2b582-136">Puede crear un <xref:System.Xml.Linq.XElement> que contenga un contenido simple con una única llamada a método.</span><span class="sxs-lookup"><span data-stu-id="2b582-136">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="2b582-137">Para ello, especifique el contenido como segundo parámetro, tal y como sigue:</span><span class="sxs-lookup"><span data-stu-id="2b582-137">To do this, specify the content as the second parameter, as follows:</span></span>  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="2b582-138">Este ejemplo produce el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="2b582-138">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 <span data-ttu-id="2b582-139">Puede pasar cualquier tipo de objeto como contenido.</span><span class="sxs-lookup"><span data-stu-id="2b582-139">You can pass any type of object as the content.</span></span> <span data-ttu-id="2b582-140">Por ejemplo, el siguiente código crea un elemento que contiene un número de punto flotante como contenido:</span><span class="sxs-lookup"><span data-stu-id="2b582-140">For example, the following code creates an element that contains a floating point number as content:</span></span>  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="2b582-141">Este ejemplo produce el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="2b582-141">This example produces the following output:</span></span>  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 <span data-ttu-id="2b582-142">Al número de punto flotante se le aplica la conversión boxing y se pasa al constructor.</span><span class="sxs-lookup"><span data-stu-id="2b582-142">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="2b582-143">El número se convierte entonces en una cadena y se utiliza como contenido del elemento.</span><span class="sxs-lookup"><span data-stu-id="2b582-143">The boxed number is converted to a string and used as the content of the element.</span></span>  
  
### <a name="creating-an-xelement-with-a-child-element"></a><span data-ttu-id="2b582-144">Creación de un XElement con un elemento secundario</span><span class="sxs-lookup"><span data-stu-id="2b582-144">Creating an XElement with a child element</span></span>  
 <span data-ttu-id="2b582-145">Si pasa una instancia de la clase <xref:System.Xml.Linq.XElement> para el argumento del contenido, el constructor creará un elemento que tiene un elemento secundario:</span><span class="sxs-lookup"><span data-stu-id="2b582-145">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 <span data-ttu-id="2b582-146">Este ejemplo produce el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="2b582-146">This example produces the following output:</span></span>  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="2b582-147">Creación de un XElement con varios elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="2b582-147">Creating an XElement with multiple child elements</span></span>  
 <span data-ttu-id="2b582-148">Para el contenido, puede pasar tantos objetos <xref:System.Xml.Linq.XElement> como desee.</span><span class="sxs-lookup"><span data-stu-id="2b582-148">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="2b582-149">Cada uno de los objetos <xref:System.Xml.Linq.XElement> se incluye como elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="2b582-149">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 <span data-ttu-id="2b582-150">Este ejemplo produce el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="2b582-150">This example produces the following output:</span></span>  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 <span data-ttu-id="2b582-151">Si se extiende el ejemplo anterior, es posible crear un árbol XML completo, tal y como sigue:</span><span class="sxs-lookup"><span data-stu-id="2b582-151">By extending the above example, you can create an entire XML tree, as follows:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
Console.WriteLine(contacts);  
```  
  
 <span data-ttu-id="2b582-152">Este ejemplo produce el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="2b582-152">This example produces the following output:</span></span>  
  
```xml  
<Contacts>  
  <Contact>  
    <Name>Patrick Hines</Name>  
    <Phone>206-555-0144</Phone>  
    <Address>  
      <Street1>123 Main St</Street1>  
      <City>Mercer Island</City>  
      <State>WA</State>  
      <Postal>68042</Postal>  
    </Address>  
  </Contact>  
</Contacts>  
```  

### <a name="creating-an-xelement-with-an-xattribute"></a><span data-ttu-id="2b582-153">Creación de un XElement con un XAttribute</span><span class="sxs-lookup"><span data-stu-id="2b582-153">Creating an XElement with an XAttribute</span></span>
 <span data-ttu-id="2b582-154">Si pasa una instancia de la clase <xref:System.Xml.Linq.XAttribute> para el argumento del contenido, el constructor creará un elemento con un atributo:</span><span class="sxs-lookup"><span data-stu-id="2b582-154">If you pass an instance of the <xref:System.Xml.Linq.XAttribute> class for the content argument, the constructor creates an element with an attribute:</span></span>

```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="2b582-155">Este ejemplo produce el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="2b582-155">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>
```

### <a name="creating-an-empty-element"></a><span data-ttu-id="2b582-156">Creación de un elemento vacío</span><span class="sxs-lookup"><span data-stu-id="2b582-156">Creating an empty element</span></span>  
 <span data-ttu-id="2b582-157">Para crear un <xref:System.Xml.Linq.XElement> vacío, no pase ningún contenido al constructor.</span><span class="sxs-lookup"><span data-stu-id="2b582-157">To create an empty <xref:System.Xml.Linq.XElement>, you do not pass any content to the constructor.</span></span> <span data-ttu-id="2b582-158">El siguiente ejemplo crea un elemento vacío:</span><span class="sxs-lookup"><span data-stu-id="2b582-158">The following example creates an empty element:</span></span>  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="2b582-159">Este ejemplo produce el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="2b582-159">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a><span data-ttu-id="2b582-160">Diferencias entre asociar y clonar</span><span class="sxs-lookup"><span data-stu-id="2b582-160">Attaching vs. cloning</span></span>  
 <span data-ttu-id="2b582-161">Como mencionamos anteriormente, cuando se agregan objetos <xref:System.Xml.Linq.XNode> (incluyendo el objeto <xref:System.Xml.Linq.XElement>) o <xref:System.Xml.Linq.XAttribute>, si el contenido nuevo no tiene un elemento primario, los objetos simplemente se adjuntan al árbol XML.</span><span class="sxs-lookup"><span data-stu-id="2b582-161">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="2b582-162">Si el contenido nuevo ya tiene un elemento primario y forma parte de otro árbol XML, el nuevo contenido se clonará y ese clon se asociará al árbol XML.</span><span class="sxs-lookup"><span data-stu-id="2b582-162">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  

<span data-ttu-id="2b582-163">En el siguiente ejemplo se demuestra qué ocurre si agrega un elemento que tiene elemento primario a un árbol y qué ocurre si agrega un elemento que no tenga elemento primario a un árbol.</span><span class="sxs-lookup"><span data-stu-id="2b582-163">The following example demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>

```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  

// The example displays the following output:  
//    Child1 was cloned  
//    Child2 was attached  
```

## <a name="see-also"></a><span data-ttu-id="2b582-164">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2b582-164">See also</span></span>

- [<span data-ttu-id="2b582-165">Crear árboles XML en C# </span><span class="sxs-lookup"><span data-stu-id="2b582-165">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)

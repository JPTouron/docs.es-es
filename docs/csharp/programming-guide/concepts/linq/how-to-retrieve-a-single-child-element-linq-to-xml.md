---
title: Procedimiento para recuperar un único elemento secundario (LINQ to XML) (C#)
description: Aprenda a usar LINQ to XML para recuperar un único elemento secundario por nombre. En este ejemplo de C#, el método Element devuelve el primer elemento secundario especificado.
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: c3a044f30cf2e411bdff52586c7a370b626f41bc
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103281"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a><span data-ttu-id="c725c-104">Procedimiento para recuperar un único elemento secundario (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c725c-104">How to retrieve a single child element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="c725c-105">En este tema se explica cómo recuperar un único elemento secundario, dado el nombre del elemento secundario.</span><span class="sxs-lookup"><span data-stu-id="c725c-105">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="c725c-106">Si conoce el nombre del elemento secundario y que solo hay un elemento que tiene ese nombre, puede resultar cómodo recuperar solamente un elemento, en lugar de una colección.</span><span class="sxs-lookup"><span data-stu-id="c725c-106">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="c725c-107">El método <xref:System.Xml.Linq.XContainer.Element%2A> devuelve el primer <xref:System.Xml.Linq.XElement> secundario con el <xref:System.Xml.Linq.XName> especificado.</span><span class="sxs-lookup"><span data-stu-id="c725c-107">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="c725c-108">Si desea recuperar un único elemento secundario de Visual Basic, un enfoque común consiste en utilizar la propiedad XML y después recuperar el primer elemento mediante una notación de indizador de matriz.</span><span class="sxs-lookup"><span data-stu-id="c725c-108">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c725c-109">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c725c-109">Example</span></span>  
 <span data-ttu-id="c725c-110">En el siguiente ejemplo se muestra el uso del método <xref:System.Xml.Linq.XContainer.Element%2A>.</span><span class="sxs-lookup"><span data-stu-id="c725c-110">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="c725c-111">Este ejemplo toma un árbol XML con el nombre `po` y busca el primer elemento con el nombre `Comment`.</span><span class="sxs-lookup"><span data-stu-id="c725c-111">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="c725c-112">El ejemplo de Visual Basic muestra el uso de la notación del indizador de matriz para recuperar un elemento único.</span><span class="sxs-lookup"><span data-stu-id="c725c-112">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="c725c-113">Este ejemplo utiliza el siguiente documento XML: [Archivo XML de ejemplo: Pedido de compra común (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="c725c-113">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="c725c-114">Este ejemplo produce el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="c725c-114">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="c725c-115">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c725c-115">Example</span></span>  
 <span data-ttu-id="c725c-116">El siguiente ejemplo muestra el mismo código sobre un XML que se encuentra en un espacio de nombres.</span><span class="sxs-lookup"><span data-stu-id="c725c-116">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="c725c-117">Para más información, consulte [Información general sobre los espacios de nombres (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c725c-117">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="c725c-118">Este ejemplo utiliza el siguiente documento XML: [Archivo XML de ejemplo: Pedido de compra común en un espacio de nombres](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="c725c-118">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="c725c-119">Este ejemplo produce el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="c725c-119">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c725c-120">Vea también</span><span class="sxs-lookup"><span data-stu-id="c725c-120">See also</span></span>

- [<span data-ttu-id="c725c-121">Ejes de LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c725c-121">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)

---
title: Procedimiento para transformar la forma de un árbol XML (C#)
description: Aprenda a transformar la forma de un árbol XML. La forma de un árbol XML hace referencia a sus nombres de elemento y atributo, y sus características de jerarquía.
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 4fa3cc18f235d061ae1778c177c4ac9b626f4b71
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302651"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a><span data-ttu-id="82cfe-104">Procedimiento para transformar la forma de un árbol XML (C#)</span><span class="sxs-lookup"><span data-stu-id="82cfe-104">How to transform the shape of an XML tree (C#)</span></span>
<span data-ttu-id="82cfe-105">La *forma* de un documento XML hace referencia a sus nombres de elemento, sus nombres de atributo y las características de su jerarquía.</span><span class="sxs-lookup"><span data-stu-id="82cfe-105">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="82cfe-106">A veces, deberá cambiar la forma de un elemento XML.</span><span class="sxs-lookup"><span data-stu-id="82cfe-106">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="82cfe-107">Por ejemplo, es posible que deba enviar un documento XML a otro sistema que requiere nombres de elemento y atributo diferentes.</span><span class="sxs-lookup"><span data-stu-id="82cfe-107">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="82cfe-108">Podría revisar el documento y eliminar y cambiar el nombre de los elementos necesarios, pero el uso de la construcción funcional proporciona un código más legible y fácil de mantener.</span><span class="sxs-lookup"><span data-stu-id="82cfe-108">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="82cfe-109">Para obtener más información sobre la construcción funcional, consulte [Construcción funcional (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="82cfe-109">For more information about functional construction, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="82cfe-110">El primer ejemplo cambia la organización del documento XML.</span><span class="sxs-lookup"><span data-stu-id="82cfe-110">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="82cfe-111">Mueve los elementos complejos de una ubicación del árbol a otra.</span><span class="sxs-lookup"><span data-stu-id="82cfe-111">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="82cfe-112">El segundo ejemplo de este tema crea un documento XML con una forma diferente a la del documento de origen.</span><span class="sxs-lookup"><span data-stu-id="82cfe-112">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="82cfe-113">Cambia el uso de mayúsculas y minúsculas de los nombres de elemento, cambia el nombre de algunos elementos y deja algunos de los elementos del árbol de origen fuera del árbol transformado.</span><span class="sxs-lookup"><span data-stu-id="82cfe-113">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82cfe-114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="82cfe-114">Example</span></span>  
 <span data-ttu-id="82cfe-115">El código siguiente cambia la forma de un archivo XML con las expresiones de consulta incrustadas.</span><span class="sxs-lookup"><span data-stu-id="82cfe-115">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="82cfe-116">El documento XML de origen de este ejemplo contiene un elemento `Customers` en el elemento `Root` que contiene todos los clientes.</span><span class="sxs-lookup"><span data-stu-id="82cfe-116">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="82cfe-117">También contiene un elemento `Orders` en el elemento `Root` que contiene todos los pedidos.</span><span class="sxs-lookup"><span data-stu-id="82cfe-117">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="82cfe-118">Este ejemplo crea un nuevo árbol XML en el que los pedidos de cada cliente se incluyen en un elemento `Orders` dentro del elemento `Customer`.</span><span class="sxs-lookup"><span data-stu-id="82cfe-118">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="82cfe-119">El documento original también contiene un elemento `CustomerID` en el elemento `Order`; este elemento se quitará del documento con la forma cambiada.</span><span class="sxs-lookup"><span data-stu-id="82cfe-119">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="82cfe-120">Este ejemplo utiliza el siguiente documento XML: [Archivo XML de ejemplo: Clientes y pedidos (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="82cfe-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
XElement newCustOrd =  
    new XElement("Root",  
        from cust in co.Element("Customers").Elements("Customer")  
        select new XElement("Customer",  
            cust.Attributes(),  
            cust.Elements(),  
            new XElement("Orders",  
                from ord in co.Element("Orders").Elements("Order")  
                where (string)ord.Element("CustomerID") == (string)cust.Attribute("CustomerID")  
                select new XElement("Order",  
                    ord.Attributes(),  
                    ord.Element("EmployeeID"),  
                    ord.Element("OrderDate"),  
                    ord.Element("RequiredDate"),  
                    ord.Element("ShipInfo")  
                )  
            )  
        )  
    );  
Console.WriteLine(newCustOrd);  
```  
  
 <span data-ttu-id="82cfe-121">Este código genera el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="82cfe-121">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Customer CustomerID="GREAL">  
    <CompanyName>Great Lakes Food Market</CompanyName>  
    <ContactName>Howard Snyder</ContactName>  
    <ContactTitle>Marketing Manager</ContactTitle>  
    <Phone>(503) 555-7555</Phone>  
    <FullAddress>  
      <Address>2732 Baker Blvd.</Address>  
      <City>Eugene</City>  
      <Region>OR</Region>  
      <PostalCode>97403</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
    <Orders />  
  </Customer>  
  <Customer CustomerID="HUNGC">  
    <CompanyName>Hungry Coyote Import Store</CompanyName>  
    <ContactName>Yoshi Latimer</ContactName>  
    <ContactTitle>Sales Representative</ContactTitle>  
    <Phone>(503) 555-6874</Phone>  
    <Fax>(503) 555-2376</Fax>  
    <FullAddress>  
      <Address>City Center Plaza 516 Main St.</Address>  
      <City>Elgin</City>  
      <Region>OR</Region>  
      <PostalCode>97827</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
    <Orders />  
  </Customer>  
  . . .  
```  
  
## <a name="example"></a><span data-ttu-id="82cfe-122">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="82cfe-122">Example</span></span>  
 <span data-ttu-id="82cfe-123">Este ejemplo cambia el nombre de algunos elementos y convierte algunos atributos en elementos.</span><span class="sxs-lookup"><span data-stu-id="82cfe-123">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="82cfe-124">El código llama a `ConvertAddress`, que devuelve una lista de objetos <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="82cfe-124">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="82cfe-125">El argumento del método es una consulta que determina el elemento complejo `Address` en el que el atributo `Type` tiene un valor `"Shipping"`.</span><span class="sxs-lookup"><span data-stu-id="82cfe-125">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="82cfe-126">Este ejemplo utiliza el siguiente documento XML: [Archivo XML de ejemplo: Pedido de compra común (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="82cfe-126">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
static IEnumerable<XElement> ConvertAddress(XElement add)  
{  
    List<XElement> fragment = new List<XElement>() {  
        new XElement("NAME", (string)add.Element("Name")),  
        new XElement("STREET", (string)add.Element("Street")),  
        new XElement("CITY", (string)add.Element("City")),  
        new XElement("ST", (string)add.Element("State")),  
        new XElement("POSTALCODE", (string)add.Element("Zip")),  
        new XElement("COUNTRY", (string)add.Element("Country"))  
    };  
    return fragment;  
}  
  
static void Main(string[] args)  
{  
    XElement po = XElement.Load("PurchaseOrder.xml");  
    XElement newPo = new XElement("PO",  
        new XElement("ID", (string)po.Attribute("PurchaseOrderNumber")),  
        new XElement("DATE", (DateTime)po.Attribute("OrderDate")),  
        ConvertAddress(  
            (from el in po.Elements("Address")  
            where (string)el.Attribute("Type") == "Shipping"  
            select el)  
            .First()  
        )  
    );  
    Console.WriteLine(newPo);  
}  
```  
  
 <span data-ttu-id="82cfe-127">Este código genera el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="82cfe-127">This code produces the following output:</span></span>  
  
```xml  
<PO>  
  <ID>99503</ID>  
  <DATE>1999-10-20T00:00:00</DATE>  
  <NAME>Ellen Adams</NAME>  
  <STREET>123 Maple Street</STREET>  
  <CITY>Mill Valley</CITY>  
  <ST>CA</ST>  
  <POSTALCODE>10999</POSTALCODE>  
  <COUNTRY>USA</COUNTRY>  
</PO>  
```  

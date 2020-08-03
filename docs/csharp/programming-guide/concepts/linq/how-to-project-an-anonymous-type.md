---
title: Procedimiento para proyectar un tipo anónimo (C#)
description: Obtenga información sobre cómo proyectar una consulta en un tipo anónimo en C#. Usar un tipo anónimo puede ser más sencillo que crear uno nuevo para emplearlo solo de forma breve.
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 6598796a4ba95362340f2551b1da6ac6d857eaae
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104635"
---
# <a name="how-to-project-an-anonymous-type-c"></a><span data-ttu-id="6be44-104">Procedimiento para proyectar un tipo anónimo (C#)</span><span class="sxs-lookup"><span data-stu-id="6be44-104">How to project an anonymous type (C#)</span></span>
<span data-ttu-id="6be44-105">En algunos casos quizás desee proyectar una consulta a un nuevo tipo, aunque sepa que solo utilizará este tipo durante un breve período.</span><span class="sxs-lookup"><span data-stu-id="6be44-105">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="6be44-106">Crear un nuevo tipo solamente para usarlo en la proyección conlleva mucho trabajo adicional.</span><span class="sxs-lookup"><span data-stu-id="6be44-106">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="6be44-107">En este caso un enfoque más eficiente consiste en proyectar en un tipo anónimo.</span><span class="sxs-lookup"><span data-stu-id="6be44-107">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="6be44-108">Los tipos anónimos permiten definir una clase y, a continuación, declarar e inicializar un objeto de esa clase, sin dar un nombre a la clase.</span><span class="sxs-lookup"><span data-stu-id="6be44-108">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="6be44-109">Los tipos anónimos son la implementación de C# del concepto matemático de *tupla*.</span><span class="sxs-lookup"><span data-stu-id="6be44-109">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="6be44-110">El término matemático tupla se originó de la secuencia único, doble, triple, cuádruple, quíntuple, n-tuple.</span><span class="sxs-lookup"><span data-stu-id="6be44-110">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="6be44-111">Se refiere a una secuencia finita de objetos, cada uno de un tipo específico.</span><span class="sxs-lookup"><span data-stu-id="6be44-111">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="6be44-112">A veces se denomina una lista de pares nombre/valor.</span><span class="sxs-lookup"><span data-stu-id="6be44-112">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="6be44-113">Por ejemplo, el contenido de una dirección en el documento XML [Archivo XML de ejemplo: Pedido de compra común (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) se podría expresar de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="6be44-113">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML document could be expressed as follows:</span></span>  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="6be44-114">Cuando se crea una instancia de un tipo anónimo, resulta práctico pensar en ella como si se creara una tupla de orden n.</span><span class="sxs-lookup"><span data-stu-id="6be44-114">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="6be44-115">Si escribe una consulta que crea una tupla en la cláusula `select`, la consulta devuelve un `IEnumerable` de la tupla.</span><span class="sxs-lookup"><span data-stu-id="6be44-115">If you write a query that creates a tuple in the `select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6be44-116">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6be44-116">Example</span></span>  
 <span data-ttu-id="6be44-117">En este ejemplo, la cláusula `select` proyecta un tipo anónimo.</span><span class="sxs-lookup"><span data-stu-id="6be44-117">In this example, the `select` clause projects an anonymous type.</span></span> <span data-ttu-id="6be44-118">A continuación, el ejemplo utiliza `var` para crear el objeto `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="6be44-118">The example then uses `var` to create the `IEnumerable` object.</span></span> <span data-ttu-id="6be44-119">En el bucle `foreach`, la variable de iteración se convierte en una instancia del tipo anónimo creado en la expresión de consulta.</span><span class="sxs-lookup"><span data-stu-id="6be44-119">Within the `foreach` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="6be44-120">Este ejemplo utiliza el siguiente documento XML: [Archivo XML de ejemplo: Clientes y pedidos (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="6be44-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement custOrd = XElement.Load("CustomersOrders.xml");  
var custList =  
    from el in custOrd.Element("Customers").Elements("Customer")  
    select new {  
        CustomerID = (string)el.Attribute("CustomerID"),  
        CompanyName = (string)el.Element("CompanyName"),  
        ContactName = (string)el.Element("ContactName")  
    };  
foreach (var cust in custList)  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName);  
```  
  
 <span data-ttu-id="6be44-121">Este código genera el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="6be44-121">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
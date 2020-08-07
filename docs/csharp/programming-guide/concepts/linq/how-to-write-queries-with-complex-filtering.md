---
title: Procedimiento para escribir consultas con filtrado complejo (C#)
description: Aprenda a escribir consultas de LINQ to XML con filtros complejos. Vea ejemplos de código y examine recursos adicionales.
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 5d2c1aafc210b35d4d6b1f1b2d74b11966d90c80
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303431"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="8d9b1-104">Procedimiento para escribir consultas con filtrado complejo (C#)</span><span class="sxs-lookup"><span data-stu-id="8d9b1-104">How to write queries with complex filtering (C#)</span></span>
<span data-ttu-id="8d9b1-105">Es posible que desee escribir consultas LINQ to XML con filtros complejos.</span><span class="sxs-lookup"><span data-stu-id="8d9b1-105">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="8d9b1-106">Por ejemplo, quizás debe buscar todos los elementos que tienen un elemento secundario con un valor y un nombre específicos.</span><span class="sxs-lookup"><span data-stu-id="8d9b1-106">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="8d9b1-107">En este tema se proporciona un ejemplo de escritura de una consulta con un filtrado complejo.</span><span class="sxs-lookup"><span data-stu-id="8d9b1-107">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d9b1-108">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8d9b1-108">Example</span></span>  
 <span data-ttu-id="8d9b1-109">En este ejemplo se muestra cómo buscar todos los elementos `PurchaseOrder` que tienen un elemento `Address` secundario que tiene un atributo `Type` igual a "Shipping" (envío) y un elemento `State` secundario igual a "NY".</span><span class="sxs-lookup"><span data-stu-id="8d9b1-109">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="8d9b1-110">Utiliza una consulta anidada en la cláusula `Where` y el operador `Any` devuelve `true` si la colección tiene elementos en ella.</span><span class="sxs-lookup"><span data-stu-id="8d9b1-110">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="8d9b1-111">Para obtener información sobre cómo usar la sintaxis de consultas basadas en métodos, vea [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md) (Sintaxis de consultas y sintaxis de métodos en LINQ).</span><span class="sxs-lookup"><span data-stu-id="8d9b1-111">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="8d9b1-112">Este ejemplo utiliza el siguiente documento XML: [Archivo XML de ejemplo: Varios pedidos de compra (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8d9b1-112">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="8d9b1-113">Para obtener más información sobre el operador `Any`, vea [ Operaciones cuantificadoras (C#)](./quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="8d9b1-113">For more information about the `Any` operator, see [Quantifier Operations (C#)](./quantifier-operations.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements("PurchaseOrder")  
    where
        (from add in el.Elements("Address")  
        where  
            (string)add.Attribute("Type") == "Shipping" &&  
            (string)add.Element("State") == "NY"  
        select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));  
```  
  
 <span data-ttu-id="8d9b1-114">Este código genera el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="8d9b1-114">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="8d9b1-115">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8d9b1-115">Example</span></span>  
 <span data-ttu-id="8d9b1-116">El siguiente ejemplo muestra la misma consulta sobre un XML que se encuentra en un espacio de nombres.</span><span class="sxs-lookup"><span data-stu-id="8d9b1-116">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="8d9b1-117">Para más información, consulte [Información general sobre los espacios de nombres (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8d9b1-117">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="8d9b1-118">Este ejemplo utiliza el siguiente documento XML: [Archivo XML de ejemplo: Varios pedidos de compra en un espacio de nombres](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="8d9b1-118">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements(aw + "PurchaseOrder")  
    where  
        (from add in el.Elements(aw + "Address")  
         where  
             (string)add.Attribute(aw + "Type") == "Shipping" &&  
             (string)add.Element(aw + "State") == "NY"  
         select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));  
```  
  
 <span data-ttu-id="8d9b1-119">Este código genera el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="8d9b1-119">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d9b1-120">Consulte también</span><span class="sxs-lookup"><span data-stu-id="8d9b1-120">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- <span data-ttu-id="8d9b1-121">[Operaciones de proyección [C#]](./projection-operations.md)</span><span class="sxs-lookup"><span data-stu-id="8d9b1-121">[Projection Operations (C#)](./projection-operations.md)</span></span>
- <span data-ttu-id="8d9b1-122">[Operaciones cuantificadoras [C#]](./quantifier-operations.md)</span><span class="sxs-lookup"><span data-stu-id="8d9b1-122">[Quantifier Operations (C#)](./quantifier-operations.md)</span></span>

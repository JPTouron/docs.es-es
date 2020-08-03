---
title: Objetos XName y XNamespace atomizados (LINQ to XML) (C#)
description: Obtenga información sobre los objetos XNamespace y XName atomizados, y cómo proporcionan ventajas de rendimiento para las consultas.
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: 305a233adab5c860b5f9509ae25ccc5d633e7957
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104283"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a><span data-ttu-id="2310d-103">Objetos XName y XNamespace atomizados (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2310d-103">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="2310d-104">Los objetos <xref:System.Xml.Linq.XName> y <xref:System.Xml.Linq.XNamespace> se *atomizan*; es decir, si contienen el mismo nombre completo, hacen referencia al mismo objeto.</span><span class="sxs-lookup"><span data-stu-id="2310d-104"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="2310d-105">De esta forma, se incrementan los beneficios de rendimiento de las consultas: cuando compare la igualdad de dos nombres atomizados, el lenguaje intermedio subyacente solo debe determinar si los dos puntos de referencia apuntan al mismo objeto.</span><span class="sxs-lookup"><span data-stu-id="2310d-105">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="2310d-106">El código subyacente no debe hacer comparaciones de cadenas, ya que sería un proceso muy lento.</span><span class="sxs-lookup"><span data-stu-id="2310d-106">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="2310d-107">Semántica de atomización</span><span class="sxs-lookup"><span data-stu-id="2310d-107">Atomization Semantics</span></span>  
 <span data-ttu-id="2310d-108">Atomización significa que si dos objetos <xref:System.Xml.Linq.XName> tienen el mismo nombre local y se encuentran en el mismo espacio de nombres, comparten la misma instancia.</span><span class="sxs-lookup"><span data-stu-id="2310d-108">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="2310d-109">De igual forma, si dos objetos <xref:System.Xml.Linq.XNamespace> tienen el mismo URI de espacio de nombres, comparten la misma instancia.</span><span class="sxs-lookup"><span data-stu-id="2310d-109">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="2310d-110">Para que una clase habilite objetos atomizados, el constructor de la clase debe ser privado y no público.</span><span class="sxs-lookup"><span data-stu-id="2310d-110">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="2310d-111">La razón es que si el constructor fuera público, podría crea un objeto no atomizado.</span><span class="sxs-lookup"><span data-stu-id="2310d-111">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="2310d-112">Las clases <xref:System.Xml.Linq.XName> y <xref:System.Xml.Linq.XNamespace> implementan un operador de conversión implícita para convertir una cadena en <xref:System.Xml.Linq.XName> o <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="2310d-112">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="2310d-113">De esta forma, obtiene una instancia de estos objetos.</span><span class="sxs-lookup"><span data-stu-id="2310d-113">This is how you get an instance of these objects.</span></span> <span data-ttu-id="2310d-114">No puede obtener ninguna instancia mediante un constructor, ya que no se puede tener acceso a él.</span><span class="sxs-lookup"><span data-stu-id="2310d-114">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="2310d-115"><xref:System.Xml.Linq.XName> y <xref:System.Xml.Linq.XNamespace> también implementan los operadores de igualdad y desigualdad, para determinar si los dos objetos que se comparan son referencias a la misma instancia.</span><span class="sxs-lookup"><span data-stu-id="2310d-115"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2310d-116">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2310d-116">Example</span></span>  
 <span data-ttu-id="2310d-117">El siguiente código crea algunos objetos <xref:System.Xml.Linq.XElement> y muestra que nombres idénticos comparten la misma instancia.</span><span class="sxs-lookup"><span data-stu-id="2310d-117">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
```csharp  
XElement r1 = new XElement("Root", "data1");  
XElement r2 = XElement.Parse("<Root>data2</Root>");  
  
if ((object)r1.Name == (object)r2.Name)  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.");  
else  
    Console.WriteLine("Different");  
  
XName n = "Root";  
  
if ((object)n == (object)r1.Name)  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.");  
else  
    Console.WriteLine("Different");  
```  
  
 <span data-ttu-id="2310d-118">Este ejemplo produce el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="2310d-118">This example produces the following output:</span></span>  
  
```output  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="2310d-119">Como se ha mencionado anteriormente, la ventaja de los objetos atomizados es que el usuario utiliza uno de los métodos de eje que toman <xref:System.Xml.Linq.XName> como parámetro, el método de eje solo debe determinar que los dos nombres hagan referencia a la misma instancia para seleccionar los elementos deseados.</span><span class="sxs-lookup"><span data-stu-id="2310d-119">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="2310d-120">El siguiente ejemplo pasa <xref:System.Xml.Linq.XName> a la llamada del método <xref:System.Xml.Linq.XContainer.Descendants%2A>, cuyo rendimiento mejora gracias al patrón de atomización.</span><span class="sxs-lookup"><span data-stu-id="2310d-120">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("C1", 1),  
    new XElement("Z1",  
        new XElement("C1", 2),  
        new XElement("C1", 1)  
    )  
);  
  
var query = from e in root.Descendants("C1")  
            where (int)e == 1  
            select e;  
  
foreach (var z in query)  
    Console.WriteLine(z);  
```  
  
 <span data-ttu-id="2310d-121">Este ejemplo produce el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="2310d-121">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  

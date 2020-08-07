---
title: Procedimiento para hacer streaming de fragmentos XML con acceso a la información del encabezado (C#)
description: Aprenda a transmitir fragmentos XML con acceso a la información del encabezado. Las técnicas de transmisión ayudan a evitar el uso excesivo de memoria.
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 8bfded96ea1fa6b096d56ae0736002b9062d58b6
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303223"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a><span data-ttu-id="192ee-104">Procedimiento para hacer streaming de fragmentos XML con acceso a la información del encabezado (C#)</span><span class="sxs-lookup"><span data-stu-id="192ee-104">How to stream XML fragments with access to header information (C#)</span></span>
<span data-ttu-id="192ee-105">A veces debe leer arbitrariamente los archivos XML grandes y escribir la aplicación para que la superficie de memoria de esta sea predecible.</span><span class="sxs-lookup"><span data-stu-id="192ee-105">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="192ee-106">Si intenta rellenar un árbol XML con un archivo XML de gran tamaño, su utilización de memoria será proporcional al tamaño del archivo (es decir, excesivo).</span><span class="sxs-lookup"><span data-stu-id="192ee-106">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="192ee-107">Por consiguiente, debe utilizar en su lugar una técnica de transmisión por secuencias.</span><span class="sxs-lookup"><span data-stu-id="192ee-107">Therefore, you should use a streaming technique instead.</span></span>  
  
<span data-ttu-id="192ee-108">Una opción consiste en escribir la aplicación usando <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="192ee-108">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="192ee-109">Pero quizás prefiera usar LINQ para consultar el árbol XML.</span><span class="sxs-lookup"><span data-stu-id="192ee-109">However, you might want to use LINQ to query the XML tree.</span></span> <span data-ttu-id="192ee-110">En ese caso, puede escribir su propio método de eje personalizado.</span><span class="sxs-lookup"><span data-stu-id="192ee-110">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="192ee-111">Para obtener más información, vea [Procedimiento para escribir un método de eje de LINQ to XML (C#)](./how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="192ee-111">For more information, see [How to write a LINQ to XML axis method (C#)](./how-to-write-a-linq-to-xml-axis-method.md).</span></span>
  
 <span data-ttu-id="192ee-112">Para escribir su propio método de eje, debe escribir un pequeño método que utiliza los nodos <xref:System.Xml.XmlReader> para leer hasta que llega a uno de los nodos en el que está interesado.</span><span class="sxs-lookup"><span data-stu-id="192ee-112">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="192ee-113">A continuación el método llama a <xref:System.Xml.Linq.XNode.ReadFrom%2A>, que lee de <xref:System.Xml.XmlReader> y crea una instancia de un fragmento XML.</span><span class="sxs-lookup"><span data-stu-id="192ee-113">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="192ee-114">A continuación ofrece cada fragmento a través de `yield return` al método que está enumerando su método de eje personalizado.</span><span class="sxs-lookup"><span data-stu-id="192ee-114">It then yields each fragment through `yield return` to the method that is enumerating your custom axis method.</span></span> <span data-ttu-id="192ee-115">A continuación puede escribir las consultas LINQ en su método de eje personalizado.</span><span class="sxs-lookup"><span data-stu-id="192ee-115">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="192ee-116">Las técnicas de transmisión por secuencias se aplican mejor en situaciones en las que el documento de origen solo se debe procesar una vez y se pueden procesar los elementos en el orden del documento.</span><span class="sxs-lookup"><span data-stu-id="192ee-116">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="192ee-117">Ciertos operadores de consulta estándar, como <xref:System.Linq.Enumerable.OrderBy%2A>, recorren en iteración su origen, recaban todos los datos, los ordenan y finalmente producen el primer elemento de la secuencia.</span><span class="sxs-lookup"><span data-stu-id="192ee-117">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="192ee-118">Si utiliza un operador de consulta que materializa su origen antes de producir el primer elemento, no retendrá una superficie de memoria pequeña.</span><span class="sxs-lookup"><span data-stu-id="192ee-118">If you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="192ee-119">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="192ee-119">Example</span></span>  

<span data-ttu-id="192ee-120">A veces el problema se pone un poco más interesante.</span><span class="sxs-lookup"><span data-stu-id="192ee-120">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="192ee-121">En el siguiente documento XML, el consumidor de su método de eje personalizado también tiene que conocer el nombre del cliente al que pertenece cada elemento.</span><span class="sxs-lookup"><span data-stu-id="192ee-121">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
 <span data-ttu-id="192ee-122">El enfoque que toma este ejemplo consiste en consultar también esta información de encabezado, guardar la información de encabezado y después crear un pequeño árbol XML que contiene la información de encabezado y el detalle que está enumerando.</span><span class="sxs-lookup"><span data-stu-id="192ee-122">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="192ee-123">El método de eje ofrece este nuevo y pequeño árbol XML.</span><span class="sxs-lookup"><span data-stu-id="192ee-123">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="192ee-124">La consulta tiene acceso a la información de encabezado así como a la información detallada.</span><span class="sxs-lookup"><span data-stu-id="192ee-124">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="192ee-125">Este enfoque ocupa una pequeña superficie de memoria.</span><span class="sxs-lookup"><span data-stu-id="192ee-125">This approach has a small memory footprint.</span></span> <span data-ttu-id="192ee-126">Como se ofrecen todos los fragmentos XML detallados, no se guardan referencias al fragmento anterior y está disponible para la recolección de elementos no utilizados.</span><span class="sxs-lookup"><span data-stu-id="192ee-126">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="192ee-127">Esta técnica crea muchos objetos de vida corta en el montón.</span><span class="sxs-lookup"><span data-stu-id="192ee-127">This technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="192ee-128">En el siguiente ejemplo se muestra cómo implementar y utilizar un método de eje personalizado que transmite por secuencias fragmentos XML del archivo especificado por la URI.</span><span class="sxs-lookup"><span data-stu-id="192ee-128">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="192ee-129">Este eje personalizado se ha escrito para que espere un documento que tiene los elementos `Customer`, `Name` y `Item`, y que esos elementos se ordenarán como en el documento `Source.xml` anterior.</span><span class="sxs-lookup"><span data-stu-id="192ee-129">This custom axis is written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="192ee-130">Se trata de una implementación simplista.</span><span class="sxs-lookup"><span data-stu-id="192ee-130">It is a simplistic implementation.</span></span> <span data-ttu-id="192ee-131">Una implementación más sólida estaría preparada para analizar un documento no válido.</span><span class="sxs-lookup"><span data-stu-id="192ee-131">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null) {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    XElement xmlTree = new XElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    Console.WriteLine(xmlTree);  
}  
```  
  
 <span data-ttu-id="192ee-132">Este código genera el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="192ee-132">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
</Root>  
```  

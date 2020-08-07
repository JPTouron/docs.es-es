---
title: Serializar en un objeto XmlReader (invocando XSLT) (C#)
description: Aprenda a usar CreateReader para crear un objeto XmlReader en C#. El módulo que lee desde este objeto XmlReader lee los nodos desde el árbol XML y los procesa.
ms.date: 07/20/2015
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: aa5a232c74c5314cb7f1cf03c2a8875ca1cd04df
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302417"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a><span data-ttu-id="4b245-104">Serializar en un objeto XmlReader (invocando XSLT) (C#)</span><span class="sxs-lookup"><span data-stu-id="4b245-104">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>
<span data-ttu-id="4b245-105">Cuando use las funciones de interoperabilidad <xref:System.Xml?displayProperty=nameWithType> de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], puede usar <xref:System.Xml.Linq.XNode.CreateReader%2A> para crear un objeto <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="4b245-105">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="4b245-106">El módulo que lee desde el objeto <xref:System.Xml.XmlReader> lee los nodos desde el árbol XML y los procesa.</span><span class="sxs-lookup"><span data-stu-id="4b245-106">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="4b245-107">Invocar una transformación XSLT</span><span class="sxs-lookup"><span data-stu-id="4b245-107">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="4b245-108">Un uso posible para este método es la invocación de una transformación XSLT.</span><span class="sxs-lookup"><span data-stu-id="4b245-108">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="4b245-109">Puede crear un árbol XML, crear un objeto <xref:System.Xml.XmlReader> desde el árbol XML, crear un nuevo documento y crear un objeto <xref:System.Xml.XmlWriter> que escribirá en el nuevo documento.</span><span class="sxs-lookup"><span data-stu-id="4b245-109">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="4b245-110">A continuación, puede invocar la transformación XSLT, pasando <xref:System.Xml.XmlReader> y <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="4b245-110">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="4b245-111">Después de que se complete correctamente la transformación, se rellenará el nuevo árbol XML con los resultados de la transformación.</span><span class="sxs-lookup"><span data-stu-id="4b245-111">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
```csharp  
string xslMarkup = @"<?xml version='1.0'?>  
<xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
    <xsl:template match='/Parent'>  
        <Root>  
            <C1>  
            <xsl:value-of select='Child1'/>  
            </C1>  
            <C2>  
            <xsl:value-of select='Child2'/>  
            </C2>  
        </Root>  
    </xsl:template>  
</xsl:stylesheet>";  
  
XDocument xmlTree = new XDocument(  
    new XElement("Parent",  
        new XElement("Child1", "Child1 data"),  
        new XElement("Child2", "Child2 data")  
    )  
);  
  
XDocument newTree = new XDocument();  
using (XmlWriter writer = newTree.CreateWriter()) {  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="4b245-112">Este ejemplo produce el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="4b245-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b245-113">Vea también</span><span class="sxs-lookup"><span data-stu-id="4b245-113">See also</span></span>

- [<span data-ttu-id="4b245-114">Serializar árboles XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4b245-114">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)

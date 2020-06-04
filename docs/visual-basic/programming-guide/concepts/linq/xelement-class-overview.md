---
title: Información general de la clase XElement
ms.date: 07/20/2015
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
ms.openlocfilehash: a0e50c8a5a14150ee09a328f4dcdd5bc88363621
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413224"
---
# <a name="xelement-class-overview-visual-basic"></a>Información general de la clase XElement (Visual Basic)
La clase <xref:System.Xml.Linq.XElement> es una de las clases fundamentales de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Representa a un elemento XML. Puede utilizar esta clase para crear elementos; cambiar el contenido del elemento; agregar, modificar o eliminar elementos secundarios; agregar atributos a un elemento; o serializar el contenido de un elemento en forma de texto. También puede operar con otras clases de <xref:System.Xml?displayProperty=nameWithType>, como son <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> y <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="xelement-functionality"></a>Funcionalidad de XElement  
 Este tema describe la funcionalidad que ofrece la clase <xref:System.Xml.Linq.XElement>.  
  
### <a name="constructing-xml-trees"></a>Construir árboles XML  
 Es posible construir árboles XML de diferentes formas, entre las que se incluyen las siguientes:  
  
- Puede construir un árbol XML mediante código. Para obtener más información, vea [crear árboles XML (Visual Basic)](creating-xml-trees.md).  
  
- Puede analizar XML a partir de diferentes orígenes, incluyendo un <xref:System.IO.TextReader>, archivos de texto o direcciones web (URL). Para obtener más información, vea [analizar XML (Visual Basic)](parsing-xml.md).  
  
- También puede utilizar un <xref:System.Xml.XmlReader> para rellenar el árbol. Para obtener más información, vea <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
- Si dispone de un módulo que pueda escribir contenidos en un <xref:System.Xml.XmlWriter>, puede utilizar el método <xref:System.Xml.Linq.XContainer.CreateWriter%2A> para crear un sistema de escritura, para pasar éste al módulo y para utilizar después el contenido que se haya escrito en <xref:System.Xml.XmlWriter> para rellenar el árbol XML.  
  
 No obstante, la forma más habitual de crear un árbol XML es la siguiente:  
  
```vb  
Dim contacts As XElement = _  
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
  
 Otra técnica que se usa con frecuencia para crear un árbol XML implica el uso de los resultados de una consulta LINK para rellenar el árbol XML, tal y como se muestra en el ejemplo siguiente:  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 Este ejemplo produce el siguiente resultado:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a>Serializar árboles XML  
 Puede serializar un árbol XML en un <xref:System.IO.File>, un <xref:System.IO.TextWriter> o en un <xref:System.Xml.XmlWriter>.  
  
 Para obtener más información, vea [serializar árboles XML (Visual Basic)](serializing-xml-trees.md).  
  
### <a name="retrieving-xml-data-via-axis-methods"></a>Recuperar datos XML mediante los métodos de los ejes  
 Puede utilizar los métodos de los ejes para recuperar atributos, elementos secundarios, elementos descendientes y elementos antecesores. Las consultas LINK operan sobre métodos de eje y proporcionan varias formas flexibles y eficaces de recorrer y procesar árboles XML.  
  
 Para obtener más información, vea [ejes de LINQ to XML (Visual Basic)](linq-to-xml-axes.md).  
  
### <a name="querying-xml-trees"></a>Consultar árboles XML  
 Puede escribir consultas LINK que extraigan datos de un árbol XML.  
  
 Para obtener más información, vea [consultar árboles XML (Visual Basic)](querying-xml-trees.md).  
  
### <a name="modifying-xml-trees"></a>Modificar árboles XML  
 Puede modificar un elemento de diferentes maneras, incluyendo el cambiar su contenido o sus atributos. También puede eliminar un elemento dependiente de un elemento primario.  
  
 Para obtener más información, vea [modificar árboles XML (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md).  
  
## <a name="see-also"></a>Consulte también

- [Información general sobre la programación de LINQ to XML (Visual Basic)](linq-to-xml-programming-overview.md)

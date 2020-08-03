---
title: Procedimiento para recuperar un único atributo (LINQ to XML) (C#)
description: Aprenda a usar LINQ to XML para recuperar un solo atributo de un elemento de C#, dado el nombre del atributo.
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 4efcae5324ad5a2e4664e68e35e15ec2053daece
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103440"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a>Procedimiento para recuperar un único atributo (LINQ to XML) (C#)
Este tema explica cómo recuperar un atributo concreto de un elemento, proporcionando el nombre del atributo. Esto puede resultar útil para escribir expresiones de consulta mediante las cuales encontrar un elemento que contiene un atributo en particular.  
  
 El método <xref:System.Xml.Linq.XElement.Attribute%2A> de la clase <xref:System.Xml.Linq.XElement> devuelve el <xref:System.Xml.Linq.XAttribute> con el nombre especificado.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo utiliza el método <xref:System.Xml.Linq.XElement.Attribute%2A>.  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 Este ejemplo encuentra todos los descendientes en el árbol cuyo nombre es `Phone` y, a continuación, encuentra aquel atributo cuyo nombre es `type`.  
  
 Este código genera el siguiente resultado:  
  
```output  
home  
work  
```  
  
## <a name="example"></a>Ejemplo  
 Si desea recuperar el valor del atributo, puede convertirlo, de la misma forma que lo haría con los objetos <xref:System.Xml.Linq.XElement>. En el siguiente ejemplo se muestra cómo hacerlo.  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 Este código genera el siguiente resultado:  
  
```output  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] proporciona operadores de conversión explícita para la clase <xref:System.Xml.Linq.XAttribute> a `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` y `GUID?`.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo muestra el mismo código para un atributo que se encuentre en un espacio de nombres. Para más información, consulte [Información general sobre los espacios de nombres (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement cust = new XElement(aw + "PhoneNumbers",  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "home"),  
        "555-555-5555"),  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants(aw + "Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute(aw + "type"));  
```  
  
 Este código genera el siguiente resultado:  
  
```output  
home  
work  
```  
  
## <a name="see-also"></a>Vea también

- [Ejes de LINQ to XML (C#)](./linq-to-xml-axes-overview.md)

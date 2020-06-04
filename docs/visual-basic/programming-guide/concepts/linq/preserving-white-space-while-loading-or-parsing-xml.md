---
title: Conservar el espacio en blanco al cargar o analizar XML
ms.date: 07/20/2015
ms.assetid: ef6518e0-2c8d-462c-8b92-a16e9dc737ad
ms.openlocfilehash: 9c60c707730ed0b07e82040a4ce3aab5d83eef1c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396446"
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>Mantener un espacio en blanco al cargar o analizar XML
En este tema se describe cómo controlar el comportamiento de los espacios en blanco de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Un caso muy común es aquel en el que se leen datos XML con sangría, se crea un árbol XML en memoria sin ningún nodo de texto con espacios en blanco (es decir, sin preservar los espacios en blanco), se realizan ciertas operaciones sobre el XML y éste se guarda con sangría. Si se serializa el XML con formato, solo se preservan en el XML aquellos espacios en blanco más significativos. Éste es el comportamiento predeterminado en [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Otro escenario muy común es aquel en el que se lee y se modifica código XML en el que se ha aplicado sangría de forma intencionada. Es posible que no desee modificar esta sangría de ninguna forma. Para hacerlo en [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], puede preservar los espacios en blanco a la hora de cargar o analizar el XML y si deshabilita el formato cuando serialice el XML.  
  
 En este tema se describe el comportamiento de espacios en blanco de métodos que rellenan los árboles XML. Para obtener información sobre cómo controlar los espacios en blanco al serializar árboles XML, consulte [Mantener un espacio en blanco al serializar](preserving-white-space-while-serializing.md).  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>Comportamiento de métodos que rellenan árboles XML  
 Los siguientes métodos de las clases <xref:System.Xml.Linq.XElement> y <xref:System.Xml.Linq.XDocument> rellenan un árbol XML. Puede rellenar un árbol XML desde un archivo, un <xref:System.IO.TextReader>, un <xref:System.Xml.XmlReader> o una cadena:  
  
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 Si el método no toma <xref:System.Xml.Linq.LoadOptions> como argumento, el método no conservará espacios en blanco no significativos.  
  
 En la mayoría de casos, si el método toma <xref:System.Xml.Linq.LoadOptions> como argumento, opcionalmente se pueden conservar los espacios en blanco no significativos como nodos de texto en el árbol XML. No obstante, si el método carga XML desde <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReader> determina si los espacios en blanco se conservan. Establecer <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> no tendrá ningún efecto.  
  
 Con estos métodos, si se conservan los espacios en blanco, se inserta un espacio en blanco insignificante en el árbol XML como nodos <xref:System.Xml.Linq.XText>. Si no se conservan los espacios en blanco, entonces no se insertan los nodos de texto.  
  
 Puede crear un árbol XML mediante <xref:System.Xml.XmlWriter>. Los nodos escritos en <xref:System.Xml.XmlWriter> se rellenan en el árbol. No obstante, al crear un árbol XML usando este método se conservan todos los nodos, independientemente de si el nodo es o no un espacio en blanco, o si el espacio en blanco es o no significativo.  
  
## <a name="see-also"></a>Consulte también

- [Analizar XML (Visual Basic)](parsing-xml.md)

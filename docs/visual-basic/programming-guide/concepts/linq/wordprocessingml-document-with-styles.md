---
title: Documento WordprocessingML con Styles2
ms.date: 07/20/2015
ms.assetid: a9136e4d-c368-4661-8049-7d45c679a236
ms.openlocfilehash: caf80014077bf57dc1ffb8eaeac6390cf4258015
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403555"
---
# <a name="wordprocessingml-document-with-styles"></a><span data-ttu-id="d0a15-102">Documento de WordprocessingML con estilos</span><span class="sxs-lookup"><span data-stu-id="d0a15-102">WordprocessingML Document with Styles</span></span>
<span data-ttu-id="d0a15-103">Los documentos WordprocessingML más complicados tienen párrafos formateados con estilos.</span><span class="sxs-lookup"><span data-stu-id="d0a15-103">More complicated WordprocessingML documents have paragraphs that are formatted with styles.</span></span>  
  
 <span data-ttu-id="d0a15-104">Resultan útiles algunas indicaciones acerca de la creación de documentos WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="d0a15-104">A few notes about the makeup of WordprocessingML documents are helpful.</span></span> <span data-ttu-id="d0a15-105">Los documentos WordprocessingML se almacenan en paquetes.</span><span class="sxs-lookup"><span data-stu-id="d0a15-105">WordprocessingML documents are stored in packages.</span></span> <span data-ttu-id="d0a15-106">Los paquetes tienen varias partes. Éstas tienen un significado explícito si se usan el contexto de los paquetes; básicamente, las partes son archivos que se comprimen para formar un paquete.</span><span class="sxs-lookup"><span data-stu-id="d0a15-106">Packages have multiple parts (parts have an explicit meaning when used in the context of packages; essentially, parts are files that are zipped together to comprise a package).</span></span> <span data-ttu-id="d0a15-107">Si un documento contiene párrafos que se formatean con estilos, habrá una parte de documento que contendrá párrafos con estilos aplicados a éstos.</span><span class="sxs-lookup"><span data-stu-id="d0a15-107">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them.</span></span> <span data-ttu-id="d0a15-108">También habrá una parte de estilo que contendrá los estilos a los que hace referencia el documento.</span><span class="sxs-lookup"><span data-stu-id="d0a15-108">There will also be a style part that contains the styles that are referred to by the document.</span></span>  
  
 <span data-ttu-id="d0a15-109">Cuando se obtiene acceso a los paquetes, es importante hacerlo mediante la relación entre las partes, en lugar de usar una ruta de acceso arbitraria.</span><span class="sxs-lookup"><span data-stu-id="d0a15-109">When accessing packages, it is important that you do so through the relationships between parts, rather than using an arbitrary path.</span></span> <span data-ttu-id="d0a15-110">Este problema se encuentra fuera del ámbito del tutorial Manipular contenido en un documento de WordprocessingML, aunque los programas de ejemplo incluidos en este tutorial demuestran el método correcto.</span><span class="sxs-lookup"><span data-stu-id="d0a15-110">This issue is beyond the scope of the Manipulating Content in a WordprocessingML Document tutorial, but the example programs that are included in this tutorial demonstrate the correct approach.</span></span>  
  
## <a name="a-document-that-uses-styles"></a><span data-ttu-id="d0a15-111">Documento que usa estilos</span><span class="sxs-lookup"><span data-stu-id="d0a15-111">A Document that Uses Styles</span></span>  
 <span data-ttu-id="d0a15-112">El ejemplo de WordML presentado en el tema [forma de documentos WordprocessingML (Visual Basic)](shape-of-wordprocessingml-documents.md) es muy sencillo.</span><span class="sxs-lookup"><span data-stu-id="d0a15-112">The WordML example presented in the [Shape of WordprocessingML Documents (Visual Basic)](shape-of-wordprocessingml-documents.md) topic is a very simple one.</span></span> <span data-ttu-id="d0a15-113">El documento siguiente es más complicado: tiene párrafos que están formateados con estilos.</span><span class="sxs-lookup"><span data-stu-id="d0a15-113">The following document is more complicated: It has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="d0a15-114">La forma más fácil de ver el XML que conforma un documento XML abierto de Office es ejecutar el [ejemplo que genera elementos de documento de Office Open XML (Visual Basic)](example-that-outputs-office-open-xml-document-parts.md).</span><span class="sxs-lookup"><span data-stu-id="d0a15-114">The easiest way to see the XML that makes up an Office Open XML document is to run the [Example that Outputs Office Open XML Document Parts (Visual Basic)](example-that-outputs-office-open-xml-document-parts.md).</span></span>  
  
 <span data-ttu-id="d0a15-115">En el documento siguiente, el primer párrafo tiene el estilo `Heading1`.</span><span class="sxs-lookup"><span data-stu-id="d0a15-115">In the following document, the first paragraph has the style `Heading1`.</span></span> <span data-ttu-id="d0a15-116">Hay varios párrafos que tienen el estilo predeterminado.</span><span class="sxs-lookup"><span data-stu-id="d0a15-116">There are a number of paragraphs that have the default style.</span></span> <span data-ttu-id="d0a15-117">Asimismo, existen diversos párrafos con el estilo `Code`.</span><span class="sxs-lookup"><span data-stu-id="d0a15-117">There are also a number of paragraphs that have the style `Code`.</span></span> <span data-ttu-id="d0a15-118">Debido a esta complejidad relativa, resulta más interesante analizar este documento con LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="d0a15-118">Because of this relative complexity, this is a more interesting document to parse with LINQ to XML.</span></span>  
  
 <span data-ttu-id="d0a15-119">En los párrafos con estilos no predeterminados, los elementos de párrafo tienen un elemento secundario llamado `w:pPr`, que a su vez tiene un elemento secundario `w:pStyle`.</span><span class="sxs-lookup"><span data-stu-id="d0a15-119">In those paragraphs with non-default styles, the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="d0a15-120">El elemento tiene un atributo, `w:val`, que contiene el nombre de estilo.</span><span class="sxs-lookup"><span data-stu-id="d0a15-120">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="d0a15-121">Si el párrafo tiene el estilo predeterminado, significa que el elemento de párrafo no tiene un elemento secundario `w:p.Pr`.</span><span class="sxs-lookup"><span data-stu-id="d0a15-121">If the paragraph has the default style, it means that the paragraph element does not have a `w:p.Pr` child element.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<w:document  
    xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:o="urn:schemas-microsoft-com:office:office"  
    xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
    xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
    xmlns:v="urn:schemas-microsoft-com:vml"  
    xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
    xmlns:w10="urn:schemas-microsoft-com:office:word"  
    xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
    xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Heading1" />  
      </w:pPr>  
      <w:r>  
        <w:t>Parsing WordprocessingML with LINQ to XML</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">  
      <w:r>  
        <w:t>The following example prints to the console.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r>  
        <w:t>using System;</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>class Program {</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">    public static void </w:t>  
      </w:r>  
      <w:smartTag w:uri="urn:schemas-microsoft-com:office:smarttags" w:element="place">  
        <w:r w:rsidRPr="00876F34">  
          <w:t>Main</w:t>  
        </w:r>  
      </w:smartTag>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>(string[] args) {</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">        Console.WriteLine("Hello World");</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">    }</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>}</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">  
      <w:r>  
        <w:t>This example produces the following output:</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r>  
        <w:t>Hello World</w:t>  
      </w:r>  
    </w:p>  
    <w:sectPr w:rsidR="00A75AE0" w:rsidSect="00A75AE0">  
      <w:pgSz w:w="12240" w:h="15840" />  
      <w:pgMar w:top="1440" w:right="1800" w:bottom="1440" w:left="1800" w:header="720" w:footer="720" w:gutter="0" />  
      <w:cols w:space="720" />  
      <w:docGrid w:linePitch="360" />  
    </w:sectPr>  
  </w:body>  
</w:document>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0a15-122">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d0a15-122">See also</span></span>

- [<span data-ttu-id="d0a15-123">Detalles de los documentos WordprocessingML de Office Open XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0a15-123">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](details-of-office-open-xml-wordprocessingml-documents.md)

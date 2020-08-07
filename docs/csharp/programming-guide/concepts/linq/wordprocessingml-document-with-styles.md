---
title: Documento de WordprocessingML con estilos
description: Este documento WordprocessingML de ejemplo tiene párrafos que están formateados con estilos. Conozca las partes del documento que pertenecen a los estilos.
ms.date: 07/20/2015
ms.assetid: 40e35de6-ac93-4bba-88ab-a018cbe93873
ms.openlocfilehash: b799c1bee95d7d638e6a3210b4876ff036e088eb
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302209"
---
# <a name="wordprocessingml-document-with-styles"></a><span data-ttu-id="d2ba2-104">Documento de WordprocessingML con estilos</span><span class="sxs-lookup"><span data-stu-id="d2ba2-104">WordprocessingML Document with Styles</span></span>
<span data-ttu-id="d2ba2-105">Los documentos WordprocessingML más complicados tienen párrafos formateados con estilos.</span><span class="sxs-lookup"><span data-stu-id="d2ba2-105">More complicated WordprocessingML documents have paragraphs that are formatted with styles.</span></span>  
  
 <span data-ttu-id="d2ba2-106">Resultan útiles algunas indicaciones acerca de la creación de documentos WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="d2ba2-106">A few notes about the makeup of WordprocessingML documents are helpful.</span></span> <span data-ttu-id="d2ba2-107">Los documentos WordprocessingML se almacenan en paquetes.</span><span class="sxs-lookup"><span data-stu-id="d2ba2-107">WordprocessingML documents are stored in packages.</span></span> <span data-ttu-id="d2ba2-108">Los paquetes tienen varias partes. Éstas tienen un significado explícito si se usan el contexto de los paquetes; básicamente, las partes son archivos que se comprimen para formar un paquete.</span><span class="sxs-lookup"><span data-stu-id="d2ba2-108">Packages have multiple parts (parts have an explicit meaning when used in the context of packages; essentially, parts are files that are zipped together to comprise a package).</span></span> <span data-ttu-id="d2ba2-109">Si un documento contiene párrafos que se formatean con estilos, habrá una parte de documento que contendrá párrafos con estilos aplicados a éstos.</span><span class="sxs-lookup"><span data-stu-id="d2ba2-109">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them.</span></span> <span data-ttu-id="d2ba2-110">También habrá una parte de estilo que contendrá los estilos a los que hace referencia el documento.</span><span class="sxs-lookup"><span data-stu-id="d2ba2-110">There will also be a style part that contains the styles that are referred to by the document.</span></span>  
  
 <span data-ttu-id="d2ba2-111">Cuando se obtiene acceso a los paquetes, es importante hacerlo mediante la relación entre las partes, en lugar de usar una ruta de acceso arbitraria.</span><span class="sxs-lookup"><span data-stu-id="d2ba2-111">When accessing packages, it is important that you do so through the relationships between parts, rather than using an arbitrary path.</span></span> <span data-ttu-id="d2ba2-112">Este problema se encuentra fuera del ámbito del tutorial Manipular contenido en un documento de WordprocessingML, aunque los programas de ejemplo incluidos en este tutorial demuestran el método correcto.</span><span class="sxs-lookup"><span data-stu-id="d2ba2-112">This issue is beyond the scope of the Manipulating Content in a WordprocessingML Document tutorial, but the example programs that are included in this tutorial demonstrate the correct approach.</span></span>  
  
## <a name="a-document-that-uses-styles"></a><span data-ttu-id="d2ba2-113">Documento que usa estilos</span><span class="sxs-lookup"><span data-stu-id="d2ba2-113">A Document that Uses Styles</span></span>  
 <span data-ttu-id="d2ba2-114">El ejemplo de WordML presentado en el tema [Forma de documentos de WordprocessingML](./shape-of-wordprocessingml-documents.md) es muy simple.</span><span class="sxs-lookup"><span data-stu-id="d2ba2-114">The WordML example presented in the [Shape of WordprocessingML Documents (C#)](./shape-of-wordprocessingml-documents.md) topic is a very simple one.</span></span> <span data-ttu-id="d2ba2-115">El documento siguiente es más complicado: tiene párrafos formateados con estilos.</span><span class="sxs-lookup"><span data-stu-id="d2ba2-115">The following document is more complicated: It has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="d2ba2-116">La forma más fácil de ver el XML que forma un documento de Office Open XML consiste en ejecutar el [Ejemplo que da como resultado partes de un documento de Office Open XML (C#)](./example-that-outputs-office-open-xml-document-parts.md).</span><span class="sxs-lookup"><span data-stu-id="d2ba2-116">The easiest way to see the XML that makes up an Office Open XML document is to run the [Example that Outputs Office Open XML Document Parts (C#)](./example-that-outputs-office-open-xml-document-parts.md).</span></span>  
  
 <span data-ttu-id="d2ba2-117">En el documento siguiente, el primer párrafo tiene el estilo `Heading1`.</span><span class="sxs-lookup"><span data-stu-id="d2ba2-117">In the following document, the first paragraph has the style `Heading1`.</span></span> <span data-ttu-id="d2ba2-118">Hay varios párrafos que tienen el estilo predeterminado.</span><span class="sxs-lookup"><span data-stu-id="d2ba2-118">There are a number of paragraphs that have the default style.</span></span> <span data-ttu-id="d2ba2-119">Asimismo, existen diversos párrafos con el estilo `Code`.</span><span class="sxs-lookup"><span data-stu-id="d2ba2-119">There are also a number of paragraphs that have the style `Code`.</span></span> <span data-ttu-id="d2ba2-120">Debido a esta complejidad relativa, resulta más interesante analizar este documento con LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="d2ba2-120">Because of this relative complexity, this is a more interesting document to parse with LINQ to XML.</span></span>  
  
 <span data-ttu-id="d2ba2-121">En los párrafos con estilos no predeterminados, los elementos de párrafo tienen un elemento secundario llamado `w:pPr`, que a su vez tiene un elemento secundario `w:pStyle`.</span><span class="sxs-lookup"><span data-stu-id="d2ba2-121">In those paragraphs with non-default styles, the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="d2ba2-122">El elemento tiene un atributo, `w:val`, que contiene el nombre de estilo.</span><span class="sxs-lookup"><span data-stu-id="d2ba2-122">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="d2ba2-123">Si el párrafo tiene el estilo predeterminado, significa que el elemento de párrafo no tiene un elemento secundario `w:p.Pr`.</span><span class="sxs-lookup"><span data-stu-id="d2ba2-123">If the paragraph has the default style, it means that the paragraph element does not have a `w:p.Pr` child element.</span></span>  
  
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

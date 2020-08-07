---
title: <list> - Guía de programación de C#
description: Aprenda sobre la etiqueta XML <list> . Esta etiqueta se usa para crear tablas y definiciones, viñetas o listas numeradas mediante bloques "item".
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: 361c2e6f343554a9b8519c3b2e41219b209e682d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381871"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="948df-105">\<list> (guía de programación de C#)</span><span class="sxs-lookup"><span data-stu-id="948df-105">\<list> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="948df-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="948df-106">Syntax</span></span>

```xml
<list type="bullet|number|table">
    <listheader>
        <term>term</term>
        <description>description</description>
    </listheader>
    <item>
        <term>term</term>
        <description>description</description>
    </item>
</list>
```

## <a name="parameters"></a><span data-ttu-id="948df-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="948df-107">Parameters</span></span>

- `term`

  <span data-ttu-id="948df-108">Término que se define en `description`.</span><span class="sxs-lookup"><span data-stu-id="948df-108">A term to define, which will be defined in `description`.</span></span>

- `description`

  <span data-ttu-id="948df-109">Elemento de una lista numerada o con viñetas, o definición de un `term`.</span><span class="sxs-lookup"><span data-stu-id="948df-109">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="948df-110">Comentarios</span><span class="sxs-lookup"><span data-stu-id="948df-110">Remarks</span></span>

<span data-ttu-id="948df-111">El bloque `<listheader>` se usa para definir la fila de encabezado de una tabla o de una lista de definiciones.</span><span class="sxs-lookup"><span data-stu-id="948df-111">The `<listheader>` block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="948df-112">Cuando se define una tabla, solo es necesario suministrar una entrada para un término en el encabezado.</span><span class="sxs-lookup"><span data-stu-id="948df-112">When defining a table, you only need to supply an entry for term in the heading.</span></span>

<span data-ttu-id="948df-113">Cada elemento de la lista se especifica con un bloque `<item>`.</span><span class="sxs-lookup"><span data-stu-id="948df-113">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="948df-114">Cuando se crea una lista de definiciones, se deberán especificar tanto `term` como `description`.</span><span class="sxs-lookup"><span data-stu-id="948df-114">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="948df-115">En cambio, para una tabla, lista con viñetas o lista numerada, solo es necesario suministrar una entrada para `description`.</span><span class="sxs-lookup"><span data-stu-id="948df-115">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>

<span data-ttu-id="948df-116">Una lista o una tabla pueden tener tantos bloques `<item>` como sean necesarios.</span><span class="sxs-lookup"><span data-stu-id="948df-116">A list or table can have as many `<item>` blocks as needed.</span></span>

<span data-ttu-id="948df-117">Compile con [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para procesar los comentarios de documentación de un archivo.</span><span class="sxs-lookup"><span data-stu-id="948df-117">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="948df-118">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="948df-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a><span data-ttu-id="948df-119">Vea también</span><span class="sxs-lookup"><span data-stu-id="948df-119">See also</span></span>

- [<span data-ttu-id="948df-120">Guía de programación de C#</span><span class="sxs-lookup"><span data-stu-id="948df-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="948df-121">Etiquetas recomendadas para los comentarios de documentación</span><span class="sxs-lookup"><span data-stu-id="948df-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)

---
title: <c> - Guía de programación de C#
description: Aprenda sobre la etiqueta XML <c>. Esta etiqueta marca el texto de una sola línea en una descripción como código, mientras que <code> indicates multiple lines..
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: 78e59e1df4b096782e0a97b6d12c21c843a1cb21
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382027"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="7a3bc-104">\<c> (guía de programación de C#)</span><span class="sxs-lookup"><span data-stu-id="7a3bc-104">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="7a3bc-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7a3bc-105">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="7a3bc-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7a3bc-106">Parameters</span></span>

- `text`

  <span data-ttu-id="7a3bc-107">El texto que le gustaría indicar como código.</span><span class="sxs-lookup"><span data-stu-id="7a3bc-107">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a3bc-108">Comentarios</span><span class="sxs-lookup"><span data-stu-id="7a3bc-108">Remarks</span></span>

<span data-ttu-id="7a3bc-109">La etiqueta `<c>` le proporciona una manera de indicar que el texto dentro de una descripción debe marcarse como código.</span><span class="sxs-lookup"><span data-stu-id="7a3bc-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="7a3bc-110">Use [\<code>](./code.md) para indicar varias líneas como código.</span><span class="sxs-lookup"><span data-stu-id="7a3bc-110">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="7a3bc-111">Compile con [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para procesar los comentarios de documentación de un archivo.</span><span class="sxs-lookup"><span data-stu-id="7a3bc-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="7a3bc-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7a3bc-112">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="7a3bc-113">Vea también</span><span class="sxs-lookup"><span data-stu-id="7a3bc-113">See also</span></span>

- [<span data-ttu-id="7a3bc-114">Guía de programación de C#</span><span class="sxs-lookup"><span data-stu-id="7a3bc-114">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="7a3bc-115">Etiquetas recomendadas para los comentarios de documentación</span><span class="sxs-lookup"><span data-stu-id="7a3bc-115">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)

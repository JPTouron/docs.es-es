---
title: No se admite la inferencia de tipos que acepten valores NULL en este contexto
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 52e5391fbcf30a4dada4d64a0e810c900ea85806
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409392"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="7ba1e-102">No se admite la inferencia de tipos que acepten valores NULL en este contexto</span><span class="sxs-lookup"><span data-stu-id="7ba1e-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="7ba1e-103">Los tipos de valor y las estructuras se pueden declarar como valores NULL.</span><span class="sxs-lookup"><span data-stu-id="7ba1e-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="7ba1e-104">Sin embargo, no puede utilizar la declaración que acepta valores NULL en combinación con la inferencia de tipos.</span><span class="sxs-lookup"><span data-stu-id="7ba1e-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="7ba1e-105">En los ejemplos siguientes se produce este error.</span><span class="sxs-lookup"><span data-stu-id="7ba1e-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="7ba1e-106">**Identificador de error:** BC36629</span><span class="sxs-lookup"><span data-stu-id="7ba1e-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7ba1e-107">Para corregir este error</span><span class="sxs-lookup"><span data-stu-id="7ba1e-107">To correct this error</span></span>  
  
- <span data-ttu-id="7ba1e-108">Use una `As` cláusula para declarar la variable como un tipo de valor que acepta valores NULL.</span><span class="sxs-lookup"><span data-stu-id="7ba1e-108">Use an `As` clause to declare the variable as a nullable value type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ba1e-109">Consulte también</span><span class="sxs-lookup"><span data-stu-id="7ba1e-109">See also</span></span>

- [<span data-ttu-id="7ba1e-110">Tipos de valor que aceptan valores NULL</span><span class="sxs-lookup"><span data-stu-id="7ba1e-110">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="7ba1e-111">Inferencia de tipo de variable local</span><span class="sxs-lookup"><span data-stu-id="7ba1e-111">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)

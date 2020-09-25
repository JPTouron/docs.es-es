---
title: COLLECTION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: c960ee69f8188f6dd3184b6fb31f3432f8d58fee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197955"
---
# <a name="collection-entity-sql"></a><span data-ttu-id="c49c6-102">COLLECTION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c49c6-102">COLLECTION (Entity SQL)</span></span>

<span data-ttu-id="c49c6-103">La palabra clave COLLECTION solo se usa en la definición de una función inline.</span><span class="sxs-lookup"><span data-stu-id="c49c6-103">The COLLECTION keyword is only used in the definition of an inline function.</span></span> <span data-ttu-id="c49c6-104">Las funciones de colección son funciones que operan en una colección de valores y generan un resultado escalar.</span><span class="sxs-lookup"><span data-stu-id="c49c6-104">Collection functions are functions that operate on a collection of values and produce a scalar output.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c49c6-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c49c6-105">Syntax</span></span>  
  
```csharp  
COLLECTION(type_definition)
```  
  
## <a name="arguments"></a><span data-ttu-id="c49c6-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="c49c6-106">Arguments</span></span>  

 `type_definition`  
 <span data-ttu-id="c49c6-107">Una expresión que devuelve una colección de tipos, filas o referencias compatibles.</span><span class="sxs-lookup"><span data-stu-id="c49c6-107">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c49c6-108">Observaciones</span><span class="sxs-lookup"><span data-stu-id="c49c6-108">Remarks</span></span>  

 <span data-ttu-id="c49c6-109">Para obtener más información sobre la palabra clave COLLECTION, vea [Type Definitions](type-definitions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c49c6-109">For more information about the COLLECTION keyword, see [Type Definitions](type-definitions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c49c6-110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c49c6-110">Example</span></span>  

 <span data-ttu-id="c49c6-111">En el ejemplo siguiente se muestra cómo usar la palabra clave COLLECTION para declarar una colección de decimales como un argumento para una función inline de consulta.</span><span class="sxs-lookup"><span data-stu-id="c49c6-111">The following sample shows how to use the COLLECTION keyword to declare a collection of decimals as an argument for an inline query function.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a><span data-ttu-id="c49c6-112">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c49c6-112">See also</span></span>

- [<span data-ttu-id="c49c6-113">Referencia de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c49c6-113">Entity SQL Reference</span></span>](entity-sql-reference.md)

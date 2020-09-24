---
title: Procedimiento para representar columnas calculadas
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: d952a6c22cd96bbc89aeebfa4b13e9727a363c73
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166331"
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="ef4d0-102">Procedimiento para representar columnas calculadas</span><span class="sxs-lookup"><span data-stu-id="ef4d0-102">How to: Represent Computed Columns</span></span>

<span data-ttu-id="ef4d0-103">Utilice la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> propiedad en un <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para representar una columna cuyo contenido es el resultado del cálculo.</span><span class="sxs-lookup"><span data-stu-id="ef4d0-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="ef4d0-104">Para obtener ejemplos de código, vea <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef4d0-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ef4d0-105">no admite las columnas calculadas como claves principales.</span><span class="sxs-lookup"><span data-stu-id="ef4d0-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="ef4d0-106">Para representar una columna calculada</span><span class="sxs-lookup"><span data-stu-id="ef4d0-106">To represent a computed column</span></span>  
  
1. <span data-ttu-id="ef4d0-107">Agregue la propiedad <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> al atributo <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ef4d0-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="ef4d0-108">Asigne una representación de cadena de la fórmula a la propiedad <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef4d0-108">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef4d0-109">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ef4d0-109">See also</span></span>

- [<span data-ttu-id="ef4d0-110">El modelo de objetos de LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ef4d0-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="ef4d0-111">Procedimiento para personalizar clases de entidades con el editor de código</span><span class="sxs-lookup"><span data-stu-id="ef4d0-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)

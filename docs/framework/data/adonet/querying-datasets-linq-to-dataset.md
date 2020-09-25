---
title: Consultar conjuntos de datos (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: f42cd792772a4e2b9f24ea8f76ea588da10d9c51
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184981"
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="3639f-102">Consultar conjuntos de datos (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="3639f-102">Querying DataSets (LINQ to DataSet)</span></span>

<span data-ttu-id="3639f-103">Después de rellenar un objeto <xref:System.Data.DataSet> con datos se puede empezar a realizar consultas sobre él.</span><span class="sxs-lookup"><span data-stu-id="3639f-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="3639f-104">La formulación de consultas con LINQ to DataSet es similar a usar Language-Integrated Query (LINQ) en otros orígenes de datos habilitados para LINQ.</span><span class="sxs-lookup"><span data-stu-id="3639f-104">Formulating queries with LINQ to DataSet is similar to using Language-Integrated Query (LINQ) against other LINQ-enabled data sources.</span></span> <span data-ttu-id="3639f-105">No obstante, recuerde que cuando utiliza consultas LINQ sobre un <xref:System.Data.DataSet> objeto, está consultando una enumeración de <xref:System.Data.DataRow> objetos en lugar de una enumeración de un tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="3639f-105">Remember, however, that when you use LINQ queries over a <xref:System.Data.DataSet> object, you're querying an enumeration of <xref:System.Data.DataRow> objects instead of an enumeration of a custom type.</span></span> <span data-ttu-id="3639f-106">Esto significa que puede usar cualquiera de los miembros de la <xref:System.Data.DataRow> clase en las consultas LINQ.</span><span class="sxs-lookup"><span data-stu-id="3639f-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your LINQ queries.</span></span> <span data-ttu-id="3639f-107">Esto permite crear consultas enriquecidas y complejas.</span><span class="sxs-lookup"><span data-stu-id="3639f-107">This lets you create rich, complex queries.</span></span>  
  
 <span data-ttu-id="3639f-108">Como con otras implementaciones de LINQ, puede crear LINQ to DataSet consultas de dos formas diferentes: sintaxis de expresiones de consulta y sintaxis de consulta basada en métodos.</span><span class="sxs-lookup"><span data-stu-id="3639f-108">As with other implementations of LINQ, you can create LINQ to DataSet queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="3639f-109">Puede usar la sintaxis de expresión de consulta o la sintaxis de consulta basada en métodos para realizar consultas en tablas únicas en un <xref:System.Data.DataSet>, en tablas múltiples en un <xref:System.Data.DataSet> o en tablas en un <xref:System.Data.DataSet> con tipo.</span><span class="sxs-lookup"><span data-stu-id="3639f-109">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3639f-110">En esta sección</span><span class="sxs-lookup"><span data-stu-id="3639f-110">In This Section</span></span>  

 [<span data-ttu-id="3639f-111">Consultas de tabla única</span><span class="sxs-lookup"><span data-stu-id="3639f-111">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="3639f-112">Describe cómo realizar consultas en una sola tabla.</span><span class="sxs-lookup"><span data-stu-id="3639f-112">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="3639f-113">Consultas entre tablas</span><span class="sxs-lookup"><span data-stu-id="3639f-113">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="3639f-114">Describe cómo realizar consultas entre tablas.</span><span class="sxs-lookup"><span data-stu-id="3639f-114">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="3639f-115">Consultar objetos DataSet con tipo</span><span class="sxs-lookup"><span data-stu-id="3639f-115">Querying Typed DataSets</span></span>](querying-typed-datasets.md)  
 <span data-ttu-id="3639f-116">Describe cómo consultar objetos <xref:System.Data.DataSet> con tipo.</span><span class="sxs-lookup"><span data-stu-id="3639f-116">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3639f-117">Consulte también</span><span class="sxs-lookup"><span data-stu-id="3639f-117">See also</span></span>

- [<span data-ttu-id="3639f-118">Ejemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="3639f-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="3639f-119">Cargar datos en un conjunto de datos</span><span class="sxs-lookup"><span data-stu-id="3639f-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)

---
title: Procedimiento para ejecutar una consulta que devuelve colecciones anidadas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
ms.openlocfilehash: 3bf6e08e7842fbf235b519680b81f79fba4a7228
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198410"
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a><span data-ttu-id="ce7a7-102">Procedimiento para ejecutar una consulta que devuelve colecciones anidadas</span><span class="sxs-lookup"><span data-stu-id="ce7a7-102">How to: Execute a Query that Returns Nested Collections</span></span>

<span data-ttu-id="ce7a7-103">Aquí se explica cómo ejecutar un comando en un modelo conceptual utilizando un objeto <xref:System.Data.EntityClient.EntityCommand> y cómo recuperar los  resultados de la colección anidados utilizando <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="ce7a7-103">This shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the nested collection results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="ce7a7-104">Para ejecutar el código de este ejemplo</span><span class="sxs-lookup"><span data-stu-id="ce7a7-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="ce7a7-105">Agregue el [modelo AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) al proyecto y configure el proyecto para usar el Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="ce7a7-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="ce7a7-106">Para obtener más información, consulte [Cómo: usar el Asistente para Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ce7a7-106">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="ce7a7-107">En la página de código de la aplicación, agregue las instrucciones `using` siguientes (`Imports` en Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="ce7a7-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="ce7a7-108">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ce7a7-108">Example</span></span>  

 <span data-ttu-id="ce7a7-109">Una *colección anidada* es una colección que está dentro de otra colección.</span><span class="sxs-lookup"><span data-stu-id="ce7a7-109">A *nested collection* is a collection that is inside another collection.</span></span> <span data-ttu-id="ce7a7-110">En el código siguiente se recupera una colección de `Contacts` y las colecciones anidadas de `SalesOrderHeaders` asociadas a cada `Contact`.</span><span class="sxs-lookup"><span data-stu-id="ce7a7-110">The following code retrieves a collection of `Contacts` and the nested collections of `SalesOrderHeaders` that are associated with each `Contact`.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="ce7a7-111">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ce7a7-111">See also</span></span>

- [<span data-ttu-id="ce7a7-112">Proveedor de EntityClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="ce7a7-112">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)

---
title: Procedimiento para ejecutar un procedimiento almacenado parametrizado mediante EntityCommand
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: 7a055fc3e62821285fe2b6e1333d516c477d025b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549762"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a><span data-ttu-id="d8ae9-102">Procedimiento para ejecutar un procedimiento almacenado parametrizado mediante EntityCommand</span><span class="sxs-lookup"><span data-stu-id="d8ae9-102">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>
<span data-ttu-id="d8ae9-103">En este tema se muestra cómo ejecutar un procedimiento almacenado parametrizado usando la clase <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-103">This topic shows how to execute a parameterized stored procedure by using the <xref:System.Data.EntityClient.EntityCommand> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="d8ae9-104">Para ejecutar el código de este ejemplo</span><span class="sxs-lookup"><span data-stu-id="d8ae9-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="d8ae9-105">Agregue el [modelo School](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) al proyecto y configure el proyecto para que use el Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-105">Add the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="d8ae9-106">Para obtener más información, consulte [Cómo: usar el Asistente para Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d8ae9-106">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="d8ae9-107">En la página de código de la aplicación, agregue las instrucciones `using` siguientes (`Imports` en Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="d8ae9-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. <span data-ttu-id="d8ae9-108">Importe el procedimiento almacenado `GetStudentGrades` y especifique entidades `CourseGrade` como tipo de valor devuelto.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-108">Import the `GetStudentGrades` stored procedure and specify `CourseGrade` entities as a return type.</span></span> <span data-ttu-id="d8ae9-109">Para obtener información sobre cómo importar un procedimiento almacenado, consulte [Cómo: importar un procedimiento almacenado](/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d8ae9-109">For information on how to import a stored procedure, see [How to: Import a Stored Procedure](/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8ae9-110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d8ae9-110">Example</span></span>  
 <span data-ttu-id="d8ae9-111">El código siguiente ejecuta el procedimiento almacenado `GetStudentGrades` donde `StudentId` es un parámetro necesario.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-111">The following code executes the `GetStudentGrades` stored procedure where `StudentId` is a required parameter.</span></span> <span data-ttu-id="d8ae9-112">Los resultados los lee después una clase <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-112">The results are then read by an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="d8ae9-113">Vea también</span><span class="sxs-lookup"><span data-stu-id="d8ae9-113">See also</span></span>

- [<span data-ttu-id="d8ae9-114">Proveedor de EntityClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="d8ae9-114">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)

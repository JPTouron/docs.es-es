---
title: Procedimiento para usar procedimientos almacenados que toman parámetros
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: a54e2ee553629179022b68658d44cbcb02ab590f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184968"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a><span data-ttu-id="a6f3a-102">Procedimiento para usar procedimientos almacenados que toman parámetros</span><span class="sxs-lookup"><span data-stu-id="a6f3a-102">How to: Use Stored Procedures that Take Parameters</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a6f3a-103">asigna los parámetros de salida a parámetros de referencia y, para los tipos de valor, declara el parámetro como que acepta valores NULL.</span><span class="sxs-lookup"><span data-stu-id="a6f3a-103">maps output parameters to reference parameters, and for value types declares the parameter as nullable.</span></span>  
  
 <span data-ttu-id="a6f3a-104">Para obtener un ejemplo de cómo usar un parámetro de entrada en una consulta que devuelve un conjunto de filas, vea [Cómo: devolver conjuntos de filas](how-to-return-rowsets.md).</span><span class="sxs-lookup"><span data-stu-id="a6f3a-104">For an example of how to use an input parameter in a query that returns a rowset, see [How to: Return Rowsets](how-to-return-rowsets.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6f3a-105">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a6f3a-105">Example</span></span>  

 <span data-ttu-id="a6f3a-106">En el ejemplo siguiente se utiliza un parámetro de entrada único (el identificador de cliente) y se devuelve un parámetro de salida (las ventas totales para ese cliente).</span><span class="sxs-lookup"><span data-stu-id="a6f3a-106">The following example takes a single input parameter (the customer ID) and returns an out parameter (the total sales for that customer).</span></span>  
  
```sql
CREATE PROCEDURE [dbo].[CustOrderTotal]
@CustomerID nchar(5),  
@TotalSales money OUTPUT  
AS  
SELECT @TotalSales = SUM(OD.UNITPRICE*(1-OD.DISCOUNT) * OD.QUANTITY)  
FROM ORDERS O, "ORDER DETAILS" OD  
where O.CUSTOMERID = @CustomerID AND O.ORDERID = OD.ORDERID  
```  
  
 [!code-csharp[DLinqSprox#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#2)]
 [!code-vb[DLinqSprox#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="a6f3a-107">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a6f3a-107">Example</span></span>  

 <span data-ttu-id="a6f3a-108">La llamada a este procedimiento almacenado sería como sigue:</span><span class="sxs-lookup"><span data-stu-id="a6f3a-108">You would call this stored procedure as follows:</span></span>  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a6f3a-109">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a6f3a-109">See also</span></span>

- [<span data-ttu-id="a6f3a-110">Procedimientos almacenados</span><span class="sxs-lookup"><span data-stu-id="a6f3a-110">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="a6f3a-111">Descargar bases de datos de ejemplo</span><span class="sxs-lookup"><span data-stu-id="a6f3a-111">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="a6f3a-112">Tipos de valor que aceptan valores NULL (C#)</span><span class="sxs-lookup"><span data-stu-id="a6f3a-112">Nullable Value Types (C#)</span></span>](../../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
- [<span data-ttu-id="a6f3a-113">Tipos que admiten valores null (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6f3a-113">Nullable Value Types (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)

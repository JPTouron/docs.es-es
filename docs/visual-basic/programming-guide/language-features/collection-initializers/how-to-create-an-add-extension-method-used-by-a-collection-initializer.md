---
title: Procedimiento para crear un método de extensión de adiciones usado por un inicializador de colección
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 4dbe6146b70181864a6717146071f9b93a1f583e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414574"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="caa50-102">Cómo: Crear un método de extensión Add usado por un inicializador de colección (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="caa50-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="caa50-103">Cuando se usa un inicializador de colección para crear una colección, el compilador Visual Basic busca un `Add` método del tipo de colección para el que los parámetros del `Add` método coinciden con los tipos de los valores del inicializador de colección.</span><span class="sxs-lookup"><span data-stu-id="caa50-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="caa50-104">Este `Add` método se usa para rellenar la colección con los valores del inicializador de colección.</span><span class="sxs-lookup"><span data-stu-id="caa50-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="caa50-105">Si no `Add` existe ningún método coincidente y no se puede modificar el código de la colección, puede Agregar un método de extensión denominado `Add` que toma los parámetros necesarios para el inicializador de colección.</span><span class="sxs-lookup"><span data-stu-id="caa50-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="caa50-106">Normalmente, esto es lo que debe hacer cuando se usan inicializadores de colección para colecciones genéricas.</span><span class="sxs-lookup"><span data-stu-id="caa50-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="caa50-107">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="caa50-107">Example</span></span>  
 <span data-ttu-id="caa50-108">En el ejemplo siguiente se muestra cómo agregar un método de extensión al <xref:System.Collections.Generic.List%601> tipo genérico para que se pueda utilizar un inicializador de colección para agregar objetos de tipo `Employee` .</span><span class="sxs-lookup"><span data-stu-id="caa50-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="caa50-109">El método de extensión le permite usar la sintaxis de inicializador de colección abreviada.</span><span class="sxs-lookup"><span data-stu-id="caa50-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="caa50-110">Consulte también</span><span class="sxs-lookup"><span data-stu-id="caa50-110">See also</span></span>

- [<span data-ttu-id="caa50-111">Inicializadores de colección</span><span class="sxs-lookup"><span data-stu-id="caa50-111">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="caa50-112">Procedimiento para crear una colección usada por un inicializador de colección</span><span class="sxs-lookup"><span data-stu-id="caa50-112">How to: Create a Collection Used by a Collection Initializer</span></span>](how-to-create-a-collection-used-by-a-collection-initializer.md)

---
title: Procedimiento para asignar jerarquías de herencia
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: c0709fde96a5d2f39f04a08ccd24ddf90c782f30
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166422"
---
# <a name="how-to-map-inheritance-hierarchies"></a><span data-ttu-id="c42f6-102">Procedimiento para asignar jerarquías de herencia</span><span class="sxs-lookup"><span data-stu-id="c42f6-102">How to: Map Inheritance Hierarchies</span></span>

<span data-ttu-id="c42f6-103">Para implementar la asignación de herencia en LINQ, debe especificar los atributos y las propiedades de atributo en la clase raíz de la jerarquía de herencia como se describe en los pasos siguientes.</span><span class="sxs-lookup"><span data-stu-id="c42f6-103">To implement inheritance mapping in LINQ, you must specify the attributes and attribute properties on the root class of the inheritance hierarchy as described in the following steps.</span></span> <span data-ttu-id="c42f6-104">Los desarrolladores que usan Visual Studio pueden usar el Object Relational Designer para asignar jerarquías de herencia.</span><span class="sxs-lookup"><span data-stu-id="c42f6-104">Developers using Visual Studio can use the Object Relational Designer to map inheritance hierarchies.</span></span> <span data-ttu-id="c42f6-105">Vea [Cómo: configurar la herencia mediante Object](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="c42f6-105">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c42f6-106">No se requieren atributos o propiedades especiales en las subclases.</span><span class="sxs-lookup"><span data-stu-id="c42f6-106">No special attributes or properties are required on the subclasses.</span></span> <span data-ttu-id="c42f6-107">Observe sobre todo que las subclases no tienen el atributo <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c42f6-107">Note especially that subclasses do not have the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span>  
  
### <a name="to-map-an-inheritance-hierarchy"></a><span data-ttu-id="c42f6-108">Para asignar una jerarquía de herencia</span><span class="sxs-lookup"><span data-stu-id="c42f6-108">To map an inheritance hierarchy</span></span>  
  
1. <span data-ttu-id="c42f6-109">Agregue el atributo <xref:System.Data.Linq.Mapping.TableAttribute> a la clase raíz.</span><span class="sxs-lookup"><span data-stu-id="c42f6-109">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the root class.</span></span>  
  
2. <span data-ttu-id="c42f6-110">También en la clase raíz, agregue un atributo <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> para cada clase de la estructura jerárquica.</span><span class="sxs-lookup"><span data-stu-id="c42f6-110">Also to the root class, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute for each class in the hierarchy structure.</span></span>  
  
3. <span data-ttu-id="c42f6-111">Para cada atributo <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>, defina una propiedad <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.</span><span class="sxs-lookup"><span data-stu-id="c42f6-111">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, define a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> property.</span></span>  
  
     <span data-ttu-id="c42f6-112">Esta propiedad contiene un valor que aparece en la tabla de base de datos, en la columna <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A>, para indicar a qué clase o subclase pertenece esta fila de datos.</span><span class="sxs-lookup"><span data-stu-id="c42f6-112">This property holds a value that appears in the database table in the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> column to indicate which class or subclass this row of data belongs to.</span></span>  
  
4. <span data-ttu-id="c42f6-113">Para cada atributo <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>, agregue también una propiedad <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>.</span><span class="sxs-lookup"><span data-stu-id="c42f6-113">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, also add a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> property.</span></span>  
  
     <span data-ttu-id="c42f6-114">Esta propiedad contiene un valor que especifica a qué clase o subclases representa el valor de clave.</span><span class="sxs-lookup"><span data-stu-id="c42f6-114">This property holds a value that specifies which class or subclass the key value signifies.</span></span>  
  
5. <span data-ttu-id="c42f6-115">En uno de los atributos <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>, agregue una propiedad <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>.</span><span class="sxs-lookup"><span data-stu-id="c42f6-115">On only one of the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attributes, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> property.</span></span>  
  
     <span data-ttu-id="c42f6-116">Esta propiedad sirve para designar una asignación de *reserva* cuando el valor de discriminador de la tabla de base de datos no coincide con ningún <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> valor de las asignaciones de herencia.</span><span class="sxs-lookup"><span data-stu-id="c42f6-116">This property serves to designate a *fallback* mapping when the discriminator value from the database table does not match any <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value in the inheritance mappings.</span></span>  
  
6. <span data-ttu-id="c42f6-117">Agregue una propiedad <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> para un atributo <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c42f6-117">Add an <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> property for a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
     <span data-ttu-id="c42f6-118">Esta propiedad indica que ésta es la columna que contiene el valor <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.</span><span class="sxs-lookup"><span data-stu-id="c42f6-118">This property signifies that this is the column that holds the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c42f6-119">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c42f6-119">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c42f6-120">Si usa Visual Studio, puede usar el Object Relational Designer para configurar la herencia.</span><span class="sxs-lookup"><span data-stu-id="c42f6-120">If you are using Visual Studio, you can use the Object Relational Designer to configure inheritance.</span></span> <span data-ttu-id="c42f6-121">Consulte [Cómo: configurar la herencia mediante Object](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer) Relational Designer</span><span class="sxs-lookup"><span data-stu-id="c42f6-121">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span></span>  
  
 <span data-ttu-id="c42f6-122">En el ejemplo de código siguiente, `Vehicle` se define como la clase raíz y se han implementado los pasos anteriores para describir la jerarquía de Linq.</span><span class="sxs-lookup"><span data-stu-id="c42f6-122">In the following code example, `Vehicle` is defined as the root class, and the previous steps have been implemented to describe the hierarchy for LINQ.</span></span>  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="c42f6-123">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c42f6-123">See also</span></span>

- [<span data-ttu-id="c42f6-124">Compatibilidad de herencia</span><span class="sxs-lookup"><span data-stu-id="c42f6-124">Inheritance Support</span></span>](inheritance-support.md)
- [<span data-ttu-id="c42f6-125">Procedimiento para personalizar clases de entidades con el editor de código</span><span class="sxs-lookup"><span data-stu-id="c42f6-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)

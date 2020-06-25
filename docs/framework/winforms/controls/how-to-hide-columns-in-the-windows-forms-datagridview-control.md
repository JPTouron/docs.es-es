---
title: Ocultar columnas en el control DataGridView
description: Obtenga información sobre cómo ocultar las columnas mediante programación en el control DataGridView Windows Forms estableciendo la propiedad DataGridViewColumn. visible en false.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], hiding columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
ms.assetid: 3f94143a-2ef0-49a5-a22a-b2e6f9289642
ms.openlocfilehash: 46d7faea76098406b8e0a91d22922bf9ca391e28
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325915"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7e2ff-103">Procedimiento para ocultar columnas en el control DataGridView de formularios Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7e2ff-103">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7e2ff-104">Algunas veces querrá mostrar solo algunas de las columnas que están disponibles en un control <xref:System.Windows.Forms.DataGridView> de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7e2ff-104">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="7e2ff-105">Por ejemplo, quiere mostrar una columna con el salario de los empleados a usuarios que tengan credenciales de administración, y ocultarla a otros usuarios.</span><span class="sxs-lookup"><span data-stu-id="7e2ff-105">For example, you might want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="7e2ff-106">O quizás quiera enlazar el control a un origen de datos que contiene muchas columnas y mostrar solo algunas de ellas.</span><span class="sxs-lookup"><span data-stu-id="7e2ff-106">Alternately, you might want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="7e2ff-107">En este caso, normalmente quitaría las columnas que no quiere mostrar en lugar de ocultarlas.</span><span class="sxs-lookup"><span data-stu-id="7e2ff-107">In this case, you will typically remove the columns you are not interested in displaying rather than hide them.</span></span>  
  
 <span data-ttu-id="7e2ff-108">En el control <xref:System.Windows.Forms.DataGridView>, el valor de la propiedad <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> de una columna determina si esa columna se muestra.</span><span class="sxs-lookup"><span data-stu-id="7e2ff-108">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property value of a column determines whether that column is displayed.</span></span>  
  
 <span data-ttu-id="7e2ff-109">Visual Studio es compatible con esta tarea.</span><span class="sxs-lookup"><span data-stu-id="7e2ff-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="7e2ff-110">Consulte también [Cómo: ocultar columnas en el control DataGridView Windows Forms mediante el diseñador](hide-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="7e2ff-110">Also see [How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer](hide-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-hide-a-column-programmatically"></a><span data-ttu-id="7e2ff-111">Para ocultar una columna mediante programación</span><span class="sxs-lookup"><span data-stu-id="7e2ff-111">To hide a column programmatically</span></span>  
  
- <span data-ttu-id="7e2ff-112">Establezca la propiedad <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> en `false`.</span><span class="sxs-lookup"><span data-stu-id="7e2ff-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> property to `false`.</span></span> <span data-ttu-id="7e2ff-113">Para ocultar una columna `CustomerID` que se genera automáticamente durante el enlace de datos, coloque el siguiente código de ejemplo en un controlador de eventos <xref:System.Windows.Forms.DataGridView.DataBindingComplete>.</span><span class="sxs-lookup"><span data-stu-id="7e2ff-113">To hide a `CustomerID` column that is automatically generated during data binding, place the following code example in a <xref:System.Windows.Forms.DataGridView.DataBindingComplete> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#063](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#063)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#063](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#063)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7e2ff-114">Compilar el código</span><span class="sxs-lookup"><span data-stu-id="7e2ff-114">Compiling the Code</span></span>  
 <span data-ttu-id="7e2ff-115">Para este ejemplo se necesita:</span><span class="sxs-lookup"><span data-stu-id="7e2ff-115">This example requires:</span></span>  
  
- <span data-ttu-id="7e2ff-116">Un control <xref:System.Windows.Forms.DataGridView> llamado `dataGridView1` que contiene una columna llamada `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="7e2ff-116">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `CustomerID`.</span></span>  
  
- <span data-ttu-id="7e2ff-117">Referencias a los ensamblados <xref:System?displayProperty=nameWithType> y <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7e2ff-117">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e2ff-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="7e2ff-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7e2ff-119">Características básicas de columnas, filas y celdas en el control DataGridView de formularios Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7e2ff-119">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="7e2ff-120">Procedimiento para quitar columnas generadas automáticamente de un control DataGridView de formularios Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7e2ff-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)
- [<span data-ttu-id="7e2ff-121">Procedimiento para cambiar el orden de las columnas en el control DataGridView de formularios Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7e2ff-121">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)

---
title: Agrupar controles RadioButton para que funcionen como un conjunto
description: Obtenga información sobre cómo agrupar Windows Forms controles RadioButton para que funcionen de forma independiente de otros conjuntos.
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 9f6795330922e739cca1f2b5c11bb2ec68bb4e84
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325927"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="1f816-103">Procedimiento para agrupar controles RadioButton de formularios Windows Forms para que funcionen como un conjunto</span><span class="sxs-lookup"><span data-stu-id="1f816-103">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="1f816-104">Windows Forms <xref:System.Windows.Forms.RadioButton> controles están diseñados para proporcionar a los usuarios una opción entre dos o más configuraciones, de las cuales solo se puede asignar una a un procedimiento u objeto.</span><span class="sxs-lookup"><span data-stu-id="1f816-104">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="1f816-105">Por ejemplo, un grupo de <xref:System.Windows.Forms.RadioButton> controles puede mostrar una selección de operadores de paquetes para un pedido, pero solo se usará uno de los operadores.</span><span class="sxs-lookup"><span data-stu-id="1f816-105">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="1f816-106">Por lo tanto <xref:System.Windows.Forms.RadioButton> , solo se puede seleccionar una vez a la vez, aunque forme parte de un grupo funcional.</span><span class="sxs-lookup"><span data-stu-id="1f816-106">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="1f816-107">Para agrupar los botones de radio, puede dibujarlos dentro de un contenedor como, por ejemplo <xref:System.Windows.Forms.Panel> , un control, un <xref:System.Windows.Forms.GroupBox> control o un formulario.</span><span class="sxs-lookup"><span data-stu-id="1f816-107">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="1f816-108">Todos los botones de radio que se agregan directamente a un formulario se convierten en un grupo.</span><span class="sxs-lookup"><span data-stu-id="1f816-108">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="1f816-109">Para agregar grupos independientes, debe colocarlos dentro de paneles o cuadros de grupo.</span><span class="sxs-lookup"><span data-stu-id="1f816-109">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="1f816-110">Para obtener más información sobre los paneles o cuadros de grupo, vea información general sobre el [control panel](panel-control-overview-windows-forms.md) o [información general sobre el control GroupBox](groupbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1f816-110">For more information about panels or group boxes, see [Panel Control Overview](panel-control-overview-windows-forms.md) or [GroupBox Control Overview](groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="1f816-111">Para agrupar los controles RadioButton como un conjunto para que funcionen de forma independiente de otros conjuntos</span><span class="sxs-lookup"><span data-stu-id="1f816-111">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1. <span data-ttu-id="1f816-112">Arrastre un <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> control o desde la ficha **Windows Forms** del cuadro de **herramientas** hasta el formulario.</span><span class="sxs-lookup"><span data-stu-id="1f816-112">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2. <span data-ttu-id="1f816-113">Dibuje <xref:System.Windows.Forms.RadioButton> controles en el <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> control o.</span><span class="sxs-lookup"><span data-stu-id="1f816-113">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f816-114">Vea también</span><span class="sxs-lookup"><span data-stu-id="1f816-114">See also</span></span>

- <xref:System.Windows.Forms.RadioButton>
- [<span data-ttu-id="1f816-115">Información general sobre el control RadioButton</span><span class="sxs-lookup"><span data-stu-id="1f816-115">RadioButton Control Overview</span></span>](radiobutton-control-overview-windows-forms.md)
- [<span data-ttu-id="1f816-116">Información general sobre el control Panel</span><span class="sxs-lookup"><span data-stu-id="1f816-116">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="1f816-117">Información general sobre el control GroupBox</span><span class="sxs-lookup"><span data-stu-id="1f816-117">GroupBox Control Overview</span></span>](groupbox-control-overview-windows-forms.md)
- [<span data-ttu-id="1f816-118">Información general sobre el control CheckBox</span><span class="sxs-lookup"><span data-stu-id="1f816-118">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="1f816-119">Control RadioButton</span><span class="sxs-lookup"><span data-stu-id="1f816-119">RadioButton Control</span></span>](radiobutton-control-windows-forms.md)

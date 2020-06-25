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
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a>Procedimiento para agrupar controles RadioButton de formularios Windows Forms para que funcionen como un conjunto
Windows Forms <xref:System.Windows.Forms.RadioButton> controles están diseñados para proporcionar a los usuarios una opción entre dos o más configuraciones, de las cuales solo se puede asignar una a un procedimiento u objeto. Por ejemplo, un grupo de <xref:System.Windows.Forms.RadioButton> controles puede mostrar una selección de operadores de paquetes para un pedido, pero solo se usará uno de los operadores. Por lo tanto <xref:System.Windows.Forms.RadioButton> , solo se puede seleccionar una vez a la vez, aunque forme parte de un grupo funcional.  
  
 Para agrupar los botones de radio, puede dibujarlos dentro de un contenedor como, por ejemplo <xref:System.Windows.Forms.Panel> , un control, un <xref:System.Windows.Forms.GroupBox> control o un formulario. Todos los botones de radio que se agregan directamente a un formulario se convierten en un grupo. Para agregar grupos independientes, debe colocarlos dentro de paneles o cuadros de grupo. Para obtener más información sobre los paneles o cuadros de grupo, vea información general sobre el [control panel](panel-control-overview-windows-forms.md) o [información general sobre el control GroupBox](groupbox-control-overview-windows-forms.md).  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a>Para agrupar los controles RadioButton como un conjunto para que funcionen de forma independiente de otros conjuntos  
  
1. Arrastre un <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> control o desde la ficha **Windows Forms** del cuadro de **herramientas** hasta el formulario.  
  
2. Dibuje <xref:System.Windows.Forms.RadioButton> controles en el <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> control o.  
  
## <a name="see-also"></a>Vea también

- <xref:System.Windows.Forms.RadioButton>
- [Información general sobre el control RadioButton](radiobutton-control-overview-windows-forms.md)
- [Información general sobre el control Panel](panel-control-overview-windows-forms.md)
- [Información general sobre el control GroupBox](groupbox-control-overview-windows-forms.md)
- [Información general sobre el control CheckBox](checkbox-control-overview-windows-forms.md)
- [Control RadioButton](radiobutton-control-windows-forms.md)

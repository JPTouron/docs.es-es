---
title: Orden de eventos
description: Obtenga información detallada sobre el orden de los eventos en Windows Forms durante varias fases importantes en la duración de las aplicaciones y los controles.
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
ms.openlocfilehash: b16d544d11500b2c684e87a915fc4b8eec071faa
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904343"
---
# <a name="order-of-events-in-windows-forms"></a><span data-ttu-id="11f1f-103">Orden de eventos en los formularios Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11f1f-103">Order of Events in Windows Forms</span></span>
<span data-ttu-id="11f1f-104">El orden en que se producen los eventos en las aplicaciones de Windows Forms es de particular interés para los programadores a los que les preocupa controlar cada uno de estos eventos uno por uno.</span><span class="sxs-lookup"><span data-stu-id="11f1f-104">The order in which events are raised in Windows Forms applications is of particular interest to developers concerned with handling each of these events in turn.</span></span> <span data-ttu-id="11f1f-105">Cuando una situación requiere un control minucioso de los eventos, por ejemplo, cuando se vuelven a dibujar partes del formulario, es necesario conocer el orden exacto en que los eventos se producen en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="11f1f-105">When a situation calls for meticulous handling of events, such as when you are redrawing parts of the form, an awareness of the precise order in which events are raised at run time is necessary.</span></span> <span data-ttu-id="11f1f-106">En este tema se proporcionan algunos detalles sobre el orden de los eventos en varias fases importantes de la duración de las aplicaciones y los controles.</span><span class="sxs-lookup"><span data-stu-id="11f1f-106">This topic provides some details on the order of events during several important stages in the lifetime of applications and controls.</span></span> <span data-ttu-id="11f1f-107">Para obtener detalles específicos sobre el orden de los eventos de entrada del mouse, consulte [eventos del mouse en Windows Forms](mouse-events-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="11f1f-107">For specific details about the order of mouse input events, see [Mouse Events in Windows Forms](mouse-events-in-windows-forms.md).</span></span> <span data-ttu-id="11f1f-108">Para obtener información general sobre los eventos de Windows Forms, consulte [información general sobre eventos](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="11f1f-108">For an overview of events in Windows Forms, see [Events Overview](events-overview-windows-forms.md).</span></span> <span data-ttu-id="11f1f-109">Para obtener más información sobre la composición de los controladores de eventos, vea [información general](event-handlers-overview-windows-forms.md)sobre los controladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="11f1f-109">For details about the makeup of event handlers, see [Event Handlers Overview](event-handlers-overview-windows-forms.md).</span></span>  
  
## <a name="application-startup-and-shutdown-events"></a><span data-ttu-id="11f1f-110">Eventos de inicio y cierre de la aplicación</span><span class="sxs-lookup"><span data-stu-id="11f1f-110">Application Startup and Shutdown Events</span></span>  
 <span data-ttu-id="11f1f-111">Las clases <xref:System.Windows.Forms.Form> y <xref:System.Windows.Forms.Control> exponen un conjunto de eventos relacionados con el inicio y el cierre de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="11f1f-111">The <xref:System.Windows.Forms.Form> and <xref:System.Windows.Forms.Control> classes expose a set of events related to application startup and shutdown.</span></span> <span data-ttu-id="11f1f-112">Cuando se inicia una aplicación de Windows Forms, se generan los eventos de inicio del formulario principal en el orden siguiente:</span><span class="sxs-lookup"><span data-stu-id="11f1f-112">When a Windows Forms application starts, the startup events of the main form are raised in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 <span data-ttu-id="11f1f-113">Cuando se cierra una aplicación, se generan los eventos de cierre del formulario principal en el orden siguiente:</span><span class="sxs-lookup"><span data-stu-id="11f1f-113">When an application closes, the shutdown events of the main form are raised in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <span data-ttu-id="11f1f-114">El evento <xref:System.Windows.Forms.Application.ApplicationExit> de la clase <xref:System.Windows.Forms.Application> se genera después de los eventos de cierre del formulario principal.</span><span class="sxs-lookup"><span data-stu-id="11f1f-114">The <xref:System.Windows.Forms.Application.ApplicationExit> event of the <xref:System.Windows.Forms.Application> class is raised after the shutdown events of the main form.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11f1f-115">Visual Basic 2005 incluye eventos de aplicación adicionales, como <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> y <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="11f1f-115">Visual Basic 2005 includes additional application events, such as <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> and <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span></span>  
  
## <a name="focus-and-validation-events"></a><span data-ttu-id="11f1f-116">Eventos de foco y validación</span><span class="sxs-lookup"><span data-stu-id="11f1f-116">Focus and Validation Events</span></span>  
 <span data-ttu-id="11f1f-117">Al cambiar el foco mediante el teclado (TAB, MAYÚS+TAB, etc.) mediante una llamada a los métodos <xref:System.Windows.Forms.Control.Select%2A> o <xref:System.Windows.Forms.Control.SelectNextControl%2A>, o estableciendo la propiedad <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> en el formulario actual, los eventos de foco de la clase <xref:System.Windows.Forms.Control> se generan en el orden siguiente:</span><span class="sxs-lookup"><span data-stu-id="11f1f-117">When you change the focus by using the keyboard (TAB, SHIFT+TAB, and so on), by calling the <xref:System.Windows.Forms.Control.Select%2A> or <xref:System.Windows.Forms.Control.SelectNextControl%2A> methods, or by setting the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property to the current form, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
 <span data-ttu-id="11f1f-118">Al cambiar el foco mediante el mouse o mediante una llamada al método <xref:System.Windows.Forms.Control.Focus%2A>, los eventos de foco de la clase <xref:System.Windows.Forms.Control> se generan en el orden siguiente:</span><span class="sxs-lookup"><span data-stu-id="11f1f-118">When you change the focus by using the mouse or by calling the <xref:System.Windows.Forms.Control.Focus%2A> method, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a><span data-ttu-id="11f1f-119">Consulte también</span><span class="sxs-lookup"><span data-stu-id="11f1f-119">See also</span></span>

- [<span data-ttu-id="11f1f-120">Crear controladores de eventos en Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11f1f-120">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)

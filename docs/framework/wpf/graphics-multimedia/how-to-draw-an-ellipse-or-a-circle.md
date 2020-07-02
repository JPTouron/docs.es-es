---
title: 'Cómo: Dibujar una elipse o un círculo'
description: Obtenga información sobre cómo dibujar una elipse o un círculo con opciones para el grosor del contorno y el color interior en Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: afa0e7d2af42aaee39dca164f23b1a1cacf430ca
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853568"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="17cd3-103">Cómo: Dibujar una elipse o un círculo</span><span class="sxs-lookup"><span data-stu-id="17cd3-103">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="17cd3-104">En este ejemplo se muestra cómo dibujar elipses y círculos mediante el <xref:System.Windows.Shapes.Ellipse> elemento.</span><span class="sxs-lookup"><span data-stu-id="17cd3-104">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="17cd3-105">Para dibujar una elipse, cree un <xref:System.Windows.Shapes.Ellipse> elemento y especifique su <xref:System.Windows.FrameworkElement.Width%2A> y <xref:System.Windows.FrameworkElement.Height%2A> .</span><span class="sxs-lookup"><span data-stu-id="17cd3-105">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="17cd3-106">Utilice la <xref:System.Windows.Shapes.Shape.Fill%2A> propiedad para especificar el <xref:System.Windows.Media.Brush> que se usa para pintar el interior de la elipse.</span><span class="sxs-lookup"><span data-stu-id="17cd3-106">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="17cd3-107">Utilice la <xref:System.Windows.Shapes.Shape.Stroke%2A> propiedad para especificar el <xref:System.Windows.Media.Brush> que se usa para pintar el contorno de la elipse.</span><span class="sxs-lookup"><span data-stu-id="17cd3-107">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="17cd3-108">La <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> propiedad especifica el grosor del contorno de la elipse.</span><span class="sxs-lookup"><span data-stu-id="17cd3-108">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="17cd3-109">Para dibujar un círculo, haga que <xref:System.Windows.FrameworkElement.Width%2A> y <xref:System.Windows.FrameworkElement.Height%2A> del <xref:System.Windows.Shapes.Ellipse> elemento sean iguales entre sí.</span><span class="sxs-lookup"><span data-stu-id="17cd3-109">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="17cd3-110">En el ejemplo siguiente se dibujan cuatro <xref:System.Windows.Shapes.Ellipse> elementos dentro de <xref:System.Windows.Controls.Canvas> .</span><span class="sxs-lookup"><span data-stu-id="17cd3-110">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17cd3-111">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17cd3-111">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="17cd3-112">Aunque en este ejemplo se usa un <xref:System.Windows.Controls.Canvas> para contener los puntos suspensivos, se pueden usar elementos de elipse (y todos los demás elementos de forma) con cualquier <xref:System.Windows.Controls.Panel> o <xref:System.Windows.Controls.Control> que admita contenido que no sea de texto.</span><span class="sxs-lookup"><span data-stu-id="17cd3-112">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="17cd3-113">Este ejemplo forma parte de un ejemplo más grande; para obtener el ejemplo completo, vea [ejemplo de elementos de forma](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="17cd3-113">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17cd3-114">Vea también</span><span class="sxs-lookup"><span data-stu-id="17cd3-114">See also</span></span>

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="17cd3-115">Ejemplo de elementos de forma</span><span class="sxs-lookup"><span data-stu-id="17cd3-115">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)

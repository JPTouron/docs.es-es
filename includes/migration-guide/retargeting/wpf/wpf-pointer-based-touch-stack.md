---
ms.openlocfilehash: eb89cbc72d8b09fd1aa5bc775a6c539eb208fa70
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614897"
---
### <a name="wpf-pointer-based-touch-stack"></a><span data-ttu-id="bf501-101">Pila táctil basada en punteros de WPF</span><span class="sxs-lookup"><span data-stu-id="bf501-101">WPF Pointer-Based Touch Stack</span></span>

#### <a name="details"></a><span data-ttu-id="bf501-102">Detalles</span><span class="sxs-lookup"><span data-stu-id="bf501-102">Details</span></span>

<span data-ttu-id="bf501-103">Este cambio agrega la posibilidad de habilitar una pila táctil o de lápiz de WPF opcional basada en WM_POINTER.</span><span class="sxs-lookup"><span data-stu-id="bf501-103">This change adds the ability to enable an optional WM_POINTER based WPF touch/stylus stack.</span></span>  <span data-ttu-id="bf501-104">Los desarrolladores que no lo habiliten explícitamente no deberían ver ningún cambio en el comportamiento del lápiz o la entrada táctil de WPF. Problemas conocidos actuales con la pila táctil o de lápiz opcional basada en WM_POINTER:</span><span class="sxs-lookup"><span data-stu-id="bf501-104">Developers that do not explicitly enable this should see no change in WPF touch/stylus behavior.Current Known Issues With optional WM_POINTER based touch/stylus stack:</span></span>

- <span data-ttu-id="bf501-105">No se admiten las entradas manuscritas en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="bf501-105">No support for real-time inking.</span></span>
- <span data-ttu-id="bf501-106">Aunque los complementos de lápiz y entrada manuscrita seguirán funcionando, se procesarán en el subproceso de la interfaz de usuario, lo que puede provocar un rendimiento deficiente.</span><span class="sxs-lookup"><span data-stu-id="bf501-106">While inking and StylusPlugins will still work, they will be processed on the UI Thread which can lead to poor performance.</span></span>
- <span data-ttu-id="bf501-107">El comportamiento cambia debido a las modificaciones en la promoción de los eventos de lápiz o de entrada táctil a los eventos de mouse.</span><span class="sxs-lookup"><span data-stu-id="bf501-107">Behavioral changes due to changes in promotion from touch/stylus events to mouse events</span></span>
- <span data-ttu-id="bf501-108">Es posible que la manipulación se comporte de otra forma.</span><span class="sxs-lookup"><span data-stu-id="bf501-108">Manipulation may behave differently</span></span>
- <span data-ttu-id="bf501-109">Arrastrar y colocar no mostrará la información adecuada para la entrada táctil.</span><span class="sxs-lookup"><span data-stu-id="bf501-109">Drag/Drop will not show appropriate feedback for touch input</span></span>
- <span data-ttu-id="bf501-110">Esto no afecta a la entrada de lápiz.</span><span class="sxs-lookup"><span data-stu-id="bf501-110">This does not affect stylus input</span></span>
- <span data-ttu-id="bf501-111">Arrastrar y colocar ya no se puede iniciar en los eventos de lápiz o entrada táctil.</span><span class="sxs-lookup"><span data-stu-id="bf501-111">Drag/Drop can no longer be initiated on touch/stylus events</span></span>
- <span data-ttu-id="bf501-112">Esto puede hacer que la aplicación de detenga hasta que se detecte la entrada del mouse.</span><span class="sxs-lookup"><span data-stu-id="bf501-112">This can potentially hang the application until mouse input is detected.</span></span>
- <span data-ttu-id="bf501-113">En su lugar, los desarrolladores deben iniciar Arrastrar y colocar en los eventos del mouse.</span><span class="sxs-lookup"><span data-stu-id="bf501-113">Instead, developers should initiate drag and drop from mouse events.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bf501-114">Sugerencia</span><span class="sxs-lookup"><span data-stu-id="bf501-114">Suggestion</span></span>

<span data-ttu-id="bf501-115">Los desarrolladores que quieran habilitar esta pila pueden agregar o combinar lo siguiente en el archivo App.config de la aplicación:</span><span class="sxs-lookup"><span data-stu-id="bf501-115">Developers who wish to enable this stack can add/merge the following to their application's App.config file:</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="bf501-116">Si se elimina esto o el valor se establece en false, esta pila opcional se desactivará. Tenga en cuenta que esta pila solo está disponible en Windows 10 Creators Update y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="bf501-116">Removing this or setting the value to false will turn this optional stack off.Note that this stack is available only on Windows 10 Creators Update and above.</span></span>

| <span data-ttu-id="bf501-117">NOMBRE</span><span class="sxs-lookup"><span data-stu-id="bf501-117">Name</span></span>    | <span data-ttu-id="bf501-118">Valor</span><span class="sxs-lookup"><span data-stu-id="bf501-118">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bf501-119">Ámbito</span><span class="sxs-lookup"><span data-stu-id="bf501-119">Scope</span></span>   | <span data-ttu-id="bf501-120">Borde</span><span class="sxs-lookup"><span data-stu-id="bf501-120">Edge</span></span>        |
| <span data-ttu-id="bf501-121">Versión</span><span class="sxs-lookup"><span data-stu-id="bf501-121">Version</span></span> | <span data-ttu-id="bf501-122">4.7</span><span class="sxs-lookup"><span data-stu-id="bf501-122">4.7</span></span>         |
| <span data-ttu-id="bf501-123">Tipo</span><span class="sxs-lookup"><span data-stu-id="bf501-123">Type</span></span>    | <span data-ttu-id="bf501-124">Redestinación</span><span class="sxs-lookup"><span data-stu-id="bf501-124">Retargeting</span></span> |

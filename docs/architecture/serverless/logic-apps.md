---
title: 'Azure Logic Apps: Aplicaciones sin servidor'
description: Azure Logic Apps permite compilar flujos de trabajo escalables automatizados que integran aplicaciones y datos en los servicios en la nube y los sistemas locales.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 11fdf5b5f176eb0d66eee6dde7638d3eae1e1f55
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171850"
---
# <a name="azure-logic-apps"></a><span data-ttu-id="f595b-103">Azure Logic Apps</span><span class="sxs-lookup"><span data-stu-id="f595b-103">Azure Logic Apps</span></span>

<span data-ttu-id="f595b-104">[Azure Logic Apps](/azure/logic-apps) proporciona un motor sin servidor para compilar flujos de trabajo automatizados que integran aplicaciones y datos entre los servicios en la nube y los sistemas locales.</span><span class="sxs-lookup"><span data-stu-id="f595b-104">[Azure Logic Apps](/azure/logic-apps) provides a serverless engine to build automated workflows to integrate apps and data between cloud services and on-premises systems.</span></span> <span data-ttu-id="f595b-105">Puede crear flujos de trabajo mediante un diseñador visual.</span><span class="sxs-lookup"><span data-stu-id="f595b-105">You build workflows using a visual designer.</span></span> <span data-ttu-id="f595b-106">Puede desencadenar flujos de trabajo basados en eventos o temporizadores, y aprovechar los conectores para integrar aplicaciones y facilitar la comunicación de negocio a negocio (B2B).</span><span class="sxs-lookup"><span data-stu-id="f595b-106">You can trigger workflows based on events or timers and leverage connectors to integration applications and facilitate business-to-business (B2B) communication.</span></span> <span data-ttu-id="f595b-107">Logic Apps se integra sin problemas con Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="f595b-107">Logic Apps integrates seamlessly with Azure Functions.</span></span>

![Logotipo de Azure Logic Apps](./media/logic-apps-logo.png)

<span data-ttu-id="f595b-109">Logic Apps puede hacer más cosas que simplemente conectar los servicios en la nube (como las funciones) con recursos en la nube (como colas y bases de datos).</span><span class="sxs-lookup"><span data-stu-id="f595b-109">Logic Apps can do more than just connect your cloud services (like functions) with cloud resources (like queues and databases).</span></span> <span data-ttu-id="f595b-110">También puede orquestar los flujos de trabajo locales con la puerta de enlace local.</span><span class="sxs-lookup"><span data-stu-id="f595b-110">You can also orchestrate on-premises workflows with the on-premises gateway.</span></span> <span data-ttu-id="f595b-111">Por ejemplo, puede usar la aplicación lógica para desencadenar un procedimiento almacenado de SQL local en respuesta a un evento basado en la nube o a una lógica condicional en el flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="f595b-111">For example, you can use the Logic App to trigger an on-premises SQL stored procedure in response to a cloud-based event or conditional logic in your workflow.</span></span> <span data-ttu-id="f595b-112">Para más información, consulte [Conexión a orígenes de datos locales con la puerta de enlace de datos local de Azure](/azure/analysis-services/analysis-services-gateway).</span><span class="sxs-lookup"><span data-stu-id="f595b-112">Learn more about [Connecting to on-premises data sources with Azure On-premises Data Gateway](/azure/analysis-services/analysis-services-gateway).</span></span>

![Arquitectura de Logic Apps](./media/logic-apps-architecture.png)

<span data-ttu-id="f595b-114">Al igual que Azure Functions, puede iniciar flujos de trabajo de Logic Apps con un desencadenador.</span><span class="sxs-lookup"><span data-stu-id="f595b-114">Like Azure Functions, you kick off Logic App workflows with a trigger.</span></span> <span data-ttu-id="f595b-115">Hay muchos desencadenadores entre los que puede elegir.</span><span class="sxs-lookup"><span data-stu-id="f595b-115">There are many triggers for you to choose from.</span></span> <span data-ttu-id="f595b-116">En la captura siguiente se muestran solo algunos de los más populares de entre los cientos que están disponibles.</span><span class="sxs-lookup"><span data-stu-id="f595b-116">The following capture shows just a few of the more popular ones out of hundreds that are available.</span></span>

![Desencadenadores de Logic Apps](./media/logic-app-triggers.png)

<span data-ttu-id="f595b-118">Una vez que se desencadena la aplicación, puede usar el diseñador visual para crear pasos, bucles, condiciones y acciones.</span><span class="sxs-lookup"><span data-stu-id="f595b-118">Once the app is triggered, you can use the visual designer to build out steps, loops, conditions, and actions.</span></span> <span data-ttu-id="f595b-119">Los datos ingeridos en un paso anterior están disponibles para su uso en los pasos posteriores.</span><span class="sxs-lookup"><span data-stu-id="f595b-119">Any data ingested in a previous step is available for you to use in subsequent steps.</span></span> <span data-ttu-id="f595b-120">El siguiente flujo de trabajo carga las direcciones URL desde una base de datos de CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="f595b-120">The following workflow loads URLs from a CosmosDB database.</span></span> <span data-ttu-id="f595b-121">Busca los que tienen un host de `t.co` y luego los busca en Twitter.</span><span class="sxs-lookup"><span data-stu-id="f595b-121">It finds the ones with a host of `t.co` then searches for them on Twitter.</span></span> <span data-ttu-id="f595b-122">Si encuentra tweets correspondientes, actualiza los documentos con los tweets relacionados mediante una llamada a una función.</span><span class="sxs-lookup"><span data-stu-id="f595b-122">If it finds corresponding tweets, it updates the documents with the related tweets by calling a function.</span></span>

![Flujo de trabajo de Logic Apps](./media/logic-app-workflow.png)

<span data-ttu-id="f595b-124">En el panel de Logic Apps se muestra el historial de ejecución de los flujos de trabajo y si cada ejecución se completó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="f595b-124">The Logic Apps dashboard shows the history of running your workflows and whether each run completed successfully or not.</span></span> <span data-ttu-id="f595b-125">Puede ir a cualquier ejecución concreta e inspeccionar los datos que se usaron en cada paso para solucionar problemas.</span><span class="sxs-lookup"><span data-stu-id="f595b-125">You can navigate into any given run and inspect the data used by each step for troubleshooting.</span></span> <span data-ttu-id="f595b-126">Logic Apps también proporciona plantillas ya existentes que puede editar y que son adecuadas para flujos de trabajo empresariales complejos.</span><span class="sxs-lookup"><span data-stu-id="f595b-126">Logic Apps also provides existing templates you can edit and are well suited for complex enterprise workflows.</span></span>

<span data-ttu-id="f595b-127">Para más información, consulte [Azure Logic Apps](/azure/logic-apps).</span><span class="sxs-lookup"><span data-stu-id="f595b-127">To learn more, see [Azure Logic Apps](/azure/logic-apps).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f595b-128">[Anterior](application-insights.md)
>[Siguiente](event-grid.md)</span><span class="sxs-lookup"><span data-stu-id="f595b-128">[Previous](application-insights.md)
[Next](event-grid.md)</span></span>

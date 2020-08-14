---
title: Diseño de aplicaciones de Docker
description: Aquí encontrará una referencia a una guía detallada de la arquitectura de microservicios, porque es un tema que no se describe en esta guía.
ms.date: 08/06/2020
ms.openlocfilehash: b63d4344abb358a393587bdacf91f6091b531af0
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915973"
---
# <a name="design-docker-applications"></a><span data-ttu-id="4cc66-103">Diseño de aplicaciones de Docker</span><span class="sxs-lookup"><span data-stu-id="4cc66-103">Design Docker applications</span></span>

<span data-ttu-id="4cc66-104">En el capítulo 1 se presentaron los conceptos fundamentales relativos a los contenedores y Docker.</span><span class="sxs-lookup"><span data-stu-id="4cc66-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="4cc66-105">Se trata del nivel básico de información que necesita para empezar.</span><span class="sxs-lookup"><span data-stu-id="4cc66-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="4cc66-106">Con todo, las aplicaciones empresariales pueden ser complejas y componerse de varios servicios en lugar de un solo servicio o contenedor.</span><span class="sxs-lookup"><span data-stu-id="4cc66-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="4cc66-107">Para esos casos de uso opcionales, tiene que conocer otros enfoques de diseño, como la arquitectura orientada a servicios (SOA) y los conceptos más avanzados de microservicios y de orquestación de contenedores.</span><span class="sxs-lookup"><span data-stu-id="4cc66-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="4cc66-108">El ámbito de este documento no se limita a los microservicios sino que comprende todo el ciclo de vida de aplicaciones de Docker y, por lo tanto, no explora a fondo la arquitectura de microservicios, ya que también se pueden utilizar contenedores y Docker con SOA normales, trabajos o tareas en segundo plano o incluso con enfoques de implementación de aplicaciones monolíticas.</span><span class="sxs-lookup"><span data-stu-id="4cc66-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you can also use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="4cc66-109">**Más información** Para obtener más información sobre las aplicaciones empresariales y la arquitectura de microservicios, lea la guía [Microservicios de NET: Arquitectura para aplicaciones .NET en contenedor](../../microservices/index.md), que también puede descargar en <https://aka.ms/MicroservicesEbook>.</span><span class="sxs-lookup"><span data-stu-id="4cc66-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="4cc66-110">Pero antes de pasar al ciclo de vida de la aplicación y DevOps, es importante saber cómo se va a diseñar y construir la aplicación y cuáles son las opciones de diseño.</span><span class="sxs-lookup"><span data-stu-id="4cc66-110">However, before you get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4cc66-111">[Anterior](index.md)
>[Siguiente](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="4cc66-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>

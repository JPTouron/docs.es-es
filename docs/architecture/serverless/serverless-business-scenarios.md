---
title: Ejemplos de escenarios empresariales y casos de uso de aplicaciones sin servidor
description: Conozca el modo sin servidor con un enfoque práctico mediante ejemplos que van desde el procesamiento de imágenes hasta la compatibilidad con aplicaciones móviles y las canalizaciones de extracción, transformación y carga de datos (ETL).
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/17/2020
ms.openlocfilehash: df76b132579eb3a6d05ce38c94cb9fceb9281aef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171616"
---
# <a name="serverless-business-scenarios-and-use-cases"></a><span data-ttu-id="8a7ae-103">Escenarios y casos de uso empresariales sin servidor</span><span class="sxs-lookup"><span data-stu-id="8a7ae-103">Serverless business scenarios and use cases</span></span>

<span data-ttu-id="8a7ae-104">Hay muchos casos de uso y escenarios para aplicaciones sin servidor.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-104">There are many use cases and scenarios for serverless applications.</span></span> <span data-ttu-id="8a7ae-105">En este capítulo se incluyen ejemplos que muestran los distintos escenarios.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-105">This chapter includes samples that illustrate the different scenarios.</span></span> <span data-ttu-id="8a7ae-106">Los escenarios incluyen vínculos a documentación relacionada y repositorios de código fuente públicos.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-106">The scenarios include links to related documentation and public source code repositories.</span></span> <span data-ttu-id="8a7ae-107">Los ejemplos de este capítulo le permiten empezar a trabajar en su propia creación e implementación de soluciones sin servidor.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-107">The samples in this chapter enable you to get started on your own building and implementing serverless solutions.</span></span>

## <a name="big-data-processing"></a><span data-ttu-id="8a7ae-108">Procesamiento de macrodatos</span><span class="sxs-lookup"><span data-stu-id="8a7ae-108">Big data processing</span></span>

![Diagrama de asignación/reducción](/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/media/mapreducearchitecture.png)

<span data-ttu-id="8a7ae-110">En este ejemplo se usa un enfoque sin servidor para realizar una operación de asignación/reducción en un gran conjunto de datos.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-110">This example uses serverless to do a map/reduce operation on a big data set.</span></span> <span data-ttu-id="8a7ae-111">Determina la velocidad media de los viajes realizados por los taxis amarillos de Nueva York por día en 2017.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-111">It determines the average speed of New York Yellow taxi trips per day in 2017.</span></span>

[<span data-ttu-id="8a7ae-112">Procesamiento de macrodatos: MapReduce sin servidor en Azure</span><span class="sxs-lookup"><span data-stu-id="8a7ae-112">Big Data Processing: Serverless MapReduce on Azure</span></span>](/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)

## <a name="create-serverless-applications-hands-on-lab"></a><span data-ttu-id="8a7ae-113">Creación de aplicaciones sin servidor: laboratorio práctico</span><span class="sxs-lookup"><span data-stu-id="8a7ae-113">Create serverless applications: hands-on lab</span></span>

<span data-ttu-id="8a7ae-114">Aprenda a usar Functions para ejecutar la lógica del servidor y crear arquitecturas sin servidor.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-114">Learn how to use functions to execute server-side logic and build serverless architectures.</span></span>

- <span data-ttu-id="8a7ae-115">Elección del mejor servicio de Azure para su empresa</span><span class="sxs-lookup"><span data-stu-id="8a7ae-115">Choosing the best Azure service for your business</span></span>
- <span data-ttu-id="8a7ae-116">Creación de Azure Functions</span><span class="sxs-lookup"><span data-stu-id="8a7ae-116">Creating Azure Functions</span></span>
- <span data-ttu-id="8a7ae-117">Uso de desencadenadores</span><span class="sxs-lookup"><span data-stu-id="8a7ae-117">Using triggers</span></span>
- <span data-ttu-id="8a7ae-118">Encadenamiento de funciones</span><span class="sxs-lookup"><span data-stu-id="8a7ae-118">Chaining functions</span></span>
- <span data-ttu-id="8a7ae-119">Flujos de trabajo de larga ejecución</span><span class="sxs-lookup"><span data-stu-id="8a7ae-119">Long-running workflows</span></span>
- <span data-ttu-id="8a7ae-120">Supervisión</span><span class="sxs-lookup"><span data-stu-id="8a7ae-120">Monitoring</span></span>
- <span data-ttu-id="8a7ae-121">Desarrollo, pruebas e implementación</span><span class="sxs-lookup"><span data-stu-id="8a7ae-121">Development, testing, and deployment</span></span>

[<span data-ttu-id="8a7ae-122">Creación de aplicaciones sin servidor</span><span class="sxs-lookup"><span data-stu-id="8a7ae-122">Create serverless applications</span></span>](/learn/paths/create-serverless-applications/)

## <a name="customer-reviews"></a><span data-ttu-id="8a7ae-123">Revisiones de clientes</span><span class="sxs-lookup"><span data-stu-id="8a7ae-123">Customer reviews</span></span>

<span data-ttu-id="8a7ae-124">En este ejemplo se muestran las nuevas herramientas de Azure Functions para las bibliotecas de clases C# de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-124">This sample showcases the new Azure Functions tooling for C# Class Libraries in Visual Studio.</span></span> <span data-ttu-id="8a7ae-125">Cree un sitio web en el que los clientes envíen revisiones de productos que se almacenan en instancias de Azure Storage Blob y CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-125">Create a website where customers submit product reviews that are stored in Azure storage blobs and CosmosDB.</span></span> <span data-ttu-id="8a7ae-126">Agregue una instancia de Azure Functions para realizar una moderación automatizada de las revisiones de clientes mediante Azure Cognitive Services.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-126">Add an Azure Function to perform automated moderation of the customer reviews using Azure Cognitive Services.</span></span> <span data-ttu-id="8a7ae-127">Use una cola de Azure Storage para desacoplar el sitio web de la función.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-127">Use an Azure storage queue to decouple the website from the function.</span></span>

[<span data-ttu-id="8a7ae-128">Aplicación de revisiones de clientes con Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="8a7ae-128">Customer Reviews App with Cognitive Services</span></span>](/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)

## <a name="docker-linux-image-support"></a><span data-ttu-id="8a7ae-129">Compatibilidad con imágenes Docker de Linux</span><span class="sxs-lookup"><span data-stu-id="8a7ae-129">Docker Linux image support</span></span>

<span data-ttu-id="8a7ae-130">En este ejemplo se muestra cómo crear un `Dockerfile` para compilar y ejecutar Azure Functions en un contenedor Docker de Linux.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-130">This sample demonstrates how to create a `Dockerfile` to build and run Azure Functions on a Linux Docker container.</span></span>

[<span data-ttu-id="8a7ae-131">Azure Functions en Linux</span><span class="sxs-lookup"><span data-stu-id="8a7ae-131">Azure Functions on Linux</span></span>](/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)

## <a name="file-processing-and-validation"></a><span data-ttu-id="8a7ae-132">Procesamiento y validación de archivos</span><span class="sxs-lookup"><span data-stu-id="8a7ae-132">File processing and validation</span></span>

<span data-ttu-id="8a7ae-133">En este ejemplo se analiza un conjunto de archivos CSV de clientes hipotéticos.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-133">This example parses a set of CSV files from hypothetical customers.</span></span> <span data-ttu-id="8a7ae-134">Esto garantiza que todos los archivos necesarios para un "lote" de un cliente estén listos y valida la estructura de cada archivo.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-134">It ensures that all files required for a customer "batch" are ready, then validates the structure of each file.</span></span> <span data-ttu-id="8a7ae-135">Se presentan diferentes soluciones mediante Azure Functions, Logic Apps y Durable Functions.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-135">Different solutions are presented using Azure Functions, Logic Apps, and Durable Functions.</span></span>

[<span data-ttu-id="8a7ae-136">Procesamiento y validación de archivos mediante Azure Functions, Logic Apps y Durable Functions</span><span class="sxs-lookup"><span data-stu-id="8a7ae-136">File processing and validation using Azure Functions, Logic Apps, and Durable Functions</span></span>](/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)

## <a name="game-data-visualization"></a><span data-ttu-id="8a7ae-137">Visualización de datos de juegos</span><span class="sxs-lookup"><span data-stu-id="8a7ae-137">Game data visualization</span></span>

![Telemetría de juegos](/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/media/points.png)

<span data-ttu-id="8a7ae-139">Este es un ejemplo de cómo un desarrollador puede implementar una solución de visualización de datos en el editor para su juego.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-139">An example of how a developer could implement an in-editor data visualization solution for their game.</span></span> <span data-ttu-id="8a7ae-140">De hecho, un complemento de Unity y un complemento de Unreal Engine 4 se desarrollaron teniendo este ejemplo como back-end.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-140">In fact, an Unreal Engine 4 Plugin and Unity Plugin were developed using this sample as its backend.</span></span> <span data-ttu-id="8a7ae-141">El componente de servicio es independiente del motor de juegos.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-141">The service component is game engine agnostic.</span></span>

[<span data-ttu-id="8a7ae-142">Visualización de telemetría de juegos en el editor</span><span class="sxs-lookup"><span data-stu-id="8a7ae-142">In-editor game telemetry visualization</span></span>](/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)

## <a name="graphql"></a><span data-ttu-id="8a7ae-143">GraphQL</span><span class="sxs-lookup"><span data-stu-id="8a7ae-143">GraphQL</span></span>

<span data-ttu-id="8a7ae-144">Cree una función sin servidor que expone una API de GraphQL.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-144">Create a serverless function that exposes a GraphQL API.</span></span>

[<span data-ttu-id="8a7ae-145">Funciones sin servidor para GraphQL</span><span class="sxs-lookup"><span data-stu-id="8a7ae-145">Serverless functions for GraphQL</span></span>](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)

## <a name="internet-of-things-iot-reliable-edge-relay"></a><span data-ttu-id="8a7ae-146">Retransmisión perimetral confiable de Internet de las cosas (IoT)</span><span class="sxs-lookup"><span data-stu-id="8a7ae-146">Internet of Things (IoT) reliable edge relay</span></span>

![Arquitectura de IoT](/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/media/architecture.png)

<span data-ttu-id="8a7ae-148">En este ejemplo se implementa un nuevo protocolo de comunicación para habilitar la comunicación ascendente confiable desde dispositivos IoT.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-148">This sample implements a new communication protocol to enable reliable upstream communication from IoT devices.</span></span> <span data-ttu-id="8a7ae-149">Automatiza la detección y reposición de lagunas de datos.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-149">It automates data gap detection and backfill.</span></span>

[<span data-ttu-id="8a7ae-150">Retransmisión perimetral confiable de IoT</span><span class="sxs-lookup"><span data-stu-id="8a7ae-150">IoT Reliable Edge Relay</span></span>](/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)

## <a name="microservices-reference-architecture"></a><span data-ttu-id="8a7ae-151">Arquitectura de referencia de microservicios</span><span class="sxs-lookup"><span data-stu-id="8a7ae-151">Microservices reference architecture</span></span>

![Arquitectura de referencia](/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/media/macro-architecture.png)

<span data-ttu-id="8a7ae-153">Esta es una arquitectura de referencia que le guía por el proceso de toma de decisiones implicado en el diseño, el desarrollo y la entrega de la aplicación Rideshare de Relecloud, una empresa ficticia.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-153">A reference architecture that walks you through the decision-making process involved in designing, developing, and delivering the Rideshare by Relecloud application (a fictitious company).</span></span> <span data-ttu-id="8a7ae-154">Incluye instrucciones prácticas para configurar e implementar todos los componentes de la arquitectura.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-154">It includes hands-on instructions for configuring and deploying all of the architecture's components.</span></span>

[<span data-ttu-id="8a7ae-155">Arquitectura de referencia de microservicios sin servidor</span><span class="sxs-lookup"><span data-stu-id="8a7ae-155">Serverless Microservices reference architecture</span></span>](/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

## <a name="migrate-console-apps-to-serverless"></a><span data-ttu-id="8a7ae-156">Migración de aplicaciones de consola a aplicaciones sin servidor</span><span class="sxs-lookup"><span data-stu-id="8a7ae-156">Migrate console apps to serverless</span></span>

<span data-ttu-id="8a7ae-157">Este ejemplo es una función genérica (archivo `.csx`) que se puede usar para convertir cualquier aplicación de consola en un servicio web HTTP en Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-157">This sample is a generic function (`.csx` file) that can be used to convert any console application to an HTTP web service in Azure Functions.</span></span> <span data-ttu-id="8a7ae-158">Lo único que tiene que hacer es editar un archivo de configuración y especificar qué parámetros de entrada se pasarán como argumentos a `.exe`.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-158">All you have to do is edit a configuration file and specify what input parameters will be passed as arguments to the `.exe`.</span></span>

[<span data-ttu-id="8a7ae-159">Ejecución de aplicaciones de consola en Azure Functions</span><span class="sxs-lookup"><span data-stu-id="8a7ae-159">Run Console Apps on Azure Functions</span></span>](/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)

## <a name="serverless-for-mobile"></a><span data-ttu-id="8a7ae-160">Aplicaciones sin servidor para dispositivos móviles</span><span class="sxs-lookup"><span data-stu-id="8a7ae-160">Serverless for mobile</span></span>

<span data-ttu-id="8a7ae-161">Azure Functions es fácil de implementar y mantener, y es accesible a través de HTTP.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-161">Azure Functions are easy to implement and maintain, and accessible through HTTP.</span></span> <span data-ttu-id="8a7ae-162">Es una excelente manera de implementar una API para una aplicación móvil.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-162">They are a great way to implement an API for a mobile application.</span></span> <span data-ttu-id="8a7ae-163">Microsoft ofrece excelentes herramientas multiplataforma para iOS, Android y Windows con Xamarin.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-163">Microsoft offers great cross-platform tools for iOS, Android, and Windows with Xamarin.</span></span> <span data-ttu-id="8a7ae-164">Por ello, Xamarin y Azure Functions funcionan muy bien conjuntamente.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-164">As such, Xamarin and Azure Functions are working great together.</span></span> <span data-ttu-id="8a7ae-165">En este artículo se muestra cómo implementar primero una instancia de Azure Functions en Azure Portal o en Visual Studio, y cómo compilar un cliente multiplataforma con Xamarin.Forms que se ejecute en Android, iOS y Windows.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-165">This article shows how to implement an Azure Function in the Azure portal or in Visual Studio at first, and build a cross-platform client with Xamarin.Forms running on Android, iOS, and Windows.</span></span>

<span data-ttu-id="8a7ae-166">[Implementing a simple Azure Function with a Xamarin.Forms client](/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/) (Implementación de una instancia de Azure Function con un cliente de Xamarin.Forms)</span><span class="sxs-lookup"><span data-stu-id="8a7ae-166">[Implementing a simple Azure Function with a Xamarin.Forms client](/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)</span></span>

## <a name="serverless-messaging"></a><span data-ttu-id="8a7ae-167">Mensajería sin servidor</span><span class="sxs-lookup"><span data-stu-id="8a7ae-167">Serverless messaging</span></span>

<span data-ttu-id="8a7ae-168">En este ejemplo se muestra cómo se usa el patrón ramificado de Durable Functions para cargar un número arbitrario de mensajes en cualquier número de sesiones o particiones.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-168">This sample shows how to utilize Durable Functions' fan-out pattern to load an arbitrary number of messages across any number of sessions/partitions.</span></span> <span data-ttu-id="8a7ae-169">Se destina a Service Bus, Event Hubs o colas de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-169">It targets Service Bus, Event Hubs, or Storage Queues.</span></span> <span data-ttu-id="8a7ae-170">El ejemplo también agrega la capacidad de usar esos mensajes con otra instancia de Azure Functions y cargar los datos de tiempo resultantes en otra instancia de Event Hubs.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-170">The sample also adds the ability to consume those messages with another Azure Function and load the resulting timing data in to another Event Hub.</span></span> <span data-ttu-id="8a7ae-171">Posteriormente, los datos se ingieren en servicios de análisis como Azure Data Explorer.</span><span class="sxs-lookup"><span data-stu-id="8a7ae-171">The data is then ingested into analytics services like Azure Data Explorer.</span></span>

[<span data-ttu-id="8a7ae-172">Generación y consumo de mensajes a través de Service Bus, Event Hubs y colas de almacenamiento con Azure Functions</span><span class="sxs-lookup"><span data-stu-id="8a7ae-172">Produce and Consume messages through Service Bus, Event Hubs, and Storage Queues with Azure Functions</span></span>](/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)

## <a name="recommended-resources"></a><span data-ttu-id="8a7ae-173">Recursos recomendados</span><span class="sxs-lookup"><span data-stu-id="8a7ae-173">Recommended resources</span></span>

- [<span data-ttu-id="8a7ae-174">Azure Functions en Linux</span><span class="sxs-lookup"><span data-stu-id="8a7ae-174">Azure Functions on Linux</span></span>](/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)
- [<span data-ttu-id="8a7ae-175">Procesamiento de macrodatos: MapReduce sin servidor en Azure</span><span class="sxs-lookup"><span data-stu-id="8a7ae-175">Big Data Processing: Serverless MapReduce on Azure</span></span>](/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)
- [<span data-ttu-id="8a7ae-176">Creación de aplicaciones sin servidor</span><span class="sxs-lookup"><span data-stu-id="8a7ae-176">Create serverless applications</span></span>](/learn/paths/create-serverless-applications/)
- [<span data-ttu-id="8a7ae-177">Aplicación de revisiones de clientes con Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="8a7ae-177">Customer Reviews App with Cognitive Services</span></span>](/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)
- [<span data-ttu-id="8a7ae-178">Procesamiento y validación de archivos mediante Azure Functions, Logic Apps y Durable Functions</span><span class="sxs-lookup"><span data-stu-id="8a7ae-178">File processing and validation using Azure Functions, Logic Apps, and Durable Functions</span></span>](/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)
- <span data-ttu-id="8a7ae-179">[Implementing a simple Azure Function with a Xamarin.Forms client](/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/) (Implementación de una instancia de Azure Function con un cliente de Xamarin.Forms)</span><span class="sxs-lookup"><span data-stu-id="8a7ae-179">[Implementing a simple Azure Function with a Xamarin.Forms client](/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)</span></span>
- [<span data-ttu-id="8a7ae-180">Visualización de telemetría de juegos en el editor</span><span class="sxs-lookup"><span data-stu-id="8a7ae-180">In-editor game telemetry visualization</span></span>](/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)
- [<span data-ttu-id="8a7ae-181">Retransmisión perimetral confiable de IoT</span><span class="sxs-lookup"><span data-stu-id="8a7ae-181">IoT Reliable Edge Relay</span></span>](/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)
- [<span data-ttu-id="8a7ae-182">Generación y consumo de mensajes a través de Service Bus, Event Hubs y colas de almacenamiento con Azure Functions</span><span class="sxs-lookup"><span data-stu-id="8a7ae-182">Produce and Consume messages through Service Bus, Event Hubs, and Storage Queues with Azure Functions</span></span>](/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)
- [<span data-ttu-id="8a7ae-183">Ejecución de aplicaciones de consola en Azure Functions</span><span class="sxs-lookup"><span data-stu-id="8a7ae-183">Run Console Apps on Azure Functions</span></span>](/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)
- [<span data-ttu-id="8a7ae-184">Funciones sin servidor para GraphQL</span><span class="sxs-lookup"><span data-stu-id="8a7ae-184">Serverless functions for GraphQL</span></span>](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)
- [<span data-ttu-id="8a7ae-185">Arquitectura de referencia de microservicios sin servidor</span><span class="sxs-lookup"><span data-stu-id="8a7ae-185">Serverless Microservices reference architecture</span></span>](/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

>[!div class="step-by-step"]
><span data-ttu-id="8a7ae-186">[Anterior](orchestration-patterns.md)
>[Siguiente](serverless-conclusion.md)</span><span class="sxs-lookup"><span data-stu-id="8a7ae-186">[Previous](orchestration-patterns.md)
[Next](serverless-conclusion.md)</span></span>

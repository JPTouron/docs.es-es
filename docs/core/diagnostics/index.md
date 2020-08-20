---
title: 'Información general de las herramientas de diagnóstico: .NET Core'
description: Información general de las herramientas y técnicas disponibles para diagnosticar las aplicaciones de .NET Core.
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: ae3b9a1961f331c9cdea786bd5fe06b7bfa10927
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558119"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="e0c12-103">¿Qué herramientas de diagnóstico están disponibles en .NET Core?</span><span class="sxs-lookup"><span data-stu-id="e0c12-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="e0c12-104">El comportamiento del software no siempre es el esperado, pero .NET Core tiene herramientas y API que lo ayudarán a diagnosticar estos problemas de manera rápida y eficaz.</span><span class="sxs-lookup"><span data-stu-id="e0c12-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="e0c12-105">Este artículo lo ayuda a encontrar las distintas herramientas que necesita.</span><span class="sxs-lookup"><span data-stu-id="e0c12-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="e0c12-106">Depuradores administrados</span><span class="sxs-lookup"><span data-stu-id="e0c12-106">Managed debuggers</span></span>

<span data-ttu-id="e0c12-107">Los [depuradores administrados](managed-debuggers.md) le permiten interactuar con el programa.</span><span class="sxs-lookup"><span data-stu-id="e0c12-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="e0c12-108">Pausar, ejecutar de manera incremental, examinar y reanudar le proporcionan información sobre el comportamiento del código.</span><span class="sxs-lookup"><span data-stu-id="e0c12-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="e0c12-109">Un depurador es la primera opción para diagnosticar problemas funcionales que se pueden reproducir de manera fácil.</span><span class="sxs-lookup"><span data-stu-id="e0c12-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="e0c12-110">Registro y seguimiento</span><span class="sxs-lookup"><span data-stu-id="e0c12-110">Logging and tracing</span></span>

<span data-ttu-id="e0c12-111">El [registro y seguimiento](logging-tracing.md) son técnicas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="e0c12-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="e0c12-112">Hacen referencia a la instrumentación del código para crear archivos de registro.</span><span class="sxs-lookup"><span data-stu-id="e0c12-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="e0c12-113">Los archivos registran los detalles de lo que hace un programa.</span><span class="sxs-lookup"><span data-stu-id="e0c12-113">The files record the details of what a program does.</span></span> <span data-ttu-id="e0c12-114">Estos detalles se pueden usar para diagnosticar los problemas más complejos.</span><span class="sxs-lookup"><span data-stu-id="e0c12-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="e0c12-115">Cuando se combinan con marcas de tiempo, estas técnicas también son valiosas para investigaciones de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="e0c12-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="e0c12-116">Pruebas unitarias</span><span class="sxs-lookup"><span data-stu-id="e0c12-116">Unit testing</span></span>

<span data-ttu-id="e0c12-117">Las [pruebas unitarias](../testing/index.md) son un componente clave de la integración continua y la implementación de software de alta calidad.</span><span class="sxs-lookup"><span data-stu-id="e0c12-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="e0c12-118">Las pruebas unitarias están diseñadas para brindarle una advertencia temprana cuando se daña algo.</span><span class="sxs-lookup"><span data-stu-id="e0c12-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="net-core-dotnet-diagnostic-global-tools"></a><span data-ttu-id="e0c12-119">Herramientas globales de diagnóstico de dotnet de .NET Core</span><span class="sxs-lookup"><span data-stu-id="e0c12-119">.NET Core dotnet diagnostic Global Tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="e0c12-120">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="e0c12-120">dotnet-counters</span></span>

<span data-ttu-id="e0c12-121">[dotnet-counters](dotnet-counters.md) es una herramienta diseñada para la investigación del rendimiento y la supervisión del estado de primer nivel.</span><span class="sxs-lookup"><span data-stu-id="e0c12-121">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="e0c12-122">Permite observar los valores del contador de rendimiento que se publican a través de la API <xref:System.Diagnostics.Tracing.EventCounter>.</span><span class="sxs-lookup"><span data-stu-id="e0c12-122">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="e0c12-123">Por ejemplo, puede supervisar rápidamente elementos como el uso de la CPU o la tasa de excepciones que se generan en su aplicación .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0c12-123">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="e0c12-124">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="e0c12-124">dotnet-dump</span></span>

<span data-ttu-id="e0c12-125">La herramienta [dotnet-dump](dotnet-dump.md) permite recopilar y analizar los volcados de Windows y Linux sin necesidad de un depurador nativo.</span><span class="sxs-lookup"><span data-stu-id="e0c12-125">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-gcdump"></a><span data-ttu-id="e0c12-126">dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="e0c12-126">dotnet-gcdump</span></span>

<span data-ttu-id="e0c12-127">La herramienta [dotnet-gcdump](dotnet-gcdump.md) permite recopilar volcados de memoria de GC (recolector de elementos no utilizados) de procesos de .NET dinámicos.</span><span class="sxs-lookup"><span data-stu-id="e0c12-127">The [dotnet-gcdump](dotnet-gcdump.md) tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="e0c12-128">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="e0c12-128">dotnet-trace</span></span>

<span data-ttu-id="e0c12-129">.NET Core incluye lo que se denomina `EventPipe`, a través del cual se exponen los datos de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="e0c12-129">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="e0c12-130">La herramienta [dotnet-trace](dotnet-trace.md) permite consumir datos interesantes sobre la generación de perfiles a partir de su aplicación, lo cual puede resultar útil para analizar la causa principal de que una aplicación se ejecute con lentitud.</span><span class="sxs-lookup"><span data-stu-id="e0c12-130">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="e0c12-131">Tutoriales de diagnóstico de .NET Core</span><span class="sxs-lookup"><span data-stu-id="e0c12-131">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="e0c12-132">Depuración de una fuga de memoria</span><span class="sxs-lookup"><span data-stu-id="e0c12-132">Debug a memory leak</span></span>

<span data-ttu-id="e0c12-133">[Tutorial: Depuración de una fuga de memoria](debug-memory-leak.md) le guía a través de la búsqueda de una fuga de memoria.</span><span class="sxs-lookup"><span data-stu-id="e0c12-133">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="e0c12-134">La herramienta [dotnet-counters](dotnet-counters.md) se usa para confirmar la fuga, y la herramienta [dotnet-dump](dotnet-dump.md), para diagnosticarla.</span><span class="sxs-lookup"><span data-stu-id="e0c12-134">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>

### <a name="debug-high-cpu-usage"></a><span data-ttu-id="e0c12-135">Depuración del uso elevado de CPU</span><span class="sxs-lookup"><span data-stu-id="e0c12-135">Debug high CPU usage</span></span>

<span data-ttu-id="e0c12-136">[Tutorial: Depuración del uso elevado de CPU](debug-highcpu.md) le guía a través de la investigación del uso elevado de CPU.</span><span class="sxs-lookup"><span data-stu-id="e0c12-136">[Tutorial: Debug high CPU usage](debug-highcpu.md) walks you through investigating high CPU usage.</span></span> <span data-ttu-id="e0c12-137">Utiliza la herramienta [dotnet-counters](dotnet-counters.md) para confirmar ese uso elevado.</span><span class="sxs-lookup"><span data-stu-id="e0c12-137">It uses the [dotnet-counters](dotnet-counters.md) tool to confirm the high CPU usage.</span></span> <span data-ttu-id="e0c12-138">A continuación, se explica el uso del [seguimiento de la utilidad de análisis del rendimiento (`dotnet-trace`)](dotnet-trace.md) o de Linux `perf` para recopilar y ver el perfil de uso de la CPU.</span><span class="sxs-lookup"><span data-stu-id="e0c12-138">It then walks you through using [Trace for performance analysis utility (`dotnet-trace`)](dotnet-trace.md) or Linux `perf` to collect and view CPU usage profile.</span></span>

### <a name="debug-deadlock"></a><span data-ttu-id="e0c12-139">Depuración de interbloqueo</span><span class="sxs-lookup"><span data-stu-id="e0c12-139">Debug deadlock</span></span>

<span data-ttu-id="e0c12-140">[Tutorial: Depuración de interbloqueo](debug-deadlock.md) muestra cómo usar la herramienta [dotnet-dump](dotnet-dump.md) para investigar los subprocesos y bloqueos.</span><span class="sxs-lookup"><span data-stu-id="e0c12-140">[Tutorial: Debug deadlock](debug-deadlock.md) shows you how to use the [dotnet-dump](dotnet-dump.md) tool to investigate threads and locks.</span></span>

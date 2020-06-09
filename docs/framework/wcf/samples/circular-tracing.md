---
title: Seguimiento circular
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: 1759db28cb024afc04d02c4b128f96d73aefdd87
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585446"
---
# <a name="circular-tracing"></a><span data-ttu-id="e860c-102">Seguimiento circular</span><span class="sxs-lookup"><span data-stu-id="e860c-102">Circular Tracing</span></span>

<span data-ttu-id="e860c-103">Este ejemplo muestra la implementación de un agente de escucha de seguimiento del búfer circular.</span><span class="sxs-lookup"><span data-stu-id="e860c-103">This sample demonstrates the implementation of a circular buffer trace listener.</span></span> <span data-ttu-id="e860c-104">Un escenario común para los servicios de producción es tener servicios que están disponibles para largos periodos de tiempo y para tener habilitado el registro de seguimiento en un nivel bajo.</span><span class="sxs-lookup"><span data-stu-id="e860c-104">A common scenario for production services is to have services that are available for long periods of time and to have trace logging enabled at a low level.</span></span> <span data-ttu-id="e860c-105">Estos servicios utilizan mucho espacio en disco.</span><span class="sxs-lookup"><span data-stu-id="e860c-105">These services consume a lot of disk space.</span></span> <span data-ttu-id="e860c-106">Al solucionar problemas de un servicio, serán relevantes los datos más recientes que haya en el registro de seguimiento para resolver un problema.</span><span class="sxs-lookup"><span data-stu-id="e860c-106">When troubleshooting a service, the most recent data in the trace log is relevant to solving a problem.</span></span> <span data-ttu-id="e860c-107">Este ejemplo muestra una implementación de un agente de escucha de seguimiento del búfer circular en el que solo los seguimientos más recientes se guardan en el disco hasta llegar a una cantidad de datos configurable.</span><span class="sxs-lookup"><span data-stu-id="e860c-107">This sample demonstrates an implementation of a circular buffer trace listener in which only the most recent traces are kept on disk up to a configurable amount of data.</span></span> <span data-ttu-id="e860c-108">Este ejemplo se basa en el [Introducción](getting-started-sample.md) e incluye un agente de escucha de seguimiento personalizado.</span><span class="sxs-lookup"><span data-stu-id="e860c-108">This sample is based on the [Getting Started](getting-started-sample.md) and includes a custom tracing listener.</span></span>

> [!NOTE]
> <span data-ttu-id="e860c-109">El procedimiento de instalación y las instrucciones de compilación de este ejemplo se encuentran al final de este tema.</span><span class="sxs-lookup"><span data-stu-id="e860c-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="e860c-110">En este ejemplo se da por supuesto que está familiarizado con el ejemplo de [registro de mensajes](tracing-and-message-logging.md) y de seguimiento y que ha leído la documentación proporcionada para el ejemplo de [registro de mensajes y seguimiento](tracing-and-message-logging.md) .</span><span class="sxs-lookup"><span data-stu-id="e860c-110">This sample assumes that you are familiar with the [Tracing and Message Logging](tracing-and-message-logging.md) sample and have read the documentation provided for the [Tracing and Message Logging](tracing-and-message-logging.md) sample.</span></span>

## <a name="circular-buffer-trace-listener"></a><span data-ttu-id="e860c-111">Agente de escucha de seguimiento de búfer circular</span><span class="sxs-lookup"><span data-stu-id="e860c-111">Circular Buffer Trace Listener</span></span>

<span data-ttu-id="e860c-112">El concepto que se encuentra detrás de la implementación del Agente de escucha de seguimiento del búfer circular es tener dos archivos que pueden almacenar hasta la mitad de los datos de registro de seguimiento deseados.</span><span class="sxs-lookup"><span data-stu-id="e860c-112">The concept behind the implementation of the Circular Buffer Trace Listener is to have two files that can each store up to half of the total desired trace log data.</span></span> <span data-ttu-id="e860c-113">El agente de escucha crea un archivo y escribe en ese archivo hasta que llega al límite de la mitad del tamaño de datos, momento en el cual cambia a un segundo archivo.</span><span class="sxs-lookup"><span data-stu-id="e860c-113">The listener creates one file and writes to that file until it reaches the limit of half of the data size, at which point it switches to a second file.</span></span> <span data-ttu-id="e860c-114">Cuando el agente de escucha alcanza el límite para el segundo archivo, sobrescribe el primer archivo con nuevos seguimientos.</span><span class="sxs-lookup"><span data-stu-id="e860c-114">When the listener reaches the limit for the second file - it overwrites the first file with new traces.</span></span>

<span data-ttu-id="e860c-115">Este agente de escucha se deriva de `XmlWriteTraceListener` y permite ver los registros con la herramienta de [visor de seguimiento de servicio (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e860c-115">This listener derives from the `XmlWriteTraceListener` and allows the logs to be viewed with the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="e860c-116">Al intentar ver los registros, los dos archivos de registro se pueden recombinar con facilidad abriendo al mismo tiempo ambos archivos de registro en la herramienta Visor de seguimiento de servicio.</span><span class="sxs-lookup"><span data-stu-id="e860c-116">When attempting to view the logs, the two log files can be easily recombined by opening both of the log files at the same time in the Service Trace Viewer tool.</span></span> <span data-ttu-id="e860c-117">La herramienta Visor de seguimiento de servicio trata automáticamente de ordenar los seguimientos de manera que aparezcan en el orden correcto.</span><span class="sxs-lookup"><span data-stu-id="e860c-117">The Service Trace Viewer tool automatically takes care of sorting the traces so that they appear in the correct order.</span></span>

## <a name="configuration"></a><span data-ttu-id="e860c-118">Configuración</span><span class="sxs-lookup"><span data-stu-id="e860c-118">Configuration</span></span>

<span data-ttu-id="e860c-119">Se puede configurar un servicio para usar el Agente de escucha de seguimiento del búfer circular agregando el código siguiente para unos elementos de agente de escucha y origen.</span><span class="sxs-lookup"><span data-stu-id="e860c-119">A service can be configured to use the Circular Buffer Trace Listener by adding the following code for a listener and source elements.</span></span> <span data-ttu-id="e860c-120">El tamaño máximo de archivo se especifica estableciendo el atributo `maxFileSizeKB` en la configuración del agente de escucha de seguimiento circular.</span><span class="sxs-lookup"><span data-stu-id="e860c-120">The max file size is specified by setting the `maxFileSizeKB` attribute in the circular trace listener's configuration.</span></span> <span data-ttu-id="e860c-121">Esto último se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="e860c-121">This is demonstrated in the following code.</span></span>

```xml
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">
      <listeners>
        <add name="CircularTraceListener" />
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />
  </sharedListeners>
  <trace autoflush="true" />
</system.diagnostics>
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e860c-122">Configurar, compilar y ejecutar el ejemplo</span><span class="sxs-lookup"><span data-stu-id="e860c-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="e860c-123">Asegúrese de que ha realizado el [procedimiento de instalación única para los ejemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e860c-123">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="e860c-124">Para compilar el código C# o Visual Basic .NET Edition de la solución, siga las instrucciones de [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e860c-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="e860c-125">Para ejecutar el ejemplo en una configuración de equipos única o cruzada, siga las instrucciones de [ejecución de los ejemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e860c-125">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e860c-126">Puede que los ejemplos ya estén instalados en su equipo.</span><span class="sxs-lookup"><span data-stu-id="e860c-126">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e860c-127">Compruebe el siguiente directorio (predeterminado) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e860c-127">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e860c-128">Si este directorio no existe, vaya a [ejemplos de Windows Communication Foundation (WCF) y Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos.</span><span class="sxs-lookup"><span data-stu-id="e860c-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e860c-129">Este ejemplo se encuentra en el siguiente directorio.</span><span class="sxs-lookup"><span data-stu-id="e860c-129">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`

## <a name="see-also"></a><span data-ttu-id="e860c-130">Vea también</span><span class="sxs-lookup"><span data-stu-id="e860c-130">See also</span></span>

- <span data-ttu-id="e860c-131">[Ejemplos de supervisión de AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e860c-131">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>

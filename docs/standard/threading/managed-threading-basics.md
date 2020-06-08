---
title: Principios básicos del subprocesamiento administrado
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: 4d2a96619fd1c48c79b5590efdb52c307d29710c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291011"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="eda74-102">Principios básicos del subprocesamiento administrado</span><span class="sxs-lookup"><span data-stu-id="eda74-102">Managed threading basics</span></span>

<span data-ttu-id="eda74-103">Los cinco primeros temas de esta sección están diseñados para ayudarle a determinar cuándo se debe utilizar un subproceso administrado así como para explicar algunas características básicas.</span><span class="sxs-lookup"><span data-stu-id="eda74-103">The first five topics of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="eda74-104">Para obtener información sobre las clases que proporcionan características adicionales, vea [Objetos y características de subprocesos](threading-objects-and-features.md) e [Información general sobre los primitivos de sincronización](overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="eda74-104">For information on classes that provide additional features, see [Threading Objects and Features](threading-objects-and-features.md) and [Overview of Synchronization Primitives](overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="eda74-105">En el resto de los temas de esta sección se tratan cuestiones más avanzadas, incluida la interacción del subproceso administrado con el sistema operativo Windows.</span><span class="sxs-lookup"><span data-stu-id="eda74-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eda74-106">En .NET Framework 4, la biblioteca TPL y PLINQ proporcionan API para el paralelismo de tareas y datos en programas multiproceso.</span><span class="sxs-lookup"><span data-stu-id="eda74-106">In the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="eda74-107">Para más información, consulte [Parallel Programming](../parallel-programming/index.md) (Programación en paralelo).</span><span class="sxs-lookup"><span data-stu-id="eda74-107">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eda74-108">En esta sección</span><span class="sxs-lookup"><span data-stu-id="eda74-108">In this section</span></span>

 [<span data-ttu-id="eda74-109">Subprocesos y subprocesamiento</span><span class="sxs-lookup"><span data-stu-id="eda74-109">Threads and Threading</span></span>](threads-and-threading.md)  
 <span data-ttu-id="eda74-110">Se explican las ventajas y desventajas de varios subprocesos y se describen los escenarios en los que puede crear subprocesos o utilizar subprocesos del grupo de subprocesos.</span><span class="sxs-lookup"><span data-stu-id="eda74-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="eda74-111">Excepciones en subprocesos administrados</span><span class="sxs-lookup"><span data-stu-id="eda74-111">Exceptions in Managed Threads</span></span>](exceptions-in-managed-threads.md)  
 <span data-ttu-id="eda74-112">Se describe el comportamiento de las excepciones no controladas en subprocesos de distintas versiones de .NET Framework, en particular las situaciones que pueden provocar la finalización de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="eda74-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="eda74-113">Sincronizar datos para subprocesamiento múltiple</span><span class="sxs-lookup"><span data-stu-id="eda74-113">Synchronizing Data for Multithreading</span></span>](synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="eda74-114">Se describen las estrategias de sincronización de datos en las clases que se utilizarán con varios subprocesos.</span><span class="sxs-lookup"><span data-stu-id="eda74-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="eda74-115">Subprocesos de primer y segundo plano</span><span class="sxs-lookup"><span data-stu-id="eda74-115">Foreground and Background Threads</span></span>](foreground-and-background-threads.md)  
 <span data-ttu-id="eda74-116">Se explican las diferencias entre los subprocesos en primer y segundo plano.</span><span class="sxs-lookup"><span data-stu-id="eda74-116">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="eda74-117">Subprocesamiento administrado y no administrado en Windows</span><span class="sxs-lookup"><span data-stu-id="eda74-117">Managed and Unmanaged Threading in Windows</span></span>](managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="eda74-118">Se describe la relación entre subprocesos administrados y no administrados, se enumeran los administrados equivalentes para las API de subprocesos de Windows y se describe la interacción entre apartamentos COM y subprocesos administrados.</span><span class="sxs-lookup"><span data-stu-id="eda74-118">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="eda74-119">Almacenamiento local para el subproceso: Campos estáticos relacionados con subproceso y ranuras de datos</span><span class="sxs-lookup"><span data-stu-id="eda74-119">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="eda74-120">Se describen los mecanismos de almacenamiento relacionados con subprocesos.</span><span class="sxs-lookup"><span data-stu-id="eda74-120">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="eda74-121">Referencia</span><span class="sxs-lookup"><span data-stu-id="eda74-121">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="eda74-122">Proporciona documentación de referencia para la clase **Thread**, que representa un subproceso administrado, independientemente de que provenga de código no administrado o que se creara en una aplicación administrada.</span><span class="sxs-lookup"><span data-stu-id="eda74-122">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="eda74-123">Proporciona una manera segura de implementar multithreading junto con objetos de interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="eda74-123">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="eda74-124">Secciones relacionadas</span><span class="sxs-lookup"><span data-stu-id="eda74-124">Related sections</span></span>

 [<span data-ttu-id="eda74-125">Información general sobre los primitivos de sincronización</span><span class="sxs-lookup"><span data-stu-id="eda74-125">Overview of Synchronization Primitives</span></span>](overview-of-synchronization-primitives.md)  
 <span data-ttu-id="eda74-126">Se describen las clases administradas utilizadas para sincronizar las actividades de varios subprocesos.</span><span class="sxs-lookup"><span data-stu-id="eda74-126">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="eda74-127">Procedimientos recomendados para el subprocesamiento administrado</span><span class="sxs-lookup"><span data-stu-id="eda74-127">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="eda74-128">Se describen los problemas comunes con multithreading y las estrategias para evitar problemas.</span><span class="sxs-lookup"><span data-stu-id="eda74-128">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="eda74-129">Programación en paralelo</span><span class="sxs-lookup"><span data-stu-id="eda74-129">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="eda74-130">Describe la biblioteca TPL y PLINQ, que simplifican significativamente el trabajo de crear aplicaciones de .NET Framework asincrónicas y multiproceso.</span><span class="sxs-lookup"><span data-stu-id="eda74-130">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>

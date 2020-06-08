---
title: ICorProfilerCallback3 (Interfaz)
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
ms.openlocfilehash: db07e2afa64ea2bf80416e6ab8cba5a4dcdc8dcf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499680"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="2cba0-102">ICorProfilerCallback3 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="2cba0-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="2cba0-103">Proporciona métodos de devolución de llamada que el Common Language Runtime (CLR) utiliza para comunicar la información de estado de asociación y desasociación al generador de perfiles.</span><span class="sxs-lookup"><span data-stu-id="2cba0-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2cba0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2cba0-104">Methods</span></span>  
  
|<span data-ttu-id="2cba0-105">Método</span><span class="sxs-lookup"><span data-stu-id="2cba0-105">Method</span></span>|<span data-ttu-id="2cba0-106">Descripción</span><span class="sxs-lookup"><span data-stu-id="2cba0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2cba0-107">Método InitializeForAttach</span><span class="sxs-lookup"><span data-stu-id="2cba0-107">InitializeForAttach Method</span></span>](icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="2cba0-108">Lo llama el CLR para dar al generador de perfiles una oportunidad de inicializar su estado después de una operación de adjuntar.</span><span class="sxs-lookup"><span data-stu-id="2cba0-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="2cba0-109">Método ProfilerAttachComplete</span><span class="sxs-lookup"><span data-stu-id="2cba0-109">ProfilerAttachComplete Method</span></span>](icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="2cba0-110">Lo llama el CLR para indicar que el generador de perfiles ahora puede llamar a los métodos de puesta al día.</span><span class="sxs-lookup"><span data-stu-id="2cba0-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="2cba0-111">Método ProfilerDetachSucceeded</span><span class="sxs-lookup"><span data-stu-id="2cba0-111">ProfilerDetachSucceeded Method</span></span>](icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="2cba0-112">Notifica al generador de perfiles que Common Language Runtime (CLR) está a punto de descargar el archivo DLL del generador de perfiles.</span><span class="sxs-lookup"><span data-stu-id="2cba0-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cba0-113">Observaciones</span><span class="sxs-lookup"><span data-stu-id="2cba0-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cba0-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2cba0-114">Requirements</span></span>  
 <span data-ttu-id="2cba0-115">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cba0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cba0-116">**Encabezado:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2cba0-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2cba0-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cba0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cba0-118">**.NET Framework versiones:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cba0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cba0-119">Consulte también:</span><span class="sxs-lookup"><span data-stu-id="2cba0-119">See also</span></span>

- [<span data-ttu-id="2cba0-120">Interfaces para generación de perfiles</span><span class="sxs-lookup"><span data-stu-id="2cba0-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="2cba0-121">ICorProfilerInfo (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="2cba0-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="2cba0-122">ICorProfilerCallback2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="2cba0-122">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="2cba0-123">ICorProfilerCallback4 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="2cba0-123">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)

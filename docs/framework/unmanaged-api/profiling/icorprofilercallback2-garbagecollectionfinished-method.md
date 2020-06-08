---
title: ICorProfilerCallback2::GarbageCollectionFinished (Método)
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished
helpviewer_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished method [.NET Framework profiling]
- GarbageCollectionFinished method [.NET Framework profiling]
ms.assetid: 1a5758ea-2354-43c0-92a3-32c9909d64e1
topic_type:
- apiref
ms.openlocfilehash: 47f25dbb1f88dbf580b096246016cd46f2d0d89c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499836"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="78a67-102">ICorProfilerCallback2::GarbageCollectionFinished (Método)</span><span class="sxs-lookup"><span data-stu-id="78a67-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="78a67-103">Notifica al generador de perfiles que se ha completado la recolección de elementos no utilizados y que se han emitido todas las devoluciones de llamada de recolección de elementos no utilizados.</span><span class="sxs-lookup"><span data-stu-id="78a67-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78a67-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="78a67-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="78a67-105">Comentarios</span><span class="sxs-lookup"><span data-stu-id="78a67-105">Remarks</span></span>  
 <span data-ttu-id="78a67-106">Es seguro que el generador de perfiles Inspeccione los objetos en sus ubicaciones finales cuando `GarbageCollectionFinished` se llama al método.</span><span class="sxs-lookup"><span data-stu-id="78a67-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78a67-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="78a67-107">Requirements</span></span>  
 <span data-ttu-id="78a67-108">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78a67-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78a67-109">**Encabezado:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="78a67-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="78a67-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78a67-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78a67-111">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78a67-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78a67-112">Consulte también:</span><span class="sxs-lookup"><span data-stu-id="78a67-112">See also</span></span>

- [<span data-ttu-id="78a67-113">ICorProfilerCallback (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="78a67-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="78a67-114">ICorProfilerCallback2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="78a67-114">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)

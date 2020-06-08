---
title: FunctionEnter3 (Función)
ms.date: 03/30/2017
api_name:
- FunctionEnter3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter3
helpviewer_keywords:
- FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type:
- apiref
ms.openlocfilehash: b435e1a3504dd623421f977ffc48264f8b0dcb5a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500707"
---
# <a name="functionenter3-function"></a><span data-ttu-id="33ece-102">FunctionEnter3 (Función)</span><span class="sxs-lookup"><span data-stu-id="33ece-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="33ece-103">Notifica al generador de perfiles que el control se pasa a una función.</span><span class="sxs-lookup"><span data-stu-id="33ece-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33ece-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="33ece-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33ece-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="33ece-105">Parameters</span></span>

- `functionOrRemappedID`

  <span data-ttu-id="33ece-106">\[in] el identificador de la función a la que se pasa el control.</span><span class="sxs-lookup"><span data-stu-id="33ece-106">\[in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="33ece-107">Comentarios</span><span class="sxs-lookup"><span data-stu-id="33ece-107">Remarks</span></span>  
 <span data-ttu-id="33ece-108">La `FunctionEnter3` función de devolución de llamada notifica al generador de perfiles cuando se llama a las funciones, pero no admite la inspección de argumentos.</span><span class="sxs-lookup"><span data-stu-id="33ece-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="33ece-109">Use el [método ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 (](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) para registrar su implementación de esta función.</span><span class="sxs-lookup"><span data-stu-id="33ece-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="33ece-110">La `FunctionEnter3` función es una devolución de llamada; debe implementarla.</span><span class="sxs-lookup"><span data-stu-id="33ece-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="33ece-111">La implementación debe usar el `__declspec(naked)` atributo de clase de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="33ece-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="33ece-112">El motor de ejecución no guarda ningún registro antes de llamar a esta función.</span><span class="sxs-lookup"><span data-stu-id="33ece-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="33ece-113">En la entrada, debe guardar todos los registros que use, incluidos los de la unidad de punto flotante (FPU).</span><span class="sxs-lookup"><span data-stu-id="33ece-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="33ece-114">Al salir, debe restaurar la pila desactivando todos los parámetros insertados por el autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="33ece-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33ece-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="33ece-115">Requirements</span></span>  
 <span data-ttu-id="33ece-116">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33ece-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33ece-117">**Encabezado:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="33ece-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="33ece-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33ece-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33ece-119">**.NET Framework versiones:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33ece-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33ece-120">Consulte también:</span><span class="sxs-lookup"><span data-stu-id="33ece-120">See also</span></span>

- [<span data-ttu-id="33ece-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="33ece-121">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="33ece-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="33ece-122">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="33ece-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="33ece-123">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="33ece-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="33ece-124">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="33ece-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="33ece-125">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="33ece-126">Setenterleavefunctionhooks3 (</span><span class="sxs-lookup"><span data-stu-id="33ece-126">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="33ece-127">Setenterleavefunctionhooks3withinfo (</span><span class="sxs-lookup"><span data-stu-id="33ece-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="33ece-128">Setfunctionidmapper (</span><span class="sxs-lookup"><span data-stu-id="33ece-128">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="33ece-129">Setfunctionidmapper2 (</span><span class="sxs-lookup"><span data-stu-id="33ece-129">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="33ece-130">Funciones estáticas globales para generación de perfiles</span><span class="sxs-lookup"><span data-stu-id="33ece-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)

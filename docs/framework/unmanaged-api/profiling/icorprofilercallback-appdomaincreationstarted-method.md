---
title: ICorProfilerCallback::AppDomainCreationStarted (Método)
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationStarted
helpviewer_keywords:
- AppDomainCreationStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationStarted method [.NET Framework profiling]
ms.assetid: b2a8240b-07fe-4859-bb2b-7d3adbfa0a9f
topic_type:
- apiref
ms.openlocfilehash: fcebe65b7f39dd2849946e445a694ad5e9b1a65d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500486"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="999aa-102">ICorProfilerCallback::AppDomainCreationStarted (Método)</span><span class="sxs-lookup"><span data-stu-id="999aa-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="999aa-103">Notifica al generador de perfiles que se está creando un dominio de aplicación.</span><span class="sxs-lookup"><span data-stu-id="999aa-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="999aa-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="999aa-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="999aa-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="999aa-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="999aa-106">\[en] identifica el dominio que se va a crear.</span><span class="sxs-lookup"><span data-stu-id="999aa-106">\[in] Identifies the domain which is being created.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="999aa-107">Comentarios</span><span class="sxs-lookup"><span data-stu-id="999aa-107">Remarks</span></span>  
 <span data-ttu-id="999aa-108">El identificador no es válido para ninguna solicitud de información hasta que se llama al método [ICorProfilerCallback:: AppDomainCreationFinished (](icorprofilercallback-appdomaincreationfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="999aa-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="999aa-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="999aa-109">Requirements</span></span>  
 <span data-ttu-id="999aa-110">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="999aa-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="999aa-111">**Encabezado:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="999aa-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="999aa-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="999aa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="999aa-113">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="999aa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="999aa-114">Consulte también:</span><span class="sxs-lookup"><span data-stu-id="999aa-114">See also</span></span>

- [<span data-ttu-id="999aa-115">ICorProfilerCallback (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="999aa-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)

---
title: ICorProfilerInfo::GetILFunctionBodyAllocator (Método)
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBodyAllocator
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type:
- apiref
ms.openlocfilehash: 967f38add9ae5996c6ac33388203b55161a84e39
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498276"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a><span data-ttu-id="636ec-102">ICorProfilerInfo::GetILFunctionBodyAllocator (Método)</span><span class="sxs-lookup"><span data-stu-id="636ec-102">ICorProfilerInfo::GetILFunctionBodyAllocator Method</span></span>
<span data-ttu-id="636ec-103">Obtiene una interfaz que proporciona un método para asignar la memoria que se va a usar para intercambiar el cuerpo de un método en el código del lenguaje intermedio de Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="636ec-103">Gets an interface that provides a method to allocate memory to be used for swapping out the body of a method in Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="636ec-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="636ec-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="636ec-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="636ec-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="636ec-106">de IDENTIFICADOR del módulo en el que reside el método.</span><span class="sxs-lookup"><span data-stu-id="636ec-106">[in] The ID of the module in which the method resides.</span></span>  
  
 `ppMalloc`  
 <span data-ttu-id="636ec-107">enuncia Puntero a una interfaz [IMethodMalloc](imethodmalloc-interface.md) que proporciona un método para asignar la memoria.</span><span class="sxs-lookup"><span data-stu-id="636ec-107">[out] A pointer to an [IMethodMalloc](imethodmalloc-interface.md) interface that provides a method to allocate the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="636ec-108">Comentarios</span><span class="sxs-lookup"><span data-stu-id="636ec-108">Remarks</span></span>  
 <span data-ttu-id="636ec-109">Un cuerpo de método en código MSIL debe estar ubicado como una dirección virtual relativa (RVA), relativa al módulo cargado, lo que significa que sigue el módulo en un plazo de 4 GB.</span><span class="sxs-lookup"><span data-stu-id="636ec-109">A method body in MSIL code must be located as a relative virtual address (RVA), relative to the loaded module, which means that it follows the module within 4 GB.</span></span> <span data-ttu-id="636ec-110">Para facilitar a una herramienta el intercambio del cuerpo de un método, el `GetILFunctionBodyAllocator` método garantiza que la memoria se asigna dentro de ese intervalo.</span><span class="sxs-lookup"><span data-stu-id="636ec-110">To make it easier for a tool to swap out the body of a method, the `GetILFunctionBodyAllocator` method ensures that memory is allocated within that range.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="636ec-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="636ec-111">Requirements</span></span>  
 <span data-ttu-id="636ec-112">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="636ec-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="636ec-113">**Encabezado:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="636ec-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="636ec-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="636ec-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="636ec-115">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="636ec-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="636ec-116">Consulte también:</span><span class="sxs-lookup"><span data-stu-id="636ec-116">See also</span></span>

- [<span data-ttu-id="636ec-117">ICorProfilerInfo (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="636ec-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)

---
title: ICorPublishEnum::Clone (Método)
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type:
- apiref
ms.openlocfilehash: 38f49e8fe632e9b38ede8815de6d8865278351f9
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421207"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="0bd36-102">ICorPublishEnum::Clone (Método)</span><span class="sxs-lookup"><span data-stu-id="0bd36-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="0bd36-103">Crea una copia de este objeto [ICorPublishEnum](icorpublishenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0bd36-103">Creates a copy of this [ICorPublishEnum](icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bd36-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0bd36-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bd36-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0bd36-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="0bd36-106">enuncia Puntero a la dirección de un `ICorPublishEnum` objeto que es una copia de este `ICorPublishEnum` objeto.</span><span class="sxs-lookup"><span data-stu-id="0bd36-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bd36-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0bd36-107">Requirements</span></span>  
 <span data-ttu-id="0bd36-108">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bd36-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bd36-109">**Encabezado:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="0bd36-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="0bd36-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bd36-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bd36-111">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bd36-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bd36-112">Consulta también</span><span class="sxs-lookup"><span data-stu-id="0bd36-112">See also</span></span>

- [<span data-ttu-id="0bd36-113">ICorPublishEnum (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="0bd36-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)

---
title: IMetaDataImport::GetModuleFromScope (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
ms.openlocfilehash: 4e2b2501b6b7117cefcfa43511ef20f25106bb42
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503593"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="fc3e0-102">IMetaDataImport::GetModuleFromScope (Método)</span><span class="sxs-lookup"><span data-stu-id="fc3e0-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="fc3e0-103">Obtiene un símbolo (token) de metadatos para el módulo al que se hace referencia en el ámbito de metadatos actual.</span><span class="sxs-lookup"><span data-stu-id="fc3e0-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc3e0-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fc3e0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc3e0-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="fc3e0-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="fc3e0-106">enuncia Puntero al token que representa el módulo al que se hace referencia en el ámbito de metadatos actual.</span><span class="sxs-lookup"><span data-stu-id="fc3e0-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc3e0-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc3e0-107">Requirements</span></span>  
 <span data-ttu-id="fc3e0-108">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc3e0-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc3e0-109">**Encabezado:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fc3e0-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc3e0-110">**Biblioteca:** Se incluye como recurso en MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fc3e0-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fc3e0-111">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc3e0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc3e0-112">Consulte también:</span><span class="sxs-lookup"><span data-stu-id="fc3e0-112">See also</span></span>

- [<span data-ttu-id="fc3e0-113">IMetaDataImport (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="fc3e0-113">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="fc3e0-114">IMetaDataImport2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="fc3e0-114">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

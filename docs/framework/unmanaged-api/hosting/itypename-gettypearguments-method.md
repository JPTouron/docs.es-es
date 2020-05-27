---
title: ITypeName::GetTypeArguments (Método)
ms.date: 03/30/2017
api_name:
- ITypeName.GetTypeArguments
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetTypeArguments
helpviewer_keywords:
- ITypeName::GetTypeArguments method [.NET Framework hosting]
- GetTypeArguments method [.NET Framework hosting]
ms.assetid: 638d77df-ff9c-40d9-88ee-930f5f87ada1
topic_type:
- apiref
ms.openlocfilehash: e059cdddef7926c1359a83bc562146203724aa60
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842127"
---
# <a name="itypenamegettypearguments-method"></a><span data-ttu-id="55a83-102">ITypeName::GetTypeArguments (Método)</span><span class="sxs-lookup"><span data-stu-id="55a83-102">ITypeName::GetTypeArguments Method</span></span>
<span data-ttu-id="55a83-103">Este método es compatible con la infraestructura de .NET Framework y no está diseñado para utilizarse directamente desde el código.</span><span class="sxs-lookup"><span data-stu-id="55a83-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55a83-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="55a83-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeArguments (  
    [in] DWORD           count,  
    [out] ITypeName**    rgpArguments,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="55a83-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="55a83-105">Requirements</span></span>  
 <span data-ttu-id="55a83-106">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55a83-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55a83-107">**Encabezado:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="55a83-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="55a83-108">**Biblioteca:** Se incluye como recurso en MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="55a83-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="55a83-109">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55a83-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55a83-110">Vea también</span><span class="sxs-lookup"><span data-stu-id="55a83-110">See also</span></span>

- [<span data-ttu-id="55a83-111">Interfaces de hospedaje</span><span class="sxs-lookup"><span data-stu-id="55a83-111">Hosting Interfaces</span></span>](hosting-interfaces.md)

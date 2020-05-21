---
title: ICLRStrongName::StrongNameGetBlob (Método)
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type:
- apiref
ms.openlocfilehash: f93d3f0322de89b2e9ce596329c06b58db9fdcdc
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760308"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="20ad4-102">ICLRStrongName::StrongNameGetBlob (Método)</span><span class="sxs-lookup"><span data-stu-id="20ad4-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="20ad4-103">Llena el búfer especificado con la representación binaria del archivo ejecutable en la dirección especificada.</span><span class="sxs-lookup"><span data-stu-id="20ad4-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20ad4-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="20ad4-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20ad4-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="20ad4-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="20ad4-106">de Ruta de acceso válida al archivo ejecutable que se va a cargar.</span><span class="sxs-lookup"><span data-stu-id="20ad4-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="20ad4-107">de Búfer en el que se va a cargar el archivo ejecutable.</span><span class="sxs-lookup"><span data-stu-id="20ad4-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="20ad4-108">[in, out] Tamaño máximo solicitado, en bytes, de `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="20ad4-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="20ad4-109">Después de la devolución, el tamaño real, en bytes, de `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="20ad4-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20ad4-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="20ad4-110">Return Value</span></span>  
 <span data-ttu-id="20ad4-111">`S_OK`Si el método se completó correctamente; de lo contrario, un valor HRESULT que indica un error (vea [Valores HRESULT comunes](/windows/win32/seccrypto/common-hresult-values) para una lista).</span><span class="sxs-lookup"><span data-stu-id="20ad4-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20ad4-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="20ad4-112">Requirements</span></span>  
 <span data-ttu-id="20ad4-113">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20ad4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20ad4-114">**Encabezado:** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="20ad4-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="20ad4-115">**Biblioteca:** Se incluye como recurso en MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="20ad4-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20ad4-116">**.NET Framework versiones:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20ad4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ad4-117">Consulte también:</span><span class="sxs-lookup"><span data-stu-id="20ad4-117">See also</span></span>

- [<span data-ttu-id="20ad4-118">Método StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="20ad4-118">StrongNameGetBlobFromImage Method</span></span>](iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="20ad4-119">ICLRStrongName (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="20ad4-119">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)

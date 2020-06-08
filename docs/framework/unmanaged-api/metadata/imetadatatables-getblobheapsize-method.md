---
title: IMetaDataTables::GetBlobHeapSize (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlobHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlobHeapSize
helpviewer_keywords:
- GetBlobHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetBlobHeapSize method [.NET Framework metadata]
ms.assetid: 6330a9ee-8cd5-4299-86f1-b4de2c701a0d
topic_type:
- apiref
ms.openlocfilehash: 68e29e932e477f286db00b0c989a3346bd13c9bc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501227"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="9393e-102">IMetaDataTables::GetBlobHeapSize (Método)</span><span class="sxs-lookup"><span data-stu-id="9393e-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="9393e-103">Obtiene el tamaño, en bytes, del montón de objetos binarios grandes (BLOB).</span><span class="sxs-lookup"><span data-stu-id="9393e-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9393e-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9393e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="9393e-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9393e-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="9393e-106">enuncia Puntero al tamaño, en bytes, del montón de BLOBs.</span><span class="sxs-lookup"><span data-stu-id="9393e-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9393e-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9393e-107">Requirements</span></span>  
 <span data-ttu-id="9393e-108">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9393e-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9393e-109">**Encabezado:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9393e-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9393e-110">**Biblioteca:** Se utiliza como recurso en MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9393e-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9393e-111">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9393e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9393e-112">Consulte también:</span><span class="sxs-lookup"><span data-stu-id="9393e-112">See also</span></span>

- [<span data-ttu-id="9393e-113">IMetaDataTables (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="9393e-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="9393e-114">IMetaDataTables2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="9393e-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)

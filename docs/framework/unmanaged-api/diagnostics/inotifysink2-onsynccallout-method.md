---
title: INotifySink2::OnSyncCallOut (Método)
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
ms.openlocfilehash: ce0e192a9d7d5abf56a55f844cf886c386f1c563
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441999"
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="81a03-102">INotifySink2::OnSyncCallOut (Método)</span><span class="sxs-lookup"><span data-stu-id="81a03-102">INotifySink2::OnSyncCallOut Method</span></span>
<span data-ttu-id="81a03-103">Se invoca cuando se realiza una llamada.</span><span class="sxs-lookup"><span data-stu-id="81a03-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81a03-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="81a03-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81a03-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="81a03-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="81a03-106">de IDENTIFICADOR de la llamada que está fuera. Vea [estructura de CALL_ID](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="81a03-106">[in] ID of the call that is out. See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="81a03-107">enuncia Búfer de llamadas.</span><span class="sxs-lookup"><span data-stu-id="81a03-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="81a03-108">enuncia Tamaño del búfer de llamadas, en bytes.</span><span class="sxs-lookup"><span data-stu-id="81a03-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81a03-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="81a03-109">Return Value</span></span>  
 <span data-ttu-id="81a03-110">S_OK si el método se ejecuta correctamente.</span><span class="sxs-lookup"><span data-stu-id="81a03-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81a03-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81a03-111">Requirements</span></span>  
 <span data-ttu-id="81a03-112">**Encabezado:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="81a03-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81a03-113">Consulta también</span><span class="sxs-lookup"><span data-stu-id="81a03-113">See also</span></span>

- [<span data-ttu-id="81a03-114">INotifySink2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="81a03-114">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="81a03-115">INotifySource2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="81a03-115">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="81a03-116">INotifyConnection2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="81a03-116">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)

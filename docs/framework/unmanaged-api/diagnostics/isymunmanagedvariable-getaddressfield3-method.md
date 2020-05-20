---
title: ISymUnmanagedVariable::GetAddressField3 (Método)
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type:
- apiref
ms.openlocfilehash: ff888d3e2b86efeea3f4e3d33528f731d85886bf
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615272"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="70e49-102">ISymUnmanagedVariable::GetAddressField3 (Método)</span><span class="sxs-lookup"><span data-stu-id="70e49-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="70e49-103">Obtiene el tercer campo de dirección para esta variable.</span><span class="sxs-lookup"><span data-stu-id="70e49-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="70e49-104">Su significado depende del tipo de dirección.</span><span class="sxs-lookup"><span data-stu-id="70e49-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70e49-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="70e49-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70e49-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="70e49-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="70e49-107">enuncia Un puntero a un `ULONG32` que recibe el tercer campo de dirección.</span><span class="sxs-lookup"><span data-stu-id="70e49-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70e49-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="70e49-108">Return Value</span></span>  
 <span data-ttu-id="70e49-109">S_OK si el método se ejecuta correctamente; de lo contrario, E_FAIL u otro código de error.</span><span class="sxs-lookup"><span data-stu-id="70e49-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70e49-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="70e49-110">Requirements</span></span>  
 <span data-ttu-id="70e49-111">**Encabezado:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="70e49-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70e49-112">Consulta también</span><span class="sxs-lookup"><span data-stu-id="70e49-112">See also</span></span>

- [<span data-ttu-id="70e49-113">ISymUnmanagedVariable (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="70e49-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="70e49-114">Método GetAddressField1</span><span class="sxs-lookup"><span data-stu-id="70e49-114">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="70e49-115">Método GetAddressField2</span><span class="sxs-lookup"><span data-stu-id="70e49-115">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="70e49-116">Método GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="70e49-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)

---
title: ISymUnmanagedWriter::OpenMethod (Método)
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
ms.openlocfilehash: d2d16ab0a29fadd3a64d906a64fc46c422e01c45
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610046"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="28e81-102">ISymUnmanagedWriter::OpenMethod (Método)</span><span class="sxs-lookup"><span data-stu-id="28e81-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="28e81-103">Abre un método en el que se emite información de símbolos.</span><span class="sxs-lookup"><span data-stu-id="28e81-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="28e81-104">El método especificado se convierte en el método actual para que las llamadas definan los puntos de secuencia, los parámetros y los ámbitos léxicos.</span><span class="sxs-lookup"><span data-stu-id="28e81-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="28e81-105">Hay un ámbito léxico implícito en torno al método completo.</span><span class="sxs-lookup"><span data-stu-id="28e81-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="28e81-106">Al volver a abrir un método que se cerró previamente, se borran los símbolos definidos previamente para ese método.</span><span class="sxs-lookup"><span data-stu-id="28e81-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="28e81-107">Solo puede haber un método abierto a la vez.</span><span class="sxs-lookup"><span data-stu-id="28e81-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28e81-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="28e81-108">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28e81-109">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28e81-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="28e81-110">de Símbolo (token) de metadatos para el método que se va a abrir.</span><span class="sxs-lookup"><span data-stu-id="28e81-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28e81-111">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="28e81-111">Return Value</span></span>  
 <span data-ttu-id="28e81-112">S_OK si el método se ejecuta correctamente; de lo contrario, E_FAIL u otro código de error.</span><span class="sxs-lookup"><span data-stu-id="28e81-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28e81-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="28e81-113">Requirements</span></span>  
 <span data-ttu-id="28e81-114">**Encabezado:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="28e81-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28e81-115">Consulta también</span><span class="sxs-lookup"><span data-stu-id="28e81-115">See also</span></span>

- [<span data-ttu-id="28e81-116">ISymUnmanagedWriter (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="28e81-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="28e81-117">Método CloseMethod</span><span class="sxs-lookup"><span data-stu-id="28e81-117">CloseMethod Method</span></span>](isymunmanagedwriter-closemethod-method.md)
- [<span data-ttu-id="28e81-118">Método OpenMethod2</span><span class="sxs-lookup"><span data-stu-id="28e81-118">OpenMethod2 Method</span></span>](isymunmanagedwriter3-openmethod2-method.md)

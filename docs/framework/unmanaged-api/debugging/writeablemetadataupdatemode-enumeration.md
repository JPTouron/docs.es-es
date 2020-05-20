---
title: WriteableMetadataUpdateMode (Enumeración)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- WriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type:
- apiref
ms.openlocfilehash: 0793dcbe4d080da83cf507e04303d66fbbb56b85
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420648"
---
# <a name="writeablemetadataupdatemode-enumeration"></a><span data-ttu-id="ef06d-102">WriteableMetadataUpdateMode (Enumeración)</span><span class="sxs-lookup"><span data-stu-id="ef06d-102">WriteableMetadataUpdateMode Enumeration</span></span>
<span data-ttu-id="ef06d-103">[Compatible con .NET Framework 4.5.2 y versiones posteriores]</span><span class="sxs-lookup"><span data-stu-id="ef06d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ef06d-104">Proporciona valores que especifican si las actualizaciones en memoria de los metadatos son visibles para un depurador.</span><span class="sxs-lookup"><span data-stu-id="ef06d-104">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef06d-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ef06d-105">Syntax</span></span>  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a><span data-ttu-id="ef06d-106">Miembros</span><span class="sxs-lookup"><span data-stu-id="ef06d-106">Members</span></span>  
  
|<span data-ttu-id="ef06d-107">Nombre del miembro</span><span class="sxs-lookup"><span data-stu-id="ef06d-107">Member name</span></span>|<span data-ttu-id="ef06d-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="ef06d-108">Description</span></span>|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|<span data-ttu-id="ef06d-109">Mantiene la compatibilidad con versiones anteriores de .NET Framework al hacer que las actualizaciones en memoria de los metadatos sean visibles.</span><span class="sxs-lookup"><span data-stu-id="ef06d-109">Maintain compatibility with previous versions of the .NET Framework when making in-memory updates to metadata visible.</span></span> <span data-ttu-id="ef06d-110">Para obtener más información, vea la sección Comentarios.</span><span class="sxs-lookup"><span data-stu-id="ef06d-110">See the Remarks section for more information.</span></span>|  
|`AlwaysShowUpdates`|<span data-ttu-id="ef06d-111">Hace que las actualizaciones en memoria de los metadatos sean visibles para el depurador.</span><span class="sxs-lookup"><span data-stu-id="ef06d-111">Make in-memory updates to metadata visible to the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef06d-112">Observaciones</span><span class="sxs-lookup"><span data-stu-id="ef06d-112">Remarks</span></span>  
 <span data-ttu-id="ef06d-113">Un miembro de la `WriteableMetadataUpdateMode` enumeración se puede pasar al método [setwriteablemetadataupdatemode (](icordebugprocess7-setwriteablemetadataupdatemode-method.md) para controlar si el depurador puede ver las actualizaciones en memoria de los metadatos en el proceso de destino.</span><span class="sxs-lookup"><span data-stu-id="ef06d-113">A member of the `WriteableMetadataUpdateMode` enumeration can be passed to the [SetWriteableMetadataUpdateMode](icordebugprocess7-setwriteablemetadataupdatemode-method.md) method to control whether in-memory updates to metadata in the target process are visible to the debugger.</span></span>  
  
 <span data-ttu-id="ef06d-114">La opción `LegacyCompatPolicy` aplica el mismo comportamiento que en las versiones de .NET Framework anteriores a la 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="ef06d-114">The `LegacyCompatPolicy` option enforces the same behavior as in versions of the .NET Framework before 4.5.2.</span></span> <span data-ttu-id="ef06d-115">Esto suele significar que los metadatos de las actualizaciones no son visibles.</span><span class="sxs-lookup"><span data-stu-id="ef06d-115">This often means that metadata from updates is not visible.</span></span> <span data-ttu-id="ef06d-116">Sin embargo, las llamadas a varios métodos de depuración obligan implícitamente al depurador a hacer las actualizaciones visibles.</span><span class="sxs-lookup"><span data-stu-id="ef06d-116">However, calls to a number of debugging methods implicitly coerce the debugger to make updates visible.</span></span> <span data-ttu-id="ef06d-117">Por ejemplo, si el depurador pasa [ICorDebugILFrame:: getlocalvariable (](icordebugilframe-getlocalvariable-method.md) , el índice de una variable no se encuentra en los metadatos originales del método, todos los metadatos del módulo se actualizan a una instantánea que coincide con el estado actual del proceso.</span><span class="sxs-lookup"><span data-stu-id="ef06d-117">For example, if the debugger passes [ICorDebugILFrame::GetLocalVariable](icordebugilframe-getlocalvariable-method.md) the index of a variable not found in the method's original metadata, all metadata for the module is updated to a snapshot matching the current state of the process.</span></span> <span data-ttu-id="ef06d-118">En otras palabras, con la opción `LegacyCompatPolicy`, el depurador podría ver ninguna, algunas o todas las actualizaciones de metadatos disponibles, según cómo use otras partes de la API de depuración no administrada.</span><span class="sxs-lookup"><span data-stu-id="ef06d-118">In other words, with the `LegacyCompatPolicy` option, the debugger might see none, some, or all of the available metadata updates, depending on how it uses other parts of the unmanaged debugging API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef06d-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ef06d-119">Requirements</span></span>  
 <span data-ttu-id="ef06d-120">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef06d-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef06d-121">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef06d-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef06d-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef06d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef06d-123">**.NET Framework versiones:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef06d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef06d-124">Consulta también</span><span class="sxs-lookup"><span data-stu-id="ef06d-124">See also</span></span>

- [<span data-ttu-id="ef06d-125">Enumeraciones de depuración</span><span class="sxs-lookup"><span data-stu-id="ef06d-125">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="ef06d-126">SetWriteableMetadataUpdateMode (método)</span><span class="sxs-lookup"><span data-stu-id="ef06d-126">SetWriteableMetadataUpdateMode Method</span></span>](icordebugprocess7-setwriteablemetadataupdatemode-method.md)

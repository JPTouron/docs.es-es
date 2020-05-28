---
title: CorSerializationType (Enumeración)
ms.date: 03/30/2017
api_name:
- CorSerializationType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSerializationType
helpviewer_keywords:
- CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type:
- apiref
ms.openlocfilehash: 649a9159f99afa64615c40c23a98a80318ae0d7f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009176"
---
# <a name="corserializationtype-enumeration"></a><span data-ttu-id="d7237-102">CorSerializationType (Enumeración)</span><span class="sxs-lookup"><span data-stu-id="d7237-102">CorSerializationType Enumeration</span></span>
<span data-ttu-id="d7237-103">Especifica cómo el Common Language Runtime serializa un objeto.</span><span class="sxs-lookup"><span data-stu-id="d7237-103">Specifies how an object is serialized by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7237-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d7237-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a><span data-ttu-id="d7237-105">Miembros</span><span class="sxs-lookup"><span data-stu-id="d7237-105">Members</span></span>  
  
|<span data-ttu-id="d7237-106">Miembro</span><span class="sxs-lookup"><span data-stu-id="d7237-106">Member</span></span>|<span data-ttu-id="d7237-107">Descripción</span><span class="sxs-lookup"><span data-stu-id="d7237-107">Description</span></span>|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|<span data-ttu-id="d7237-108">La serialización del objeto no está definida.</span><span class="sxs-lookup"><span data-stu-id="d7237-108">Serialization of the object is undefined.</span></span>|  
|`SERIALIZATION_TYPE_BOOLEAN`|<span data-ttu-id="d7237-109">El objeto se serializa como un tipo booleano</span><span class="sxs-lookup"><span data-stu-id="d7237-109">Object is serialized as a Boolean type</span></span>|  
|`SERIALIZATION_TYPE_CHAR`|<span data-ttu-id="d7237-110">El objeto se serializa como un tipo de carácter.</span><span class="sxs-lookup"><span data-stu-id="d7237-110">Object is serialized as a character type.</span></span>|  
|`SERIALIZATION_TYPE_I1`|<span data-ttu-id="d7237-111">El objeto se serializa como un entero de 1 byte con signo.</span><span class="sxs-lookup"><span data-stu-id="d7237-111">Object is serialized as a signed 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U1`|<span data-ttu-id="d7237-112">El objeto se serializa como un entero de 1 byte sin signo.</span><span class="sxs-lookup"><span data-stu-id="d7237-112">Object is serialized as an unsigned 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I2`|<span data-ttu-id="d7237-113">El objeto se serializa como un entero de 2 bytes con signo.</span><span class="sxs-lookup"><span data-stu-id="d7237-113">Object is serialized as a signed 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U2`|<span data-ttu-id="d7237-114">El objeto se serializa como un entero de 2 bytes sin signo.</span><span class="sxs-lookup"><span data-stu-id="d7237-114">Object is serialized as an unsigned 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I4`|<span data-ttu-id="d7237-115">El objeto se serializa como un entero de 4 bytes con signo.</span><span class="sxs-lookup"><span data-stu-id="d7237-115">Object is serialized as a signed 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U4`|<span data-ttu-id="d7237-116">El objeto se serializa como un entero de 4 bytes sin signo.</span><span class="sxs-lookup"><span data-stu-id="d7237-116">Object is serialized as an unsigned 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I8`|<span data-ttu-id="d7237-117">El objeto se serializa como un entero de 8 bytes con signo.</span><span class="sxs-lookup"><span data-stu-id="d7237-117">Object is serialized as a signed 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U8`|<span data-ttu-id="d7237-118">El objeto se serializa como un entero de 8 bytes sin signo.</span><span class="sxs-lookup"><span data-stu-id="d7237-118">Object is serialized as an unsigned 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_R4`|<span data-ttu-id="d7237-119">El objeto se serializa como un punto flotante de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="d7237-119">Object is serialized as a 4-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_R8`|<span data-ttu-id="d7237-120">El objeto se serializa como un punto flotante de 8 bytes.</span><span class="sxs-lookup"><span data-stu-id="d7237-120">Object is serialized as an 8-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_STRING`|<span data-ttu-id="d7237-121">El objeto se serializa como un tipo System. String.</span><span class="sxs-lookup"><span data-stu-id="d7237-121">Object is serialized as a System.String type.</span></span>|  
|`SERIALIZATION_TYPE_SZARRAY`|<span data-ttu-id="d7237-122">El objeto se serializa como una matriz unidimensional de límite inferior de cero.</span><span class="sxs-lookup"><span data-stu-id="d7237-122">Object is serialized as a single-dimensional, zero lower-bound array.</span></span>|  
|`SERIALIZATION_TYPE_TYPE`|<span data-ttu-id="d7237-123">El objeto se serializa como un tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="d7237-123">Object is serialized as a generic type.</span></span>|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|<span data-ttu-id="d7237-124">El objeto se serializa como un objeto etiquetado.</span><span class="sxs-lookup"><span data-stu-id="d7237-124">Object is serialized as a tagged object.</span></span>|  
|`SERIALIZATION_TYPE_FIELD`|<span data-ttu-id="d7237-125">El objeto se serializa como un campo.</span><span class="sxs-lookup"><span data-stu-id="d7237-125">Object is serialized as a field.</span></span>|  
|`SERIALIZATION_TYPE_PROPERTY`|<span data-ttu-id="d7237-126">El objeto se serializa como una propiedad.</span><span class="sxs-lookup"><span data-stu-id="d7237-126">Object is serialized as a property.</span></span>|  
|`SERIALIZATION_TYPE_ENUM`|<span data-ttu-id="d7237-127">El objeto se serializa como una enumeración.</span><span class="sxs-lookup"><span data-stu-id="d7237-127">Object is serialized as an enumeration.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d7237-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7237-128">Requirements</span></span>  
 <span data-ttu-id="d7237-129">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7237-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7237-130">**Encabezado:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="d7237-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d7237-131">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7237-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7237-132">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d7237-132">See also</span></span>

- [<span data-ttu-id="d7237-133">Enumeraciones para metadatos</span><span class="sxs-lookup"><span data-stu-id="d7237-133">Metadata Enumerations</span></span>](metadata-enumerations.md)

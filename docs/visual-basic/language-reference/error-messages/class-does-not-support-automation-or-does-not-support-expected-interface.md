---
title: Esta clase no admite automatización o no admite la interfaz esperada
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: 856c3f5ef503a7e5919e9e602532c56d9557482f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415406"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="d2fa9-102">Esta clase no admite automatización o no admite la interfaz esperada</span><span class="sxs-lookup"><span data-stu-id="d2fa9-102">Class does not support Automation or does not support expected interface</span></span>
<span data-ttu-id="d2fa9-103">La clase especificada en la llamada a la función `GetObject` o a la función `CreateObject` no ha expuesto una interfaz de programación, o bien el proyecto se ha cambiado de .dll a .exe (o a la inversa).</span><span class="sxs-lookup"><span data-stu-id="d2fa9-103">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d2fa9-104">Para corregir este error</span><span class="sxs-lookup"><span data-stu-id="d2fa9-104">To correct this error</span></span>  
  
1. <span data-ttu-id="d2fa9-105">Consulte la documentación de la aplicación que creó el objeto para conocer las limitaciones en cuanto al uso de la automatización con esta clase de objeto.</span><span class="sxs-lookup"><span data-stu-id="d2fa9-105">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2. <span data-ttu-id="d2fa9-106">Si cambió un proyecto de .dll a .exe o a la inversa, deberá eliminar manualmente el registro del antiguo .dll o .exe.</span><span class="sxs-lookup"><span data-stu-id="d2fa9-106">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2fa9-107">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d2fa9-107">See also</span></span>

- [<span data-ttu-id="d2fa9-108">Tipos de error</span><span class="sxs-lookup"><span data-stu-id="d2fa9-108">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="d2fa9-109">Hable con nosotros</span><span class="sxs-lookup"><span data-stu-id="d2fa9-109">Talk to Us</span></span>](/visualstudio/ide/feedback-options)

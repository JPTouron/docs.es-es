---
title: Proteger los datos de estado
description: Declare los datos de estado como variables privadas o internas para limitar el acceso a ellos. Todavía se puede tener acceso a estos datos a través de la reflexión, la serialización y la depuración.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: 73bd0ace28e5b9661cc86d6749ceef9aa4c9ac92
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557130"
---
# <a name="securing-state-data"></a><span data-ttu-id="57ffb-104">Proteger los datos de estado</span><span class="sxs-lookup"><span data-stu-id="57ffb-104">Securing State Data</span></span>

<span data-ttu-id="57ffb-105">Las aplicaciones que administran datos confidenciales o realizan cualquier tipo de decisiones de seguridad necesitan mantener los datos bajo control y no pueden permitir que otro código potencialmente malintencionado acceda directamente a los datos.</span><span class="sxs-lookup"><span data-stu-id="57ffb-105">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="57ffb-106">La mejor manera de proteger los datos en memoria es declarar los datos como variables privadas o internas (con el ámbito limitado al mismo ensamblado).</span><span class="sxs-lookup"><span data-stu-id="57ffb-106">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="57ffb-107">Sin embargo, incluso estos datos están sujetos a acceso, por lo que debe tenerse en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="57ffb-107">However, even this data is subject to access you should be aware of:</span></span>  
  
- <span data-ttu-id="57ffb-108">Al usar mecanismos de reflexión, se puede obtener y establecer miembros privados en el código de plena confianza al que puede hacer referencia el objeto.</span><span class="sxs-lookup"><span data-stu-id="57ffb-108">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
- <span data-ttu-id="57ffb-109">Con la serialización, el código de plena confianza puede obtener y establecer eficazmente miembros privados si pueden acceder a los datos correspondientes en el formulario serializado del objeto.</span><span class="sxs-lookup"><span data-stu-id="57ffb-109">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
- <span data-ttu-id="57ffb-110">En la depuración, se pueden leer estos datos.</span><span class="sxs-lookup"><span data-stu-id="57ffb-110">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="57ffb-111">Asegúrese de que ninguno de sus métodos o propiedades expone estos valores de manera involuntaria.</span><span class="sxs-lookup"><span data-stu-id="57ffb-111">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ffb-112">Consulte también</span><span class="sxs-lookup"><span data-stu-id="57ffb-112">See also</span></span>

- [<span data-ttu-id="57ffb-113">Instrucciones de codificación segura</span><span class="sxs-lookup"><span data-stu-id="57ffb-113">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
- [<span data-ttu-id="57ffb-114">Seguridad de ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="57ffb-114">ASP.NET Core Security</span></span>](/aspnet/core/security/)

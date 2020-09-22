---
title: My.Response (Objeto)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 53e8012e762c46e6efbd8e9d2191aa62d58aa42b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870041"
---
# <a name="myresponse-object"></a><span data-ttu-id="e30ed-102">My.Response (Objeto)</span><span class="sxs-lookup"><span data-stu-id="e30ed-102">My.Response Object</span></span>

<span data-ttu-id="e30ed-103">Obtiene el <xref:System.Web.HttpResponse> objeto asociado a <xref:System.Web.UI.Page> .</span><span class="sxs-lookup"><span data-stu-id="e30ed-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="e30ed-104">Este objeto permite enviar datos de respuesta HTTP a un cliente y contiene información sobre esa respuesta.</span><span class="sxs-lookup"><span data-stu-id="e30ed-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e30ed-105">Comentarios</span><span class="sxs-lookup"><span data-stu-id="e30ed-105">Remarks</span></span>  

 <span data-ttu-id="e30ed-106">El `My.Response` objeto contiene el <xref:System.Web.HttpResponse> objeto actual asociado a la página.</span><span class="sxs-lookup"><span data-stu-id="e30ed-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="e30ed-107">El `My.Response` objeto solo está disponible para las aplicaciones de ASP.net.</span><span class="sxs-lookup"><span data-stu-id="e30ed-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e30ed-108">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e30ed-108">Example</span></span>  

 <span data-ttu-id="e30ed-109">En el ejemplo siguiente se obtiene la colección de encabezados del `My.Request` objeto y se usa el `My.Response` objeto para escribirla en la página ASP.net.</span><span class="sxs-lookup"><span data-stu-id="e30ed-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e30ed-110">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e30ed-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="e30ed-111">My.Request (objeto)</span><span class="sxs-lookup"><span data-stu-id="e30ed-111">My.Request Object</span></span>](my-request-object.md)

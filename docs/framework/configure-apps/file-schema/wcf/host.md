---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: b764bc21e9c4555b39c3d096212b6e6bcabb62ff
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855216"
---
# \<host>
<span data-ttu-id="7be44-101">Especifica los valores para un host de servicio.</span><span class="sxs-lookup"><span data-stu-id="7be44-101">Specifies settings for a service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**  
  
## <a name="syntax"></a><span data-ttu-id="7be44-102">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7be44-102">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="7be44-103">Tipo</span><span class="sxs-lookup"><span data-stu-id="7be44-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7be44-104">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="7be44-104">Attributes and Elements</span></span>  
 <span data-ttu-id="7be44-105">En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.</span><span class="sxs-lookup"><span data-stu-id="7be44-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7be44-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="7be44-106">Attributes</span></span>  
 <span data-ttu-id="7be44-107">Ninguno.</span><span class="sxs-lookup"><span data-stu-id="7be44-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7be44-108">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="7be44-108">Child Elements</span></span>  
  
|<span data-ttu-id="7be44-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="7be44-109">Element</span></span>|<span data-ttu-id="7be44-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="7be44-110">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="7be44-111">Una colección de elementos `baseAddress` que especifica las direcciones base utilizada por el host del servicio.</span><span class="sxs-lookup"><span data-stu-id="7be44-111">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[\<timeOuts>](timeouts.md)|<span data-ttu-id="7be44-112">Un elemento de configuración que especifica el intervalo de tiempo permitido para que el host del servicio abra o cierre.</span><span class="sxs-lookup"><span data-stu-id="7be44-112">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7be44-113">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="7be44-113">Parent Elements</span></span>  
  
|<span data-ttu-id="7be44-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="7be44-114">Element</span></span>|<span data-ttu-id="7be44-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="7be44-115">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="7be44-116">Especifica la configuración de un servicio de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7be44-116">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7be44-117">Consulte también</span><span class="sxs-lookup"><span data-stu-id="7be44-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="7be44-118">Hospedar aplicaciones de WPF</span><span class="sxs-lookup"><span data-stu-id="7be44-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)

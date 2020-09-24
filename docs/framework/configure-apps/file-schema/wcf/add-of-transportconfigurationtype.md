---
title: <add> de <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 9bef44ed39ee892080342058206f779b38fb460d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151160"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="50114-102">\<add> de \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="50114-102">\<add> of \<transportConfigurationType></span></span>

<span data-ttu-id="50114-103">Este elemento es una par clave-valor, que identifica el tipo de un transporte determinado.</span><span class="sxs-lookup"><span data-stu-id="50114-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="50114-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="50114-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50114-105">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="50114-105">Attributes and Elements</span></span>  

 <span data-ttu-id="50114-106">En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.</span><span class="sxs-lookup"><span data-stu-id="50114-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50114-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="50114-107">Attributes</span></span>  
  
|<span data-ttu-id="50114-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="50114-108">Attribute</span></span>|<span data-ttu-id="50114-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="50114-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="50114-110">name</span><span class="sxs-lookup"><span data-stu-id="50114-110">name</span></span>|<span data-ttu-id="50114-111">Atributo de cadena necesario.</span><span class="sxs-lookup"><span data-stu-id="50114-111">Required String attribute.</span></span><br /><br /> <span data-ttu-id="50114-112">Contiene una clave definida por el usuario que identifica de forma única el tipo de transporte.</span><span class="sxs-lookup"><span data-stu-id="50114-112">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="50114-113">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="50114-113">transportConfigurationType</span></span>|<span data-ttu-id="50114-114">Una cadena que contiene el tipo que implementa el transporte concreto.</span><span class="sxs-lookup"><span data-stu-id="50114-114">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50114-115">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="50114-115">Child Elements</span></span>  

 <span data-ttu-id="50114-116">None</span><span class="sxs-lookup"><span data-stu-id="50114-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="50114-117">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="50114-117">Parent Elements</span></span>  
  
|<span data-ttu-id="50114-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="50114-118">Element</span></span>|<span data-ttu-id="50114-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="50114-119">Description</span></span>|  
|-------------|-----------------|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="50114-120">Una colección de tipos que implementan el transporte concreto.</span><span class="sxs-lookup"><span data-stu-id="50114-120">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="50114-121">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="50114-121">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="50114-122">Vea también</span><span class="sxs-lookup"><span data-stu-id="50114-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="50114-123">Hospedar aplicaciones de WPF</span><span class="sxs-lookup"><span data-stu-id="50114-123">Hosting</span></span>](../../../wcf/feature-details/hosting.md)

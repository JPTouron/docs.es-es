---
title: <add>del <claimTypeRequirements> elemento
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: f6948052c62684faa734b592f5bdfc2e7827a07a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153105"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="1e87d-102">\<add>del \<claimTypeRequirements> elemento</span><span class="sxs-lookup"><span data-stu-id="1e87d-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="1e87d-103">Especifica los tipos de notificaciones necesarias y opcionales que se espera que aparezcan en una credencial aliada.</span><span class="sxs-lookup"><span data-stu-id="1e87d-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="1e87d-104">Por ejemplo, los servicios indican los requisitos en las credenciales de entrada, que deben poseer un cierto conjunto de tipos de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="1e87d-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**
  
## <a name="syntax"></a><span data-ttu-id="1e87d-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1e87d-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e87d-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="1e87d-106">Attributes and Elements</span></span>  
 <span data-ttu-id="1e87d-107">En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.</span><span class="sxs-lookup"><span data-stu-id="1e87d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e87d-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="1e87d-108">Attributes</span></span>  
  
|<span data-ttu-id="1e87d-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="1e87d-109">Attribute</span></span>|<span data-ttu-id="1e87d-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="1e87d-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1e87d-111">claimType</span><span class="sxs-lookup"><span data-stu-id="1e87d-111">claimType</span></span>|<span data-ttu-id="1e87d-112">URI que define el tipo de una notificación.</span><span class="sxs-lookup"><span data-stu-id="1e87d-112">A URI that defines the type of a claim.</span></span> <span data-ttu-id="1e87d-113">Por ejemplo, para comprar un producto de un sitio web, el usuario debe presentar una tarjeta de crédito válida con límite de crédito suficiente.</span><span class="sxs-lookup"><span data-stu-id="1e87d-113">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="1e87d-114">El tipo de notificación sería el URI de la tarjeta de crédito.</span><span class="sxs-lookup"><span data-stu-id="1e87d-114">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="1e87d-115">isOptional</span><span class="sxs-lookup"><span data-stu-id="1e87d-115">isOptional</span></span>|<span data-ttu-id="1e87d-116">Valor de tipo booleano que especifica si se trata de una notificación opcional.</span><span class="sxs-lookup"><span data-stu-id="1e87d-116">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="1e87d-117">Establezca este atributo en `false` si se trata de una notificación necesaria.</span><span class="sxs-lookup"><span data-stu-id="1e87d-117">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="1e87d-118">Puede usar este atributo cuando el servicio pregunte para obtener alguna información, pero no lo requiere.</span><span class="sxs-lookup"><span data-stu-id="1e87d-118">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="1e87d-119">Por ejemplo, si necesita que el usuario escriba su nombre, Apellido y dirección, pero decide que el número de teléfono es opcional.</span><span class="sxs-lookup"><span data-stu-id="1e87d-119">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e87d-120">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="1e87d-120">Child Elements</span></span>  
 <span data-ttu-id="1e87d-121">Ninguno.</span><span class="sxs-lookup"><span data-stu-id="1e87d-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e87d-122">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="1e87d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1e87d-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="1e87d-123">Element</span></span>|<span data-ttu-id="1e87d-124">Descripción</span><span class="sxs-lookup"><span data-stu-id="1e87d-124">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="1e87d-125">Especifica una colección de tipos de notificación requeridos.</span><span class="sxs-lookup"><span data-stu-id="1e87d-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="1e87d-126">Cada elemento es del tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="1e87d-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="1e87d-127">En un escenario aliado, los servicios indican los requisitos de las credenciales de entrada.</span><span class="sxs-lookup"><span data-stu-id="1e87d-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="1e87d-128">Por ejemplo, las credenciales de entrada deben poseer un determinado conjunto de tipos de notificación.</span><span class="sxs-lookup"><span data-stu-id="1e87d-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="1e87d-129">Cada elemento de la colección especifica los tipos de notificaciones necesarias y opcionales que se espera que aparezcan en una credencial aliada.</span><span class="sxs-lookup"><span data-stu-id="1e87d-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e87d-130">Comentarios</span><span class="sxs-lookup"><span data-stu-id="1e87d-130">Remarks</span></span>  
 <span data-ttu-id="1e87d-131">En un escenario aliado, los servicios indican los requisitos de las credenciales de entrada.</span><span class="sxs-lookup"><span data-stu-id="1e87d-131">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="1e87d-132">Por ejemplo, las credenciales de entrada deben poseer un determinado conjunto de tipos de notificación.</span><span class="sxs-lookup"><span data-stu-id="1e87d-132">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="1e87d-133">Este requisito se manifiesta en una directiva de seguridad.</span><span class="sxs-lookup"><span data-stu-id="1e87d-133">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="1e87d-134">Cuando un cliente solicita las credenciales de un servicio aliado (por ejemplo, CardSpace), coloca los requisitos en una solicitud del token (RequestSecurityToken) para que el servicio aliado pueda emitir las credenciales que satisfacen según los requisitos.</span><span class="sxs-lookup"><span data-stu-id="1e87d-134">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e87d-135">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1e87d-135">Example</span></span>  
 <span data-ttu-id="1e87d-136">La siguiente configuración agrega dos requisitos de tipo de notificación a un enlace de seguridad.</span><span class="sxs-lookup"><span data-stu-id="1e87d-136">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="1e87d-137">Consulte también</span><span class="sxs-lookup"><span data-stu-id="1e87d-137">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>

---
ms.openlocfilehash: 8cc4f2ba2923774ef4e4e6861a89a7797ca988e1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621378"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a><span data-ttu-id="641be-101">Cambios importantes en SignedXml y EncryptedXml</span><span class="sxs-lookup"><span data-stu-id="641be-101">SignedXml and EncryptedXml Breaking Changes</span></span>

#### <a name="details"></a><span data-ttu-id="641be-102">Detalles</span><span class="sxs-lookup"><span data-stu-id="641be-102">Details</span></span>

<span data-ttu-id="641be-103">En .NET Framework 4.6.2, las revisiones de seguridad de <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> y <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> generan otros comportamientos en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="641be-103">In .NET Framework 4.6.2, Security fixes in <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> and <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> lead to different run-time behaviors.</span></span> <span data-ttu-id="641be-104">Por ejemplo,</span><span class="sxs-lookup"><span data-stu-id="641be-104">For example,</span></span><ul><li><span data-ttu-id="641be-105">Si un documento tiene varios elementos con el mismo atributo <code>id</code> y una firma está destinada a uno de esos elementos como la raíz de la firma, el documento ahora se considerará no válido.</span><span class="sxs-lookup"><span data-stu-id="641be-105">If a document has multiple elements with the same <code>id</code> attribute and a signature targets one of those elements as the root of the signature, the document will now be considered invalid.</span></span></li><li><span data-ttu-id="641be-106">Los documentos con algoritmos de transformación de XPath no canónicos en las referencias ahora se consideran no válidos.</span><span class="sxs-lookup"><span data-stu-id="641be-106">Documents using non-canonical XPath transform algorithms in references are now considered invalid.</span></span></li><li><span data-ttu-id="641be-107">Los documentos con algoritmos de transformación de XSLT no canónicos en las referencias ahora se consideran no válidos.</span><span class="sxs-lookup"><span data-stu-id="641be-107">Documents using non-canonical XSLT transform algorithms in references are now consider invalid.</span></span></li><li><span data-ttu-id="641be-108">Los programas que usen firmas separadas de recurso externo no podrán hacerlo.</span><span class="sxs-lookup"><span data-stu-id="641be-108">Any program making use of external resource detached signatures will be unable to do so.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="641be-109">Sugerencia</span><span class="sxs-lookup"><span data-stu-id="641be-109">Suggestion</span></span>

<span data-ttu-id="641be-110">Es posible que los desarrolladores quieran revisar el uso de <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> y <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, así como los tipos derivados de <xref:System.Security.Cryptography.Xml.Transform>, ya que es posible que un receptor de documentos no pueda procesarlo.</span><span class="sxs-lookup"><span data-stu-id="641be-110">Developers might want to review the usage of <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> and <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, as well as types derived from <xref:System.Security.Cryptography.Xml.Transform> since a document receiver may not be able to process it.</span></span>

| <span data-ttu-id="641be-111">Nombre</span><span class="sxs-lookup"><span data-stu-id="641be-111">Name</span></span>    | <span data-ttu-id="641be-112">Valor</span><span class="sxs-lookup"><span data-stu-id="641be-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="641be-113">Ámbito</span><span class="sxs-lookup"><span data-stu-id="641be-113">Scope</span></span>   |<span data-ttu-id="641be-114">Secundaria</span><span class="sxs-lookup"><span data-stu-id="641be-114">Minor</span></span>|
|<span data-ttu-id="641be-115">Versión</span><span class="sxs-lookup"><span data-stu-id="641be-115">Version</span></span>|<span data-ttu-id="641be-116">4.6.2</span><span class="sxs-lookup"><span data-stu-id="641be-116">4.6.2</span></span>|
|<span data-ttu-id="641be-117">Tipo</span><span class="sxs-lookup"><span data-stu-id="641be-117">Type</span></span>|<span data-ttu-id="641be-118">Tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="641be-118">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="641be-119">API afectadas</span><span class="sxs-lookup"><span data-stu-id="641be-119">Affected APIs</span></span>

-<xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|

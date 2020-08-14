---
ms.openlocfilehash: e0cdcce9b8c7d591925b08635e3354dadaf22b7b
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556037"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>EnvelopedCms utiliza de forma predeterminada el cifrado AES-256

El algoritmo de cifrado simétrico predeterminado que usa `EnvelopedCms` ha cambiado de TripleDES a AES-256.

#### <a name="change-description"></a>Descripción del cambio

En versiones anteriores, cuando se usa <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> para cifrar datos sin especificar un algoritmo de cifrado simétrico a través de una sobrecarga de constructor, los datos se cifran con el algoritmo TripleDES/3DES/3DEA/DES3-EDE.

A partir de .NET Core 3.0 (a través de la versión 4.6.0 del paquete NuGet [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/)), el algoritmo predeterminado se ha cambiado a AES-256 para la modernización de algoritmos y para mejorar la seguridad de opciones predeterminadas. Si el certificado del destinatario de un mensaje tiene una clave pública Diffie-Hellman (no de cliente de empresa), es posible que se produzca un error <xref:System.Security.Cryptography.CryptographicException> en la operación de cifrado debido a limitaciones de la plataforma subyacente.

En el siguiente código de ejemplo, los datos se cifran con TripleDES si se ejecutan en .NET Core 2.2 o anterior. Si se ejecutan en .NET Core 3.0 o posterior, se cifran con AES-256.

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>Versión introducida

3.0

#### <a name="recommended-action"></a>Acción recomendada

Si el cambio le afecta negativamente, puede restaurar el cifrado TripleDES especificando explícitamente el identificador del algoritmo de cifrado en un constructor de <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> que incluya un parámetro del tipo <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, por ejemplo:

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a>Categoría

Criptografía

#### <a name="affected-apis"></a>API afectadas

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->

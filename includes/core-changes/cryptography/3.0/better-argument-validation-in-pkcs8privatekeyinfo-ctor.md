---
ms.openlocfilehash: 32030698c12de87daef5e1d8851a0f55ec36d688
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721095"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="4e325-101">Mejor validación de argumentos en el constructor de Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="4e325-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="4e325-102">A partir de la versión preliminar 9 de .NET Core 3.0, el constructor de `Pkcs8PrivateKeyInfo` valida el parámetro `algorithmParameters`como un único valor codificado en BER.</span><span class="sxs-lookup"><span data-stu-id="4e325-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4e325-103">Descripción del cambio</span><span class="sxs-lookup"><span data-stu-id="4e325-103">Change description</span></span>

<span data-ttu-id="4e325-104">Antes de la versión preliminar 9 de .NET Core 3.0, el [constructor `Pkcs8PrivateKeyInfo`](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) no validó el argumento `algorithmParameters`.</span><span class="sxs-lookup"><span data-stu-id="4e325-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="4e325-105">Cuando este argumento represente un valor no válido, el constructor se realizará correctamente, pero una llamada a cualquiera de los métodos <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A> o <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> produciría una <xref:System.ArgumentException>con un argumento que no aceptasen (`preEncodedValue`) o una <xref:System.Security.Cryptography.CryptographicException>.</span><span class="sxs-lookup"><span data-stu-id="4e325-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="4e325-106">Si se ejecuta con una versión preliminar de .NET Core 3.0 anterior a la 9, el código siguiente solo produce una excepción cuando se llama al método <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>:</span><span class="sxs-lookup"><span data-stu-id="4e325-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="4e325-107">A partir de la versión preliminar 9 de .NET Core 3.0, el argumento se valida en el constructor y un valor no válido se traduce en que el método produce una <xref:System.Security.Cryptography.CryptographicException>.</span><span class="sxs-lookup"><span data-stu-id="4e325-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="4e325-108">Este cambio acerca la excepción al origen del error de datos.</span><span class="sxs-lookup"><span data-stu-id="4e325-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="4e325-109">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4e325-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="4e325-110">Versión introducida</span><span class="sxs-lookup"><span data-stu-id="4e325-110">Version introduced</span></span>

<span data-ttu-id="4e325-111">3.0 (versión preliminar 9)</span><span class="sxs-lookup"><span data-stu-id="4e325-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4e325-112">Acción recomendada</span><span class="sxs-lookup"><span data-stu-id="4e325-112">Recommended action</span></span>

<span data-ttu-id="4e325-113">Asegúrese de que solo se especifiquen valores `algorithmParameters` válidos o, si se quiere un control de excepciones, de que se realicen llamadas a la prueba del constructor de `Pkcs8PrivateKeyInfo` tanto para <xref:System.ArgumentException> como para <xref:System.Security.Cryptography.CryptographicException>.</span><span class="sxs-lookup"><span data-stu-id="4e325-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

#### <a name="category"></a><span data-ttu-id="4e325-114">Categoría</span><span class="sxs-lookup"><span data-stu-id="4e325-114">Category</span></span>

<span data-ttu-id="4e325-115">Criptografía</span><span class="sxs-lookup"><span data-stu-id="4e325-115">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4e325-116">API afectadas</span><span class="sxs-lookup"><span data-stu-id="4e325-116">Affected APIs</span></span>

- <span data-ttu-id="4e325-117">[Constructor de Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="4e325-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->

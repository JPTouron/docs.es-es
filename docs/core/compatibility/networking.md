---
title: Cambios importantes en las redes
description: Enumera los cambios importantes en las redes en .NET Core.
ms.date: 05/05/2020
ms.openlocfilehash: fa5807c882c3bc6f66e8a27361ccc14254e90b3e
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465524"
---
# <a name="networking-breaking-changes"></a>Cambios importantes en las redes

En esta página se documentan los siguientes cambios importantes:

| Cambio importante | Versión introducida |
| - | - |
| [WinHttpHandler quitado del entorno de ejecución de .NET](#winhttphandler-removed-from-net-runtime) | 5.0 |
| [MulticastOption.Group no acepta un valor NULL](#multicastoptiongroup-doesnt-accept-a-null-value) | 5.0 |
| [La administración de rutas de acceso de cookies ahora se ajusta a RFC 6265](#cookie-path-handling-now-conforms-to-rfc-6265) | 5.0 |
| [El valor predeterminado de HttpRequestMessage.Version ha cambiado a 1.1](#default-value-of-httprequestmessageversion-changed-to-11) | 3.0 |
| [WebClient.CancelAsync no siempre se cancela inmediatamente](#webclientcancelasync-doesnt-always-cancel-immediately) | 2.0 |

## <a name="net-50"></a>.NET 5.0

[!INCLUDE [winhttphandler-removed-from-runtime](../../../includes/core-changes/networking/5.0/winhttphandler-removed-from-runtime.md)]

***

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

[!INCLUDE [cookie-path-conforms-to-rfc6265](../../../includes/core-changes/networking/5.0/cookie-path-conforms-to-rfc6265.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a>.NET Core 2.0

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***

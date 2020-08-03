---
title: Serialización de caracteres de control con DataContractJsonSerializer
description: Obtenga información sobre la forma en que la serialización de caracteres de control ha cambiado para ser conforme con ECMAScript V6 y V8 en .NET Framework 4.7.
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: a317884da014097a7a60aef2cef4ec146ccb04f7
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475390"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Mitigación: serialización de caracteres de control con DataContractJsonSerializer

A partir de NET Framework 4.7, ha cambiado la forma en la que se serializan los caracteres de control con <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> para que sean conformes con ECMAScript V6 y V8.

## <a name="impact"></a>Impacto

En .NET Framework 4.6.2 y versiones anteriores, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> no serializaba algunos caracteres de control especiales, como `\b`, `\f` y `\t`, de una forma que fuera compatible con los estándares ECMAScript V6 y V8.

Para las aplicaciones destinadas a versiones de .NET Framework a partir de .NET Framework 4.7, la serialización de estos caracteres de control es compatible con ECMAScript V6 y V8. Afecta a las siguientes API:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a>Mitigación

Para las aplicaciones destinadas a versiones de .NET Framework a partir de .NET Framework 4.7, este comportamiento está habilitado de forma predeterminada.

Si no desea este compartimiento, puede rechazar esta característica agregando la siguiente línea a la sección `<runtime>` del archivo app.config o web.config:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a>Vea también

- [Compatibilidad de aplicaciones](application-compatibility.md)

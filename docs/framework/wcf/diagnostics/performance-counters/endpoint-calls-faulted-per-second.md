---
title: 'punto de conexión: Errores en llamadas por segundo'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: 4be8f1b527ea72601b14173813f4f24e44685ce0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544172"
---
# <a name="endpoint-calls-faulted-per-second"></a>punto de conexión: Errores en llamadas por segundo
Nombre del contador: Errores de llamadas por segundo.  
  
## <a name="description"></a>Descripción  
 Número de llamadas que han devuelto errores a este punto de conexión en un segundo.  
  
 Este contador es de tipo de contador de rendimiento [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cuyo valor se calcula mediante la siguiente fórmula.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 En las aplicaciones Windows Communication Foundation (WCF), los métodos de servicio comunican la información de errores de procesamiento mediante mensajes de error de SOAP. Los errores SOAP son tipos de mensaje que se incluyen en los metadatos de una operación del servicio y, por consiguiente, crean un contrato de error que los clientes pueden utilizar para que su ejecución sea más sólida o interactiva. Dado que los errores SOAP se muestran a los clientes en formato XML, son sumamente interoperativos.  
  
## <a name="see-also"></a>Vea también

- [Especificación y administración de errores en contratos y servicios](../../specifying-and-handling-faults-in-contracts-and-services.md)

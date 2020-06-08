---
title: 'Cómo: Implementar las particiones dinámicas'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
ms.openlocfilehash: 197e71cf4f00c98891e58e5f72974c0ec407e6ce
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288451"
---
# <a name="how-to-implement-dynamic-partitions"></a>Cómo: Implementar las particiones dinámicas

En el ejemplo siguiente se muestra cómo implementar una clase <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> personalizada que implementa la partición dinámica y que puede usarse desde determinadas sobrecargas <xref:System.Threading.Tasks.Parallel.ForEach%2A> y desde PLINQ.  
  
## <a name="example"></a>Ejemplo

Cada vez que se llama a una partición <xref:System.Collections.IEnumerator.MoveNext%2A> en el enumerador, este proporciona la partición con un elemento de lista. En el caso de PLINQ y <xref:System.Threading.Tasks.Parallel.ForEach%2A>, la partición es una instancia <xref:System.Threading.Tasks.Task>. Dado que las solicitudes se producen simultáneamente en varios subprocesos, se sincroniza el acceso al índice actual.  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

Este es un ejemplo de creación de particiones por fragmentos, donde cada fragmento consta de un elemento. Proporcionando más elementos a la vez, podría reducir la contención sobre el bloqueo y teóricamente lograr un rendimiento más rápido. Sin embargo, en algún momento, los fragmentos más grandes podrían requerir lógica de equilibrio de carga adicional con el fin de mantener todos los subprocesos ocupados hasta que se completa todo el trabajo.  
  
## <a name="see-also"></a>Vea también

* [Particionadores personalizados para PLINQ y TPL](custom-partitioners-for-plinq-and-tpl.md)
* [Implementar un particionador para particionamiento estático](how-to-implement-a-partitioner-for-static-partitioning.md)

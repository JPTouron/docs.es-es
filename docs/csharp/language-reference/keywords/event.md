---
description: 'event: Referencia de C#'
title: 'event: Referencia de C#'
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: 5e75fec12390cb694126c5bec684c40caa378915
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139104"
---
# <a name="event-c-reference"></a>event (Referencia de C#)

La palabra clave `event` se usa para declarar un evento en una clase de publicador.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo declarar y generar un evento que usa <xref:System.EventHandler> como el tipo de delegado subyacente. Para obtener el código de ejemplo completo que también muestra cómo usar el tipo delegado <xref:System.EventHandler%601> genérico y cómo suscribirse a un evento y crear un método de controlador de evento, consulte [Procedimiento Publicar eventos que cumplan las directrices de .NET Framework](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).

[!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]

Los eventos son un tipo especial de delegado de multidifusión que solo se pueden invocar desde la clase o el struct en la que se declaran (la clase de publicador). Si otras clases o structs se suscriben al evento, se llamará a sus métodos de controlador de eventos cuando la clase de publicador genera el evento. Para más información y ejemplos de código, vea [Eventos](../../programming-guide/events/index.md) y [Delegados](../../programming-guide/delegates/index.md).

Las constantes pueden marcarse como [public](./public.md), [private](./private.md), [protected](./protected.md), [internal](./internal.md), [protected internal](./protected-internal.md) o [private protected](./private-protected.md). Estos modificadores de acceso definen cómo los usuarios de la clase pueden obtener acceso al evento. Para obtener más información, consulte [Modificadores de acceso](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="keywords-and-events"></a>Palabras clave y eventos

Las palabras clave siguientes se aplican a eventos.

|Palabra clave|Descripción|Para obtener más información|
|-------------|-----------------|--------------------------|
|[static](./static.md)|Hace que el evento esté disponible para los llamadores en cualquier momento, aunque no exista ninguna instancia de la clase.|[Clases estáticas y sus miembros](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|
|[virtual](./virtual.md)|Permite que las clases derivadas invaliden el comportamiento de eventos mediante la palabra clave [override](./override.md).|[Herencia](../../programming-guide/classes-and-structs/inheritance.md)|
|[sealed](./sealed.md)|Especifica que ya no es virtual para las clases derivadas.||
|[abstract](./abstract.md)|El compilador no generará los bloques de descriptor de acceso de eventos `add` y `remove`, y por tanto, las clases deben proporcionar su propia implementación.||

Un evento puede declararse como evento estático mediante la palabra clave [static](./static.md). Esto hace que el evento esté disponible para los llamadores en cualquier momento, aunque no exista ninguna instancia de la clase. Para más información, vea [Clases estáticas y sus miembros](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

Un evento puede marcarse como virtual mediante la palabra clave [virtual](./virtual.md). Esto permite que las clases derivadas invaliden el comportamiento de eventos mediante la palabra clave [override](./override.md). Para obtener más información, vea [Herencia](../../programming-guide/classes-and-structs/inheritance.md). Un evento que reemplaza un evento virtual también puede ser [sealed](./sealed.md), que especifica que ya no es virtual para las clases derivadas. Por último, se puede declarar un evento como [abstract](./abstract.md), lo que significa que el compilador no generará los bloques de descriptor de acceso de eventos `add` y `remove`. Por tanto, las clases derivadas deben proporcionar una implementación propia.

## <a name="c-language-specification"></a>Especificación del lenguaje C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Vea también

- [Referencia de C#](../index.md)
- [Guía de programación de C#](../../programming-guide/index.md)
- [Palabras clave de C#](./index.md)
- [add](./add.md)
- [remove](./remove.md)
- [Modificadores](index.md)
- [Procedimiento para combinar delegados (delegados de multidifusión)](../../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)

---
title: Reflexión (C#)
description: La reflexión proporciona objetos que describen los ensamblados, módulos y tipos en C#. Si el código incluye atributos, la reflexión le permite acceder a ellos.
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 4d4f4c082dd2d58e212bae53524e5dd4fd06fb75
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302807"
---
# <a name="reflection-c"></a>Reflexión (C#)

La reflexión proporciona objetos (de tipo <xref:System.Type>) que describen los ensamblados, módulos y tipos. Puede usar la reflexión para crear dinámicamente una instancia de un tipo, enlazar el tipo a un objeto existente u obtener el tipo desde un objeto existente e invocar sus métodos, o acceder a sus campos y propiedades. Si usa atributos en el código, la reflexión le permite acceder a ellos. Para obtener más información, consulte [Attributes](../../../standard/attributes/index.md) (Atributos).

Este es un ejemplo simple de reflexión que usa el método <xref:System.Object.GetType>, heredado por todos los tipos de la clase base `Object`, para obtener el tipo de una variable:

> [!NOTE]
> Asegúrese de agregar `using System;` y `using System.Reflection;` en la parte superior del archivo de *.cs*.

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

El resultado es `System.Int32`.

En el ejemplo siguiente se usa la reflexión para obtener el nombre completo del ensamblado cargado.

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

El resultado es `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.

> [!NOTE]
> Las palabras clave de C# `protected` y `internal` no tienen ningún significado en IL y no se usan en las API de reflexión. Los términos correspondientes en IL son *Family* y *Assembly*. Para identificar un método `internal` con la reflexión, use la propiedad <xref:System.Reflection.MethodBase.IsAssembly%2A>. Para identificar un método `protected internal`, use <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.

## <a name="reflection-overview"></a>Información general de la reflexión

La reflexión resulta útil en las siguientes situaciones:

- Cuando tenga que acceder a atributos en los metadatos del programa. Para obtener más información, consulte [Recuperar información almacenada en atributos](../../../standard/attributes/retrieving-information-stored-in-attributes.md).
- Para examinar y crear instancias de tipos en un ensamblado.
- Para generar nuevos tipos en tiempo de ejecución. Usar clases en <xref:System.Reflection.Emit>.
- Para llevar a cabo métodos de acceso de enlace en tiempo de ejecución en tipos creados en tiempo de ejecución. Consulte el tema [Cargar y utilizar tipos dinámicamente](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).

## <a name="related-sections"></a>Secciones relacionadas

Para obtener más información:

- [Reflexión](../../../framework/reflection-and-codedom/reflection.md)
- [Ver información tipos](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [Reflexión y tipos genéricos](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [Recuperar la información almacenada en atributos](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a>Consulte también

- [Guía de programación de C#](../index.md)
- [Ensamblados de .NET](../../../standard/assembly/index.md)

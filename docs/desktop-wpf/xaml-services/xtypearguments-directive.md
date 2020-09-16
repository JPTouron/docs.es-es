---
title: x:TypeArguments (Directiva)
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 430ab65af52282ccb1d429cd2523efe213f13609
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543556"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments (Directiva)

Pasa los argumentos de tipo restrictivos de un genérico al constructor del tipo genérico.

## <a name="xaml-attribute-usage"></a>Uso de atributos XAML

```xaml
<object x:TypeArguments="typeString" .../>
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|`object`|Una declaración de elemento de objeto de un tipo XAML, que está respaldada por un tipo genérico de CLR. Si `object` hace referencia a un tipo XAML que no es del espacio de nombres XAML predeterminado, `object` requiere un prefijo para indicar el espacio de nombres XAML donde `object` existe.|
|`typeString`|Cadena que declara uno o más nombres de tipo XAML como cadenas, lo que proporciona los argumentos de tipo para el tipo genérico de CLR. Vea la sección Comentarios para obtener más notas sobre la sintaxis.|

## <a name="remarks"></a>Comentarios

En la mayoría de los casos, los tipos XAML que se usan como un elemento de información en una `typeString` cadena tienen el prefijo. Los tipos típicos de restricciones genéricas de CLR (por ejemplo, <xref:System.Int32> y <xref:System.String> ) proceden de las bibliotecas de clases base de CLR. Estas bibliotecas no se asignan a los espacios de nombres XAML predeterminados específicos del marco y, por lo tanto, requieren una asignación de prefijo para el uso de XAML.

Puede especificar más de un nombre de tipo XAML mediante un delimitador de coma.

Si las restricciones genéricas usan tipos genéricos, los argumentos de tipo de restricción anidados pueden estar incluidos entre paréntesis ().

Tenga en cuenta que esta definición de `x:TypeArguments` es específica de los servicios XAML de .net y usa la copia de seguridad de CLR. Puede encontrar una definición de nivel de lenguaje en la [ \[ sección MS-XAML \] 5.3.11](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="usage-examples"></a>Ejemplos de uso

En estos ejemplos, suponga que se declaran las siguientes definiciones de espacio de nombres XAML:

```xaml
xmlns:sys="clr-namespace:System;assembly=mscorlib"
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"
```

### <a name="liststring"></a>List\<String>

`<scg:List x:TypeArguments="sys:String" ...>` crea una instancia de un nuevo <xref:System.Collections.Generic.List%601> con un <xref:System.String> argumento de tipo.

### <a name="dictionarystringstring"></a>Diccionario\<String,String>

`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` crea una instancia de un nuevo <xref:System.Collections.Generic.Dictionary%602> con dos <xref:System.String> argumentos de tipo.

### <a name="queuekeyvaluepairstringstring"></a><de la cola KeyValuePair\<String,String>>

`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` crea una instancia de un nuevo <xref:System.Collections.Generic.Queue%601> que tiene una restricción de <xref:System.Collections.Generic.KeyValuePair%602> con los argumentos de tipo de restricción interna <xref:System.String> y <xref:System.String> .

## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 y usos de XAML genéricos de WPF

Para el uso de XAML 2006 y el XAML que se usa para las aplicaciones de WPF, existen las siguientes restricciones para los `x:TypeArguments` usos de tipos genéricos de XAML en general:

- Solo el elemento raíz de un archivo XAML puede admitir un uso de XAML genérico que hace referencia a un tipo genérico.

- El elemento raíz debe asignarse a un tipo genérico con al menos un argumento de tipo. Un ejemplo es <xref:System.Windows.Navigation.PageFunction%601>. Las funciones de página son el escenario principal para la compatibilidad con el uso genérico de XAML en WPF.

- El elemento raíz del elemento de objeto XAML para el genérico también debe declarar una clase parcial mediante `x:Class` . Esto es así incluso si se define una acción de compilación de WPF.

- `x:TypeArguments` no se puede hacer referencia a restricciones genéricas anidadas.

## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 o XAML 2006 sin dependencia de WPF 3,0 o WPF 3,5

En los servicios XAML de .NET para XAML 2006 o XAML 2009, se relajan las restricciones relacionadas con WPF en el uso de XAML genérico. Puede crear instancias de un elemento de objeto genérico en cualquier posición en el marcado XAML que admitan el sistema de tipos de respaldo y el modelo de objetos.

Si usa XAML 2009 en lugar de asignar los tipos base de CLR para obtener tipos XAML para los primitivos del lenguaje común, puede usar [tipos integrados para primitivas del lenguaje XAML comunes](types-for-primitives.md) como elementos de información en un `typeString` . Por ejemplo, podría declarar lo siguiente (no se muestran las asignaciones de prefijo, pero x es el espacio de nombres XAML del lenguaje XAML para XAML 2009):

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

En WPF y cuando el destino es .NET Framework 4 o .NET Core 3,0 (o posterior), puede usar las características de XAML 2009 junto con `x:TypeArguments` pero solo para XAML dinámico (XAML que no está compilado por marcado). XAML compilado por marcado para WPF y el formulario BAML de XAML no admiten de momento las palabras clave y características de XAML 2009. Si necesita marcado compilar el código XAML, debe operar con las restricciones que se indican en la sección [xaml 2006 y los usos de XAML genéricos de WPF](#xaml-2006-and-wpf-generic-xaml-usages) . BAML solo se admite en .NET Framework.

## <a name="see-also"></a>Vea también

- [x:Class (Directiva)](xclass-directive.md)
- [x:Type (Extensión de marcado)](xtype-markup-extension.md)
- [Tipos integrados para primitivas comunes en el lenguaje XAML](types-for-primitives.md)
- [Elementos genéricos en XAML](generics.md)

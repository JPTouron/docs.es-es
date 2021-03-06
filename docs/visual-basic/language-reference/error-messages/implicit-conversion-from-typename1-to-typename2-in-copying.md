---
title: Conversión implícita de '<typename1>' a '<typename2>' al copiar de nuevo el valor del parámetro 'ByRef' '<parametername>' en el argumento correspondiente
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: fced95fe24d42d4af2118706bcaf3337429fea91
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873988"
---
# <a name="implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a>Conversión implícita de '\<typename1>' a '\<typename2>' al copiar de nuevo el valor del parámetro 'ByRef' '\<parametername>' en el argumento correspondiente

Se llama a un procedimiento con un argumento [ByRef](../modifiers/byref.md) de un tipo diferente al de su parámetro correspondiente.  
  
 Si se pasa un argumento `ByRef` , Visual Basic a veces copia el valor del argumento en una variable local en el procedimiento en lugar de pasar una referencia. En tal caso, cuando el procedimiento vuelve, Visual Basic debe copiar de nuevo el valor de la variable local en el argumento del código de llamada.  
  
 Si un valor de argumento `ByRef` se copia en el procedimiento y el argumento y el parámetro son del mismo tipo, no es necesario realizar ninguna conversión. Pero si los tipos son diferentes, Visual Basic debe convertir en ambas direcciones. Dado que no se puede usar `CType` ni ninguna de las otras palabras clave de conversión en un argumento de procedimiento o parámetro, esta conversión siempre es implícita.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identificador de error:** BC41999  
  
## <a name="to-correct-this-error"></a>Para corregir este error  
  
- Si es posible, use un argumento de llamada del mismo tipo que el parámetro de procedimiento, por lo que Visual Basic no necesita realizar ninguna conversión.  
  
- Si necesita llamar al procedimiento con un argumento de tipo diferente del tipo de parámetro pero no es necesario devolver un valor al argumento de llamada, defina el parámetro para que sea [ByVal](../modifiers/byval.md) en lugar de `ByRef`.  
  
## <a name="see-also"></a>Consulte también

- [Procedimientos](../../programming-guide/language-features/procedures/index.md)
- [Argumentos y parámetros de procedimiento](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Pasar argumentos por valor y por referencia](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [Conversiones implícitas y explícitas](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)

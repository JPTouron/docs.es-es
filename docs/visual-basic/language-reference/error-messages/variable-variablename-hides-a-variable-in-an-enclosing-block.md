---
title: La variable '<variablename>' oculta una variable en un bloque de inclusión
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 04538be3431fb06518051db4378e986ea5711219
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875060"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>La variable '\<variablename>' oculta una variable en un bloque de inclusión

Una variable encerrada en un bloque tiene el mismo nombre que otra variable local.  
  
 **Identificador de error:** BC30616  
  
## <a name="to-correct-this-error"></a>Para corregir este error  
  
- Cambie el nombre de la variable en el bloque incluido para que no sea el mismo que cualquier otra variable local. Por ejemplo:  
  
    ```vb  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- Una causa común de este error es el uso de `Catch e As Exception` dentro de un controlador de eventos. En este caso, asigne un nombre `Catch` a la variable de bloque `ex` en lugar de `e` .  
  
- Otro origen común de este error es un intento de obtener acceso a una variable local declarada dentro de un `Try` bloque en un `Catch` bloque independiente. Para corregir esto, declare la variable fuera de la `Try...Catch...Finally` estructura.  
  
## <a name="see-also"></a>Consulte también

- [Instrucción Try...Catch...Finally](../statements/try-catch-finally-statement.md)
- [Declaración de variable](../../programming-guide/language-features/variables/variable-declaration.md)

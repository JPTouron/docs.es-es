---
description: -recurse (Opciones del compilador de C#)
title: -recurse (Opciones del compilador de C#)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: 3edd7e23358bc0569dae6204d519209df1ade290
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124830"
---
# <a name="-recurse-c-compiler-options"></a>-recurse (Opciones del compilador de C#)
La opción -recurse permite compilar archivos de código fuente de todos los directorios secundarios del directorio especificado (dir) o del directorio del proyecto.  
  
## <a name="syntax"></a>Sintaxis  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Argumentos  
 `dir` (opcional)  
 El directorio en el que quiere que comience la búsqueda. Si no se especifica, la búsqueda comienza en el directorio del proyecto.  
  
 `file`  
 Los archivos que buscará. Se admiten los caracteres comodín.  
  
## <a name="remarks"></a>Comentarios  
 La opción **-recurse** permite compilar archivos de código fuente de todos los directorios secundarios del directorio especificado (`dir`) o del directorio del proyecto.  
  
 Puede usar caracteres comodín en un nombre de archivo para compilar todos los archivos coincidentes en el directorio del proyecto sin usar **-recurse**.  
  
 Esta opción del compilador no está disponible en Visual Studio y no se puede cambiar mediante programación.  
  
## <a name="example"></a>Ejemplo  
 Compila todos los archivos de C# en el directorio actual:  
  
```console  
csc *.cs  
```  
  
 Compila todos los archivos de C# en el directorio dir1\dir2 y los directorios que haya por debajo y genera dir2.dll:  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Vea también

- [Opciones del compilador de C#](./index.md)
- [Administrar propiedades de soluciones y proyectos](/visualstudio/ide/managing-project-and-solution-properties)

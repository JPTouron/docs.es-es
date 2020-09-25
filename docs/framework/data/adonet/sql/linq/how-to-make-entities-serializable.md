---
title: Procedimiento para serializar entidades
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: f4528cab21ac678f5d06717d0ce6e7ff7e77d3e4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203506"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="05235-102">Procedimiento para serializar entidades</span><span class="sxs-lookup"><span data-stu-id="05235-102">How to: Make Entities Serializable</span></span>

<span data-ttu-id="05235-103">Puede hacer que las entidades sean serializables al generar el código.</span><span class="sxs-lookup"><span data-stu-id="05235-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="05235-104">Las clases de entidad se decoran con el atributo <xref:System.Runtime.Serialization.DataContractAttribute> y las columnas con el atributo <xref:System.Runtime.Serialization.DataMemberAttribute>.</span><span class="sxs-lookup"><span data-stu-id="05235-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="05235-105">Los desarrolladores que usan Visual Studio pueden usar el Object Relational Designer para este fin.</span><span class="sxs-lookup"><span data-stu-id="05235-105">Developers using Visual Studio can use the Object Relational Designer for this purpose.</span></span>  
  
 <span data-ttu-id="05235-106">Si usa la herramienta de línea de comandos de SQLMetal, use la opción **/Serialization** con el `unidirectional` argumento.</span><span class="sxs-lookup"><span data-stu-id="05235-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="05235-107">Para obtener más información, vea [SqlMetal.exe (Herramienta de generación de código)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="05235-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05235-108">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="05235-108">Example</span></span>  

 <span data-ttu-id="05235-109">Con las siguientes líneas de comandos de SQLMetal se generan archivos que tienen entidades serializables.</span><span class="sxs-lookup"><span data-stu-id="05235-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```console  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```console  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="05235-110">Vea también</span><span class="sxs-lookup"><span data-stu-id="05235-110">See also</span></span>

- [<span data-ttu-id="05235-111">Serialización</span><span class="sxs-lookup"><span data-stu-id="05235-111">Serialization</span></span>](serialization.md)
- [<span data-ttu-id="05235-112">Crear el modelo de objetos</span><span class="sxs-lookup"><span data-stu-id="05235-112">Creating the Object Model</span></span>](creating-the-object-model.md)

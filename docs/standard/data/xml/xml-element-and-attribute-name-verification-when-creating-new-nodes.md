---
title: Comprobación de nombres de atributos y elementos XML al crear nodos nuevos
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
ms.openlocfilehash: 1da893261b35c6b57c4f08eb53b7701ec1d81fae
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289855"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="90a4c-102">Comprobación de nombres de atributos y elementos XML al crear nodos nuevos</span><span class="sxs-lookup"><span data-stu-id="90a4c-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="90a4c-103">El modelo de objetos de documento (DOM) XML comprueba la validez de los nombres cuando se crean nuevos nodos de elementos o de atributos.</span><span class="sxs-lookup"><span data-stu-id="90a4c-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="90a4c-104">Si los nombres contienen caracteres no válidos, se produce una excepción.</span><span class="sxs-lookup"><span data-stu-id="90a4c-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="90a4c-105">Para asegurarse de que los nombres son válidos y que están codificados correctamente, debe usar la clase **XmlConvert** para codificar el nombre y decodificarlo de nuevo en el nivel de aplicación.</span><span class="sxs-lookup"><span data-stu-id="90a4c-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="90a4c-106">La clase **XmlWriter** cuenta con métodos que realizan trabajo adicional para asegurar que se genera XML con el formato correcto.</span><span class="sxs-lookup"><span data-stu-id="90a4c-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90a4c-107">Vea también</span><span class="sxs-lookup"><span data-stu-id="90a4c-107">See also</span></span>

- [<span data-ttu-id="90a4c-108">Document Object Model (DOM) para XML</span><span class="sxs-lookup"><span data-stu-id="90a4c-108">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)

---
title: Procedimiento para cifrar elementos XML con claves simétricas
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AES algorithm
- cryptography [.NET Framework], symmetric keys
- encryption [.NET Framework], symmetric keys
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Advanced Encryption Standard algorithm
- Rijndael
ms.assetid: d8461a44-aa2c-4ef4-b3e4-ab7cbaaee1b5
ms.openlocfilehash: 1ad75b7f36130a9f3acad97f724406650a7fdb68
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277328"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a>Procedimiento para cifrar elementos XML con claves simétricas
Puede usar las clases en el espacio de nombres <xref:System.Security.Cryptography.Xml> para cifrar un elemento dentro de un documento XML.  El cifrado XML le permite almacenar o transportar información XML confidencial, sin preocuparse de que los datos se puedan leer con facilidad.  Este procedimiento cifra un elemento XML mediante el algoritmo Estándar de cifrado avanzado (AES), también conocido como Rijndael.  
  
 Para obtener información sobre cómo descifrar un elemento XML cifrado mediante este procedimiento, vea [Cómo: descifrar elementos XML con claves simétricas](how-to-decrypt-xml-elements-with-symmetric-keys.md).  
  
 Al usar un algoritmo simétrico como AES para cifrar datos XML, debe usar la misma clave para cifrar y descifrar los datos XML.  En el ejemplo de este procedimiento se supone que el código XML cifrado se descifrará con la misma clave y que las partes de cifrado y descifrado están de acuerdo en el algoritmo y la clave que se van a usar.  En este ejemplo no se almacena ni se cifra la clave AES dentro del código XML cifrado.  
  
 Este ejemplo es idóneo en las situaciones en las que una aplicación necesita cifrar datos en función de una clave de sesión almacenada en memoria o en función de una clave criptográficamente segura derivada de una contraseña.  En las situaciones en las que dos o más aplicaciones deben compartir datos XML cifrados, considere el uso de un esquema de cifrado basado en un algoritmo asimétrico o un certificado X.509.  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a>Para cifrar un elemento XML con una clave simétrica  
  
1. Genere una clave simétrica mediante la clase <xref:System.Security.Cryptography.RijndaelManaged>.  Esta clave se usará para cifrar el elemento XML.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. Cree un objeto <xref:System.Xml.XmlDocument> cargando un archivo XML del disco.  El objeto <xref:System.Xml.XmlDocument> contiene el elemento XML que se va a cifrar.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. Busque el elemento especificado en el objeto <xref:System.Xml.XmlDocument> y cree un objeto <xref:System.Xml.XmlElement> nuevo para representar el elemento que desea cifrar.  En este ejemplo, el elemento `"creditcard"` está cifrado.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. Cree una nueva instancia de la clase <xref:System.Security.Cryptography.Xml.EncryptedXml> y úsela para cifrar el <xref:System.Xml.XmlElement> con la clave simétrica.  El método <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> devuelve el elemento cifrado como una matriz de bytes cifrados.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. Construya un objeto <xref:System.Security.Cryptography.Xml.EncryptedData> y rellénelo con el identificador de dirección URL del elemento XML cifrado.  Este identificador de dirección URL permite que una entidad descifradora sepa que el código XML contiene un elemento cifrado.  Puede usar el campo <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> para especificar el identificador de dirección URL.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. Cree un objeto <xref:System.Security.Cryptography.Xml.EncryptionMethod> inicializado en el identificador de dirección URL del algoritmo criptográfico usado para generar la clave.  Pase el objeto <xref:System.Security.Cryptography.Xml.EncryptionMethod> a la propiedad <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A>.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. Agregue los datos de elementos cifrados al objeto <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. Reemplace el elemento del objeto <xref:System.Xml.XmlDocument> original por el elemento <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a>Ejemplo  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
  
- Para compilar este ejemplo, debe incluir una referencia a `System.Security.dll`.  
  
- Incluya los siguientes espacios de nombres: <xref:System.Xml>, <xref:System.Security.Cryptography> y <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 No almacene nunca una clave criptográfica en texto sin formato ni transfiera una clave entre equipos en texto sin formato.  En su lugar, use un contenedor de claves seguro para almacenar las claves criptográficas.  
  
 Cuando termine de usar una clave criptográfica, bórrela de la memoria estableciendo cada byte en cero o llamando al método <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> de la clase criptográfica administrada.  
  
## <a name="see-also"></a>Consulte también

- <xref:System.Security.Cryptography.Xml>
- [Procedimiento para descifrar elementos XML con claves simétricas](how-to-decrypt-xml-elements-with-symmetric-keys.md)

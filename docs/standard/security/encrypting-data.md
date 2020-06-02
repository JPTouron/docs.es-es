---
title: Cifrar datos
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET Framework], symmetric
- symmetric encryption
- cryptography [.NET Framework], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
ms.openlocfilehash: 3230836b93ea191e5de27717a918038f2f8dead6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288360"
---
# <a name="encrypting-data"></a><span data-ttu-id="1bb89-102">Cifrar datos</span><span class="sxs-lookup"><span data-stu-id="1bb89-102">Encrypting Data</span></span>
<span data-ttu-id="1bb89-103">El cifrado simétrico y el cifrado asimétrico se efectúan mediante procesos distintos.</span><span class="sxs-lookup"><span data-stu-id="1bb89-103">Symmetric encryption and asymmetric encryption are performed using different processes.</span></span> <span data-ttu-id="1bb89-104">El cifrado simétrico se realiza en secuencias y, por tanto, resulta útil para cifrar grandes cantidades de datos.</span><span class="sxs-lookup"><span data-stu-id="1bb89-104">Symmetric encryption is performed on streams and is therefore useful to encrypt large amounts of data.</span></span> <span data-ttu-id="1bb89-105">El cifrado asimétrico se realiza en un pequeño número de bytes y, por tanto, solo resulta útil para pequeñas cantidades de datos.</span><span class="sxs-lookup"><span data-stu-id="1bb89-105">Asymmetric encryption is performed on a small number of bytes and is therefore useful only for small amounts of data.</span></span>  
  
## <a name="symmetric-encryption"></a><span data-ttu-id="1bb89-106">Cifrado simétrico</span><span class="sxs-lookup"><span data-stu-id="1bb89-106">Symmetric Encryption</span></span>  
 <span data-ttu-id="1bb89-107">Las clases de criptografía simétrica administrada se usan con una clase de secuencia especial llamada <xref:System.Security.Cryptography.CryptoStream> que cifra los datos leídos en la secuencia.</span><span class="sxs-lookup"><span data-stu-id="1bb89-107">The managed symmetric cryptography classes are used with a special stream class called a <xref:System.Security.Cryptography.CryptoStream> that encrypts data read into the stream.</span></span> <span data-ttu-id="1bb89-108">La clase **CryptoStream** se inicializa con una clase de secuencia administrada, una clase que implementa la interfaz <xref:System.Security.Cryptography.ICryptoTransform> (creada a partir de una clase que implementa un algoritmo criptográfico) y una enumeración <xref:System.Security.Cryptography.CryptoStreamMode> que describe el tipo de acceso permitido a **CryptoStream**.</span><span class="sxs-lookup"><span data-stu-id="1bb89-108">The **CryptoStream** class is initialized with a managed stream class, a class implements the <xref:System.Security.Cryptography.ICryptoTransform> interface (created from a class that implements a cryptographic algorithm), and a <xref:System.Security.Cryptography.CryptoStreamMode> enumeration that describes the type of access permitted to the **CryptoStream**.</span></span> <span data-ttu-id="1bb89-109">La clase **CryptoStream** puede inicializarse usando cualquier clase que derive de la <xref:System.IO.Stream> clase, incluidas <xref:System.IO.FileStream> , <xref:System.IO.MemoryStream> y <xref:System.Net.Sockets.NetworkStream> .</span><span class="sxs-lookup"><span data-stu-id="1bb89-109">The **CryptoStream** class can be initialized using any class that derives from the <xref:System.IO.Stream> class, including <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, and <xref:System.Net.Sockets.NetworkStream>.</span></span> <span data-ttu-id="1bb89-110">Mediante estas clases, puede realizar el cifrado simétrico en diversos objetos de secuencia.</span><span class="sxs-lookup"><span data-stu-id="1bb89-110">Using these classes, you can perform symmetric encryption on a variety of stream objects.</span></span>  
  
 <span data-ttu-id="1bb89-111">En el ejemplo siguiente se muestra cómo crear una nueva instancia de la clase <xref:System.Security.Cryptography.RijndaelManaged> , que implementa el algoritmo de cifrado Rijndael, y usarla para realizar el cifrado en una clase **CryptoStream** .</span><span class="sxs-lookup"><span data-stu-id="1bb89-111">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class, which implements the Rijndael encryption algorithm, and use it to perform encryption on a **CryptoStream** class.</span></span> <span data-ttu-id="1bb89-112">En este ejemplo, **CryptoStream** se inicializa con un objeto de secuencia llamado `myStream` que puede ser cualquier tipo de secuencia administrada.</span><span class="sxs-lookup"><span data-stu-id="1bb89-112">In this example, the **CryptoStream** is initialized with a stream object called `myStream` that can be any type of managed stream.</span></span> <span data-ttu-id="1bb89-113">Se pasan la clave y el IV que se usan para el cifrado al método **CreateEncryptor** de la clase **RijndaelManaged** .</span><span class="sxs-lookup"><span data-stu-id="1bb89-113">The **CreateEncryptor** method from the **RijndaelManaged** class is passed the key and IV that are used for encryption.</span></span> <span data-ttu-id="1bb89-114">En este caso, se usan la clave predeterminada y el IV generados desde `rmCrypto` .</span><span class="sxs-lookup"><span data-stu-id="1bb89-114">In this case, the default key and IV generated from `rmCrypto` are used.</span></span> <span data-ttu-id="1bb89-115">Por último, se pasa **CryptoStreamMode.Write y** , que especifica el acceso de escritura a la secuencia.</span><span class="sxs-lookup"><span data-stu-id="1bb89-115">Finally, the **CryptoStreamMode.Write** is passed, specifying write access to the stream.</span></span>  
  
```vb  
Dim rmCrypto As New RijndaelManaged()  
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateEncryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Write)  
```  
  
```csharp  
RijndaelManaged rmCrypto = new RijndaelManaged();  
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 <span data-ttu-id="1bb89-116">Después de que se ejecute este código, los datos escritos en el objeto **CryptoStream** se cifran usando el algoritmo Rijndael.</span><span class="sxs-lookup"><span data-stu-id="1bb89-116">After this code is executed, any data written to the **CryptoStream** object is encrypted using the Rijndael algorithm.</span></span>  
  
 <span data-ttu-id="1bb89-117">En el ejemplo siguiente se muestra todo el proceso de crear una secuencia, cifrarla, escribir en ella y cerrarla.</span><span class="sxs-lookup"><span data-stu-id="1bb89-117">The following example shows the entire process of creating a stream, encrypting the stream, writing to the stream, and closing the stream.</span></span> <span data-ttu-id="1bb89-118">En este ejemplo se crea una secuencia de red que se cifra usando las clases **CryptoStream** y **RijndaelManaged** .</span><span class="sxs-lookup"><span data-stu-id="1bb89-118">This example creates a network stream that is encrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="1bb89-119">Se escribe un mensaje en la secuencia cifrada con la clase <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="1bb89-119">A message is written to the encrypted stream with the <xref:System.IO.StreamWriter> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1bb89-120">También puede usar este ejemplo para escribir en un archivo.</span><span class="sxs-lookup"><span data-stu-id="1bb89-120">You can also use this example to write to a file.</span></span> <span data-ttu-id="1bb89-121">Para ello, elimine la referencia <xref:System.Net.Sockets.TcpClient> y reemplace <xref:System.Net.Sockets.NetworkStream> con <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="1bb89-121">To do that, delete the <xref:System.Net.Sockets.TcpClient> reference and replace the <xref:System.Net.Sockets.NetworkStream> with a <xref:System.IO.FileStream>.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
Imports System.Net.Sockets  
  
Module Module1  
Sub Main()  
   Try  
      'Create a TCP connection to a listening TCP process.  
      'Use "localhost" to specify the current computer or  
      'replace "localhost" with the IP address of the
      'listening process.
      Dim tcp As New TcpClient("localhost", 11000)  
  
      'Create a network stream from the TCP connection.
      Dim netStream As NetworkStream = tcp.GetStream()  
  
      'Create a new instance of the RijndaelManaged class  
      'and encrypt the stream.  
      Dim rmCrypto As New RijndaelManaged()  
  
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
  
      'Create a CryptoStream, pass it the NetworkStream, and encrypt
      'it with the Rijndael class.  
      Dim cryptStream As New CryptoStream(netStream, rmCrypto.CreateEncryptor(key, iv), CryptoStreamMode.Write)  
  
      'Create a StreamWriter for easy writing to the
      'network stream.  
      Dim sWriter As New StreamWriter(cryptStream)  
  
      'Write to the stream.  
      sWriter.WriteLine("Hello World!")  
  
      'Inform the user that the message was written  
      'to the stream.  
      Console.WriteLine("The message was sent.")  
  
      'Close all the connections.  
      sWriter.Close()  
      cryptStream.Close()  
      netStream.Close()  
      tcp.Close()  
   Catch  
      'Inform the user that an exception was raised.  
      Console.WriteLine("The connection failed.")  
   End Try  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
using System.Net.Sockets;  
  
public class main  
{  
   public static void Main(string[] args)  
   {  
      try  
      {  
         //Create a TCP connection to a listening TCP process.  
         //Use "localhost" to specify the current computer or  
         //replace "localhost" with the IP address of the
         //listening process.
         TcpClient tcp = new TcpClient("localhost",11000);  
  
         //Create a network stream from the TCP connection.
         NetworkStream netStream = tcp.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and encrypt the stream.  
         RijndaelManaged rmCrypto = new RijndaelManaged();  
  
         byte[] key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
         byte[] iv = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
  
         //Create a CryptoStream, pass it the NetworkStream, and encrypt
         //it with the Rijndael class.  
         CryptoStream cryptStream = new CryptoStream(netStream,
         rmCrypto.CreateEncryptor(key, iv),
         CryptoStreamMode.Write);  
  
         //Create a StreamWriter for easy writing to the
         //network stream.  
         StreamWriter sWriter = new StreamWriter(cryptStream);  
  
         //Write to the stream.  
         sWriter.WriteLine("Hello World!");  
  
         //Inform the user that the message was written  
         //to the stream.  
         Console.WriteLine("The message was sent.");  
  
         //Close all the connections.  
         sWriter.Close();  
         cryptStream.Close();  
         netStream.Close();  
         tcp.Close();  
      }  
      catch  
      {  
         //Inform the user that an exception was raised.  
         Console.WriteLine("The connection failed.");  
      }  
   }  
}  
```  
  
 <span data-ttu-id="1bb89-122">Para que el ejemplo anterior se ejecute correctamente, debe haber un proceso escuchando en la dirección IP y un número de puerto especificado en la clase <xref:System.Net.Sockets.TcpClient> .</span><span class="sxs-lookup"><span data-stu-id="1bb89-122">For the previous example to execute successfully, there must be a process listening on the IP address and port number specified in the <xref:System.Net.Sockets.TcpClient> class.</span></span> <span data-ttu-id="1bb89-123">Si existe un proceso de escucha, el código se conectará con el proceso de escucha, cifrará la secuencia usando el algoritmo simétrico Rijndael y escribirá "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="1bb89-123">If a listening process exists, the code will connect to the listening process, encrypt the stream using the Rijndael symmetric algorithm, and write "Hello World!"</span></span> <span data-ttu-id="1bb89-124">en la secuencia.</span><span class="sxs-lookup"><span data-stu-id="1bb89-124">to the stream.</span></span> <span data-ttu-id="1bb89-125">Si el código es correcto, mostrará el texto siguiente en la consola:</span><span class="sxs-lookup"><span data-stu-id="1bb89-125">If the code is successful, it displays the following text to the console:</span></span>  
  
```console  
The message was sent.  
```  
  
 <span data-ttu-id="1bb89-126">Sin embargo, si no se encuentra ningún proceso de escucha o si se produce una excepción, el código muestra el texto siguiente en la consola:</span><span class="sxs-lookup"><span data-stu-id="1bb89-126">However, if no listening process is found or an exception is raised, the code displays the following text to the console:</span></span>  
  
```console  
The connection failed.  
```  
  
## <a name="asymmetric-encryption"></a><span data-ttu-id="1bb89-127">Cifrado asimétrico</span><span class="sxs-lookup"><span data-stu-id="1bb89-127">Asymmetric Encryption</span></span>  
 <span data-ttu-id="1bb89-128">Los algoritmos asimétricos suelen usarse para cifrar pequeñas cantidades de datos, como el cifrado de una clave simétrica y un IV.</span><span class="sxs-lookup"><span data-stu-id="1bb89-128">Asymmetric algorithms are usually used to encrypt small amounts of data such as the encryption of a symmetric key and IV.</span></span> <span data-ttu-id="1bb89-129">Normalmente, cuando se realiza un cifrado asimétrico, se usa la clave pública generada por terceros.</span><span class="sxs-lookup"><span data-stu-id="1bb89-129">Typically, an individual performing asymmetric encryption uses the public key generated by another party.</span></span> <span data-ttu-id="1bb89-130">.NET Framework proporciona la clase <xref:System.Security.Cryptography.RSACryptoServiceProvider> necesaria para este propósito.</span><span class="sxs-lookup"><span data-stu-id="1bb89-130">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is provided by the .NET Framework for this purpose.</span></span>  
  
 <span data-ttu-id="1bb89-131">En el ejemplo siguiente se usa la información de clave pública para cifrar una clave simétrica y un IV.</span><span class="sxs-lookup"><span data-stu-id="1bb89-131">The following example uses public key information to encrypt a symmetric key and IV.</span></span> <span data-ttu-id="1bb89-132">Se inicializan dos matrices de bytes que representan la clave pública de un tercero.</span><span class="sxs-lookup"><span data-stu-id="1bb89-132">Two byte arrays are initialized that represent the public key of a third party.</span></span> <span data-ttu-id="1bb89-133">Se inicializa un objeto <xref:System.Security.Cryptography.RSAParameters> en estos valores.</span><span class="sxs-lookup"><span data-stu-id="1bb89-133">An <xref:System.Security.Cryptography.RSAParameters> object is initialized to these values.</span></span> <span data-ttu-id="1bb89-134">A continuación, el objeto **RSAParameters** (junto con la clave pública que representa) se importa en **RSACryptoServiceProvider** a través del método <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1bb89-134">Next, the **RSAParameters** object (along with the public key it represents) is imported into an **RSACryptoServiceProvider** using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1bb89-135">Por último, se cifran la clave privada y el IV creados por una clase <xref:System.Security.Cryptography.RijndaelManaged> .</span><span class="sxs-lookup"><span data-stu-id="1bb89-135">Finally, the private key and IV created by a <xref:System.Security.Cryptography.RijndaelManaged> class are encrypted.</span></span> <span data-ttu-id="1bb89-136">Este ejemplo requiere sistemas que tengan instalado el cifrado de 128 bits.</span><span class="sxs-lookup"><span data-stu-id="1bb89-136">This example requires systems to have 128-bit encryption installed.</span></span>  
  
```vb  
Imports System  
Imports System.Security.Cryptography  
  
Module Module1  
  
    Sub Main()  
        'Initialize the byte arrays to the public key information.  
      Dim publicKey As Byte() =  {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19,202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}  
  
        Dim exponent As Byte() = {1, 0, 1}  
  
        'Create values to store encrypted symmetric keys.  
        Dim encryptedSymmetricKey() As Byte  
        Dim encryptedSymmetricIV() As Byte  
  
        'Create a new instance of the RSACryptoServiceProvider class.  
        Dim rsa As New RSACryptoServiceProvider()  
  
        'Create a new instance of the RSAParameters structure.  
        Dim rsaKeyInfo As New RSAParameters()  
  
        'Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = publicKey  
        rsaKeyInfo.Exponent = exponent  
  
        'Import key parameters into rsa.  
        rsa.ImportParameters(rsaKeyInfo)  
  
        'Create a new instance of the RijndaelManaged class.  
        Dim RM As New RijndaelManaged()  
  
        'Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(RM.Key, False)  
        encryptedSymmetricIV = rsa.Encrypt(RM.IV, False)  
    End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using System.Security.Cryptography;  
  
class Class1  
{  
   static void Main()  
   {  
      //Initialize the byte arrays to the public key information.  
      byte[] publicKey = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,  
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,  
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,  
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,  
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,  
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,  
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,  
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};  
  
      byte[] exponent = {1,0,1};  
  
      //Create values to store encrypted symmetric keys.  
      byte[] encryptedSymmetricKey;  
      byte[] encryptedSymmetricIV;  
  
      //Create a new instance of the RSACryptoServiceProvider class.  
      RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
  
      //Create a new instance of the RSAParameters structure.  
      RSAParameters rsaKeyInfo = new RSAParameters();  
  
      //Set rsaKeyInfo to the public key values.
      rsaKeyInfo.Modulus = publicKey;  
      rsaKeyInfo.Exponent = exponent;  
  
      //Import key parameters into RSA.  
      rsa.ImportParameters(rsaKeyInfo);  
  
      //Create a new instance of the RijndaelManaged class.  
      RijndaelManaged rm = new RijndaelManaged();  
  
      //Encrypt the symmetric key and IV.  
      encryptedSymmetricKey = rsa.Encrypt(rm.Key, false);  
      encryptedSymmetricIV = rsa.Encrypt(rm.IV, false);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bb89-137">Consulte también</span><span class="sxs-lookup"><span data-stu-id="1bb89-137">See also</span></span>

- [<span data-ttu-id="1bb89-138">Generar claves para cifrado y descifrado</span><span class="sxs-lookup"><span data-stu-id="1bb89-138">Generating Keys for Encryption and Decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="1bb89-139">Descifrar datos</span><span class="sxs-lookup"><span data-stu-id="1bb89-139">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="1bb89-140">Servicios criptográficos</span><span class="sxs-lookup"><span data-stu-id="1bb89-140">Cryptographic Services</span></span>](cryptographic-services.md)

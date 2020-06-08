---
title: Convertir cadenas en tipos de datos de .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
ms.openlocfilehash: fda5441c58d14b91a9eca16fff9149c8795f95b9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289231"
---
# <a name="converting-strings-to-net-framework-data-types"></a>Convertir cadenas en tipos de datos de .NET Framework
Si desea convertir una cadena en un tipo de datos de .NET Framework, utilice el método **XmlConvert** que cumple los requisitos de la aplicación. Para obtener una lista de los métodos de conversión disponibles en la clase **XmlConvert**, vea <xref:System.Xml.XmlConvert>.  
  
 La cadena que devuelve el método **ToString** es una versión de cadena de los datos que se le pasan. Además, hay varios tipos de .NET Framework que realizan la conversión mediante la clase **XmlConvert**, pero no utilizan los métodos de la clase **System.Convert**. La clase **XmlConvert** sigue la especificación de tipos de datos de los esquemas XML (XSD) y tiene un tipo de datos que se puede asignar en **XmlConvert**.  
  
 En la tabla siguiente se enumeran los tipos de datos de .NET Framework y los tipos de cadena que se devuelven mediante la asignación de tipos de datos de los esquemas XML (XSD). Estos tipos de .NET Framework no se pueden procesar mediante **System.Convert**.  
  
|Tipo de .NET Framework|Cadena devuelta|  
|-------------------------|---------------------|  
|Booleano|"true", "false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DateTime|El formato es "aaaa-MM-ddTHH:mm:sszzzzzz" y sus subconjuntos.|  
|Timespan|El formato es PnYnMnTnHnMnS, es decir, `P2Y10M15DT10H30M20S` corresponde a una duración de 2 años, 10 meses, 15 días, 10 horas, 30 minutos y 20 segundos.|  
  
> [!NOTE]
> Si se convierte uno de los tipos de .NET Framework enumerados en la tabla en una cadena mediante el método **ToString**, la cadena devuelta no será el tipo base, sino el tipo de cadena de esquema XML (XSD).  
  
 Los tipos de valor de **DateTime** y **Timespan** difieren en que **DateTime** representa un instante en el tiempo, mientras que **TimeSpan** representa un intervalo de tiempo. Los formatos de **DateTime** y **Timespan** se describen en la especificación de tipos de datos de esquema XML (XSD). Por ejemplo:  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim [date] As New DateTime(2001, 8, 4)  
writer.WriteElementString("Date", XmlConvert.ToString([date]))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
DateTime date = new DateTime (2001, 08, 04);  
writer.WriteElementString("Date", XmlConvert.ToString(date));  
```  
  
 **Salida**  
  
 `<Date>2001-08-04T00:00:00</Date>`.  
  
 En el código siguiente se convierte un número entero en una cadena:  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim value As Int32 = 200  
writer.WriteElementString("Number", XmlConvert.ToString(value))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
Int32 value = 200;  
writer.WriteElementString("Number", XmlConvert.ToString(value));  
```  
  
 **Salida**  
  
 `<Number>200</Number>`  
  
 Sin embargo, si se convierte una cadena en un tipo **Boolean**, **Single** o **Double**, el tipo de .NET Framework que se devuelve no es el mismo que el devuelto al utilizar la clase **System.Convert**.  
  
## <a name="string-to-boolean"></a>Conversión de cadenas en Boolean  
 En la tabla siguiente se muestra qué tipo se genera para las cadenas de entrada dadas al convertir una cadena en **Boolean** mediante el método **ToBoolean**.  
  
|Parámetro de entrada de cadena válido|Tipo de salida de .NET Framework|  
|----------------------------------|--------------------------------|  
|"true"|Boolean.True|  
|"1"|Boolean.True|  
|"false"|Boolean.False|  
|"0"|Boolean.False|  
  
 Por ejemplo, dado el siguiente código XML:  
  
 **Entrada**  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>
```  
  
 El código siguiente puede entender ambas líneas y **bvalue** es **System.Boolean.True**:  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a>Conversión de cadenas en Single  
 En la tabla siguiente se muestra qué tipo se genera para las cadenas de entrada dadas, al convertir una cadena en **Single** mediante el método **ToSingle**.  
  
|Parámetro de entrada de cadena válido|Tipo de salida de .NET Framework|  
|----------------------------------|--------------------------------|  
|"INF"|Single.PositiveInfinity|  
|"-INF"|Single.NegativeInfinity|  
  
## <a name="string-to-double"></a>Conversión de cadenas en Double  
 En la tabla siguiente se muestra qué tipo se genera para las cadenas de entrada dadas, al convertir una cadena en **Single** mediante el método **ToDouble**.  
  
|Parámetro de entrada de cadena válido|Tipo de salida de .NET Framework|  
|----------------------------------|--------------------------------|  
|"INF"|Double.PositiveInfinity|  
|"-INF"|Double.NegativeInfinity|  
  
 El código siguiente escribe `<Infinity>INF</Infinity>`:  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a>Vea también

- [Conversión de tipos de datos XML](conversion-of-xml-data-types.md)
- [Conversión de tipos de .NET Framework en cadenas](converting-dotnet-types-to-strings.md)

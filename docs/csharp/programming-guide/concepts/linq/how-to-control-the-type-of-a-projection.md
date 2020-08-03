---
title: Procedimiento para controlar el tipo de una proyección (C#)
description: Obtenga información sobre cómo controlar el tipo de una proyección en LINQ en C# para crear colecciones de tipos que no sean IEnumerable<T> de XElement.
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: 32b019b5e1574e7160b4dce5fb0322caa3c1ca71
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103349"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a>Procedimiento para controlar el tipo de una proyección (C#)
La proyección es el proceso de tomar un conjunto de datos, filtrarlo, cambiar su forma e incluso cambiar su tipo. La mayoría de las expresiones de consulta realizan proyecciones. La mayor parte de las expresiones de consulta de esta sección se evalúan como <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, aunque puede controlar el tipo de proyección para crear colecciones de otros tipos. En este tema se explica cómo hacerlo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, se define un nuevo tipo, `Customer`. La expresión de consulta crea una instancia de nuevos objetos `Customer` en la cláusula `Select`. Esto hace que el tipo de la expresión de consulta sea <xref:System.Collections.Generic.IEnumerable%601> de `Customer`.  
  
 Este ejemplo utiliza el siguiente documento XML: [Archivo XML de ejemplo: Clientes y pedidos (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
```csharp  
public class Customer  
{  
    private string customerID;  
    public string CustomerID{ get{return customerID;} set{customerID = value;}}  
  
    private string companyName;  
    public string CompanyName{ get{return companyName;} set{companyName = value;}}  
  
    private string contactName;  
    public string ContactName { get{return contactName;} set{contactName = value;}}  
  
    public Customer(string customerID, string companyName, string contactName)  
    {  
        CustomerID = customerID;  
        CompanyName = companyName;  
        ContactName = contactName;  
    }  
  
    public override string ToString()  
    {  
        return $"{this.customerID}:{this.companyName}:{this.contactName}";
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement custOrd = XElement.Load("CustomersOrders.xml");  
        IEnumerable<Customer> custList =  
            from el in custOrd.Element("Customers").Elements("Customer")  
            select new Customer(  
                (string)el.Attribute("CustomerID"),  
                (string)el.Element("CompanyName"),  
                (string)el.Element("ContactName")  
            );  
        foreach (Customer cust in custList)  
            Console.WriteLine(cust);  
    }  
}  
```  
  
 Este código genera el siguiente resultado:  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Vea también

- <xref:System.Linq.Enumerable.Select%2A>

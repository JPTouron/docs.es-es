---
title: Elemento <assemblyBinding> para <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
ms.openlocfilehash: 202b063ad3f0f9696cdc12aff434d61fe5a813e6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154327"
---
# <a name="assemblybinding-element-for-runtime"></a>Elemento \<assemblyBinding> para \<runtime>
Contiene información sobre la redirección de versiones de ensamblado y las ubicaciones de ensamblados.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyBinding>**  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
      <assemblyBinding
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|**xmlns**|Atributo necesario.<br /><br /> Especifica el espacio de nombres XML necesario para el enlace de ensamblados. Utilice la cadena "urn: schemas-microsoft-v1" como valor.|  
|**appliesTo**|Especifica la versión en tiempo de ejecución a la que se aplica la redirección del ensamblado de .NET Framework. Este atributo opcional usa un número de versión de .NET Framework para indicar a qué versión se aplica. Si no se especifica ningún atributo **appliesTo** , el **\<assemblyBinding>** elemento se aplica a todas las versiones del .NET Framework. El atributo **appliesTo** se incorporó en .NET Framework versión 1,1; se omite en la versión 1,0 de .NET Framework. Esto significa que todos los **\<assemblyBinding>** elementos se aplican cuando se usa la .NET Framework versión 1,0, aunque se especifique un atributo **appliesTo** .|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[\<dependentAssembly>](dependentassembly-element.md)|Encapsula la directiva de enlace y la ubicación de un ensamblado. Use una **\<dependentAssembly>** etiqueta para cada ensamblado.|  
|[\<probing>](probing-element.md)|Especifica los subdirectorios en los que busca Common Language Runtime cuando se cargan los ensamblados.|  
|[\<publisherPolicy>](publisherpolicy-element.md)|Especifica si el tiempo de ejecución aplica la directiva de editor.|  
|[\<qualifyAssembly>](qualifyassembly-element.md)|Especifica el nombre completo del ensamblado que debe cargarse dinámicamente cuando se utiliza un nombre parcial.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|`configuration`|Elemento raíz de cada archivo de configuración usado por las aplicaciones de Common Language Runtime y .NET Framework.|  
|`runtime`|Contiene información del enlace del ensamblado y de la recolección de elementos no utilizados.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, se muestra cómo redirigir una versión de ensamblado a otra versión y cómo proporcionar un código base.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 En el ejemplo siguiente se muestra cómo usar el atributo **appliesTo** para redirigir el enlace de un ensamblado de .NET Framework.  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a>Consulte también

- [Esquema de la configuración de Common Language Runtime](index.md)
- [Esquema de los archivos de configuración](../index.md)
- [Redirigir versiones de ensamblado](../../redirect-assembly-versions.md)

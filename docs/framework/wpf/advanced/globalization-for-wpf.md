---
title: Globalización
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: 2d7cf73e37fe8c4bbdbef3d356f1dbb8903815f3
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812333"
---
# <a name="globalization-for-wpf"></a>Globalización de WPF
En este tema se presentan los problemas que debe tener en cuenta al escribir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplicaciones para el mercado mundial. Los elementos de programación de globalización se definen en .NET en el <xref:System.Globalization> espacio de nombres.

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>Globalización XAML
 Lenguaje XAML (XAML) se basa en XML y aprovecha la compatibilidad de globalización definida en la especificación XML. En las secciones siguientes se describen algunas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de las características que debe tener en cuenta.

<a name="char_reference"></a>
### <a name="character-references"></a>Referencias de caracteres
Una referencia de carácter proporciona la unidad de código UTF16 del carácter Unicode determinado que representa, en formato decimal o hexadecimal. En el ejemplo siguiente se muestra una referencia de carácter decimal para la letra mayúscula CÓPTICA HORI o ' Ϩ ':

```xaml
&#1000;
```

En el ejemplo siguiente se muestra una referencia de carácter hexadecimal. Observe que tiene una **x** delante del número hexadecimal.

```xaml
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>Encoding
 La codificación admitida por [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] son ASCII, Unicode UTF-16 y UTF-8. La instrucción de codificación está al principio del [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] documento. Si no existe ningún atributo de codificación y no hay ningún orden de bytes, el analizador utiliza el valor predeterminado UTF-8. UTF-8 y UTF-16 son las codificaciones preferentes. No se admite UTF-7. En el ejemplo siguiente se muestra cómo especificar una codificación UTF-8 en un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] archivo.

```xaml
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>Atributo de idioma
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usa [xml: lang](../../../desktop-wpf/xaml-services/xml-language-handling.md) para representar el atributo de idioma de un elemento.  Para beneficiarse de la <xref:System.Globalization.CultureInfo> clase, el valor del atributo Language debe ser uno de los nombres de referencia cultural predefinidos por <xref:System.Globalization.CultureInfo> . [xml:lang](../../../desktop-wpf/xaml-services/xml-language-handling.md) es heredable en el árbol de elementos (mediante reglas XML, no necesariamente debido a la herencia de las propiedades de dependencia) y su valor predeterminado es una cadena vacía si no se asigna de manera explícita.

 El atributo de idioma es muy útil para especificar dialectos. Por ejemplo, el francés tiene una ortografía, un vocabulario y una pronunciación diferentes en Francia, Quebec, Bélgica y Suiza. Además, el chino, el japonés y el coreano comparten puntos de código en Unicode, pero las formas ideográficas son diferentes y usan fuentes totalmente diferentes.

 En el [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ejemplo siguiente se utiliza el `fr-CA` atributo Language para especificar francés canadiense.

```xaml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] admite todas las características Unicode, incluidos los suplentes. Siempre que el juego de caracteres se pueda asignar a Unicode, se admite. Por ejemplo, GB18030 presenta algunos caracteres que se asignan a la extensión A y B de chino, japonés y coreano (CFK) y pares suplentes, por lo tanto, es totalmente compatible. Una [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicación puede utilizar <xref:System.Globalization.StringInfo> para manipular cadenas sin comprender si tienen pares suplentes o caracteres combinables.

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>Diseñar una interfaz de usuario internacional con XAML
 En esta sección se describen [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] las características que debe tener en cuenta al escribir una aplicación.

<a name="intl_text"></a>
### <a name="international-text"></a>Texto internacional
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] incluye el procesamiento integrado para todos los sistemas de escritura compatibles con el marco de Microsoft .NET.

 Actualmente se admiten los siguientes scripts:

- Árabe

- Bengalí

- Devanagari

- Cirílico

- Griego

- Gujarati

- Gurmukhi

- Hebreo

- Scripts ideográficos

- Canarés

- Lao

- Latín

- Malayalam

- Mongol

- Odia

- Sirio

- Tamil

- Telugu

- Thaana

- Tailandés*

- Tibetano

 * En esta versión, la visualización y edición de texto tailandés es compatible; no lo es la separación de palabras.

 Actualmente no se admiten los siguientes scripts:

- Khmer

- Hangul coreano antiguo

- Myanmar

- Cingalés

 Todos los motores del sistema de escritura admiten fuentes OpenType. Las fuentes OpenType pueden incluir las tablas de diseño OpenType que permiten a los creadores de fuentes diseñar mejores fuentes tipográficas internacionales y de gama alta. Las tablas de diseño de fuentes OpenType contienen información sobre las sustituciones de glifos, la posición del glifo, la justificación y la posición de línea base, lo que permite a las aplicaciones de procesamiento de texto mejorar el diseño del texto.

 Las fuentes OpenType permiten el control de grandes conjuntos de glifos mediante la codificación Unicode. Esta codificación permite una amplia compatibilidad internacional, así como variantes tipográficas de los glifos.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] la representación de texto se basa en la tecnología de subpíxeles de ClearType de Microsoft, que admite la independencia de la resolución. Esto mejora significativamente la legibilidad y permite la capacidad de admitir documentos de estilo de revista de gran calidad para todos los scripts.

<a name="intl_layout"></a>
### <a name="international-layout"></a>Diseño internacional
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] proporciona una manera muy cómoda de admitir diseños horizontales, bidireccionales y verticales. En el marco de presentación, <xref:System.Windows.FrameworkElement.FlowDirection%2A> se puede usar la propiedad para definir el diseño. Los patrones de dirección de flujo son:

- *LeftToRight*: diseño horizontal para latín, Este de Asia y demás.

- *RightToLeft*: bidireccional para árabe, hebreo y demás.

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>Desarrollar aplicaciones localizables
 Al escribir una aplicación para su consumo global, debe tener en cuenta que la aplicación debe ser localizable. En los temas siguientes se señalan las cosas que deben tenerse en cuenta.

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>Interfaz de usuario multilingüe
 La interfaz de usuario multilingüe (MUI) es un servicio de soporte técnico de Microsoft para cambiar ius de un idioma a otro. Una [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicación utiliza el modelo de ensamblado para admitir MUI. Una aplicación contiene los ensamblados neutrales respecto al idioma, así como los ensamblados de recursos satélite dependientes del idioma. El punto de entrada es un .EXE administrado en el ensamblado principal.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] el cargador de recursos aprovecha el administrador de recursos del marco de trabajo para admitir la búsqueda de recursos y la reserva. Varios ensamblados satélite de idioma funcionan con el mismo ensamblado principal. El ensamblado de recursos que se carga depende de la <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> del subproceso actual.

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>Interfaz de usuario localizable
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] las aplicaciones usan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para definir su [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] permite a los desarrolladores especificar una jerarquía de objetos con un conjunto de propiedades y lógica. El uso principal de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] es desarrollar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicaciones, pero se puede usar para especificar una jerarquía de cualquier objeto Common Language Runtime (CLR). La mayoría de los desarrolladores usan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para especificar la aplicación [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] y usar un lenguaje de programación como C# para reaccionar a la interacción del usuario.

 Desde el punto de vista de los recursos, un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] archivo diseñado para describir un dependiente del lenguaje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] es un elemento de recurso y, por tanto, su formato de distribución final debe ser localizable para admitir idiomas internacionales. Dado [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que no puede controlar eventos, muchas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplicaciones contienen bloques de código para hacerlo. Para obtener más información, vea [información general sobre XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md). El código se quita y se compila en distintos archivos binarios cuando un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] archivo se acorta en la forma BAML de XAML. Los archivos, imágenes y otros tipos de objetos de recursos administrados con formato BAML de XAML se insertan en el ensamblado de recursos satélite, que se puede localizar a otros idiomas, o en el ensamblado principal, cuando no se requiere la localización.

> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] las aplicaciones admiten todos los recursos de FrameworkCLR, como tablas de cadenas, imágenes, etc.

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>Compilar aplicaciones localizables
 La localización significa adaptar una [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a distintas referencias culturales. Para que una [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicación sea localizable, los desarrolladores deben compilar todos los recursos localizables en un ensamblado de recursos. El ensamblado de recursos se localiza en idiomas diferentes y el código subyacente usa la API de administración de recursos para cargar. Uno de los archivos necesarios para una [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicación es un archivo de proyecto (. proj). Todos los recursos que se utilizan en la aplicación deben incluirse en el archivo de proyecto. En el ejemplo siguiente de un archivo .csproj se muestra cómo hacerlo.

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 Para usar un recurso en la aplicación, cree una instancia de <xref:System.Resources.ResourceManager> y cargue el recurso que desea usar. En el ejemplo siguiente se muestra cómo hacerlo:

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>Utilizar ClickOnce con aplicaciones localizadas
 ClickOnce es una nueva tecnología de implementación de Windows Forms que se incluirá con Visual Studio 2005. Permite la instalación y actualización de aplicaciones web. Cuando se localiza una aplicación que se implementó con ClickOnce, solo puede verse en la referencia cultural localizada. Por ejemplo, si una aplicación implementada se localiza en japonés, solo se puede ver en las ventanas en japonés de Microsoft Windows, no en inglés. Esto supone un problema porque se trata de un escenario común para que los usuarios japoneses ejecuten una versión en Inglés de Windows.

 La solución a este problema es establecer el atributo neutro de reserva de idioma. Como alternativa, un desarrollador de aplicaciones puede quitar recursos del ensamblado principal y especificar que los recursos puedan encontrarse en un ensamblado satélite correspondiente a una referencia cultural específica. Para controlar este proceso, utilice el <xref:System.Resources.NeutralResourcesLanguageAttribute> . El constructor de la <xref:System.Resources.NeutralResourcesLanguageAttribute> clase tiene dos firmas, una que toma un <xref:System.Resources.UltimateResourceFallbackLocation> parámetro para especificar la ubicación donde <xref:System.Resources.ResourceManager> debe extraer los recursos de reserva: ensamblado principal o ensamblado satélite. En el ejemplo siguiente se muestra cómo utilizar el atributo. En el caso de la ubicación de reserva definitiva, el código hace <xref:System.Resources.ResourceManager> que busque los recursos en el subdirectorio "de" del directorio del ensamblado que se está ejecutando actualmente.

```csharp
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>Consulte también

- [Información general sobre la globalización y la localización de WPF](wpf-globalization-and-localization-overview.md)

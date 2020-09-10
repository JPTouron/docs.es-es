---
title: Selección entre .NET Core y .NET Framework para aplicaciones de servidor
description: Guía para ayudarle a decidir qué implementación de .NET usar al compilar una aplicación de servidor.
author: cartermp
ms.date: 04/28/2020
ms.openlocfilehash: a3c15e8f2198b1bcc4e623a7dc7f5cddca9c83f6
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2020
ms.locfileid: "89415025"
---
# <a name="net-core-vs-net-framework-for-server-apps"></a>Diferencias entre .NET Core y .NET Framework en cuanto a aplicaciones de servidor

Existen dos implementaciones de .NET admitidas para compilar aplicaciones del lado servidor: .NET Framework y .NET Core. Ambas comparten muchos de los mismos componentes y es posible compartir código entre ellas. En cambio, presentan diferencias fundamentales y su elección depende de lo que quiera realizar. En este artículo se proporcionan orientaciones sobre cuándo usar cada una.

Use .NET Core para la aplicación de servidor cuando:

- Tenga necesidades multiplataforma.
- Tenga los microservicios como objetivo.
- Vaya a usar contenedores de Docker.
- Necesite sistemas escalables y de alto rendimiento.
- Necesite versiones de .NET en paralelo por aplicación.

Use .NET Framework para su aplicación de servidor cuando:

- La aplicación usa actualmente .NET Framework (la recomendación es extender en lugar de migrar).
- La aplicación usa bibliotecas .NET de terceros o paquetes de NuGet que no están disponibles para .NET Core.
- La aplicación usa tecnologías de .NET que no están disponibles para .NET Core.
- La aplicación usa una plataforma que no es compatible con .NET Core. Windows, macOS y Linux admiten .NET Core.

## <a name="when-to-choose-net-core"></a>Cuándo elegir .NET Core

En las siguientes secciones, se explican de manera más detallada las razones indicadas anteriormente para elegir .NET Core.

### <a name="cross-platform-needs"></a>Necesidades multiplataforma

Si la aplicación (web/servicio) tiene que ejecutarse en varias plataformas (Windows, Linux y macOS), use .NET Core.

.NET Core admite los sistemas operativos mencionados anteriormente como estación de trabajo de desarrollo. Visual Studio proporciona un entorno de desarrollo integrado (IDE) para Windows y macOS. También puede usar Visual Studio Code, que se ejecuta en macOS, Linux y Windows. Visual Studio Code es compatible con .NET Core, incluidos IntelliSense y la depuración. La mayoría de los editores de terceros, como Sublime, Emacs y VI, funcionan con .NET Core. Estos editores de terceros obtienen el editor de IntelliSense mediante [Omnisharp](https://www.omnisharp.net/). También puede evitar el uso de un editor de código y usar directamente la [CLI de .NET Core](../core/tools/index.md), disponibles para todas las plataformas compatibles.

### <a name="microservices-architecture"></a>Arquitectura de microservicios

Una arquitectura de microservicios permite una combinación de tecnologías en un límite de servicio. Esta combinación de tecnología permite un adopción gradual de .NET Core para microservicios nuevos que funcionan con otros servicios o microservicios. Por ejemplo, puede combinar microservicios o servicios desarrollados con .NET Framework, Java, Ruby u otras tecnologías monolíticas.

Existen muchas plataformas de infraestructura. [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) está diseñada para sistemas de microservicios grandes y complejos. [Azure App Service](https://azure.microsoft.com/services/app-service/) es una buena elección para microservicios sin estado. Los microservicios alternativos basados en Docker encajan en cualquier enfoque de microservicios, como se explica en la sección [Contenedores](#containers). Todas estas plataformas admiten .NET Core, lo que hace que resulten perfectas para hospedar sus microservicios.

Para obtener más información sobre la arquitectura de microservicios, consulte [.NET Microservices. Architecture for Containerized .NET Applications](../architecture/microservices/index.md) (Microservicios de .NET: Arquitectura para aplicaciones .NET en contenedor).

### <a name="containers"></a>Contenedores

Los contenedores se usan normalmente junto con una arquitectura de microservicios. Los contenedores también se pueden usar para incluir las aplicaciones web o los servicios en contenedores que sigan cualquier patrón de arquitectura. .NET Framework se puede usar en contenedores de Windows, la modularidad y ligereza de .NET Core la convierten en una mejor elección para los contenedores. Al crear e implementar un contenedor, el tamaño de su imagen es mucho más pequeño con .NET Core que con .NET Framework. Como es multiplataforma, puede implementar aplicaciones de servidor en contenedores de Docker de Linux, por ejemplo.

Los contenedores de Docker pueden hospedarse en su propia infraestructura de Linux o Windows, o en un servicio en la nube como [Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/). Azure Kubernetes Service puede administrar, organizar y escalar aplicaciones basadas en contenedores en la nube.

### <a name="high-performance-and-scalable-systems"></a>Sistemas escalables y de alto rendimiento

Cuando el sistema necesite el mejor rendimiento y escalabilidad posible, .NET Core y ASP.NET Core son sus mejores opciones. El entorno de ejecución de servidor de alto rendimiento para Windows Server y Linux convierte .NET en un marco web de gran rendimiento en los bancos de pruebas de [TechEmpower](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext).

El rendimiento y la escalabilidad son especialmente importantes para las arquitecturas de microservicios, donde podrían ejecutarse cientos de microservicios. Con ASP.NET Core, los sistemas se ejecutan con un número mucho menor de servidores/máquinas virtuales. Al usar menos servidores/máquinas virtuales, se ahorran costos de infraestructura y hospedaje.

### <a name="side-by-side-net-versions-per-application-level"></a>Versiones de .NET en paralelo por nivel de aplicación

Para instalar aplicaciones con dependencias en diferentes versiones de .NET, se recomienda .NET Core. .NET Core admite la instalación en paralelo de diferentes versiones del entorno de ejecución .NET Core en la misma máquina. Esta instalación en paralelo permite varios servicios en el mismo servidor, cada uno de ellos en su propia versión de .NET Core. También reduce los riesgos y ahorra dinero en las operaciones de TI y las actualizaciones de aplicaciones.

La instalación en paralelo no es posible con .NET Framework. Se trata de un componente de Windows, y solo puede existir una versión en una máquina a la vez. Cada versión de .NET Framework reemplaza la anterior. Si instala una aplicación nueva que tenga como destino una versión posterior de .NET Framework, es posible que se interrumpan las aplicaciones existentes que se ejecutan en la máquina, ya que se ha reemplazado la versión anterior.

## <a name="when-to-choose-net-framework"></a>Cuándo elegir .NET Framework

.NET Core ofrece ventajas significativas para las aplicaciones nuevas y los patrones de aplicación. Sin embargo, .NET Framework sigue siendo la opción natural para muchos escenarios existentes y, por tanto, no se reemplaza por .NET Core para todas las aplicaciones de servidor.

### <a name="current-net-framework-applications"></a>Aplicaciones actuales de .NET Framework

En la mayoría de los casos, no necesita migrar sus aplicaciones existentes a .NET Core. En su lugar, un enfoque recomendado es usar .NET Core al extender una aplicación existente, como escribir un nuevo servicio web en ASP.NET Core.

### <a name="aspnet-core-on-net-framework"></a>ASP.NET Core en .NET Framework

Para obtener información sobre la compatibilidad de ASP.NET Core en .NET Framework, vea la página sobre la [directiva de compatibilidad de .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

### <a name="third-party-libraries-or-nuget-packages-not-available-for-net-core"></a>Bibliotecas de terceros o paquetes NuGet no disponibles para .NET Core

Las bibliotecas están adoptando rápidamente .NET Standard. .NET Standard permite compartir código entre todas las implementaciones de .NET, incluido .NET Core. Con .NET Standard 2.0, esto es incluso más fácil:

- La superficie de API es mucho más grande.
- Presentó un modo de compatibilidad de .NET Framework.

  Este modo de compatibilidad permite que los proyectos de .NET Standard y .NET Core hagan referencia a bibliotecas de .NET Framework. Para obtener más información sobre el modo de compatibilidad, vea [Announcing .NET Standard 2.0](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-0/) (Anuncio de .NET Standard 2.0).

Se debe usar .NET Framework solo en los casos en los que las bibliotecas o paquetes NuGet usen tecnologías que no estén disponibles en .NET Standard o .NET Core.

### <a name="net-technologies-not-available-for-net-core"></a>Tecnologías de .NET no disponibles para .NET Core

Algunas tecnologías de .NET Framework no están disponibles en .NET Core. Algunas de ellas puede que estén disponibles en versiones posteriores de .NET Core. Otras no se aplican a los nuevos patrones de aplicaciones a los que se dirige .NET Core y puede que nunca estén disponibles. En la siguiente lista, se muestran las tecnologías más comunes que no se encuentran en .NET Core:

- Aplicaciones de formularios Web Forms ASP.NET: ASP.NET Web Forms solo está disponible en .NET Framework. No se puede usar ASP.NET Core para ASP.NET Web Forms. No está previsto migrar ASP.NET Web Forms a .NET Core.

- Aplicaciones de ASP.NET Web Pages: ASP.NET Web Pages no se incluye en ASP.NET Core.

- Implementación de servicios WCF. Aunque hay una [biblioteca cliente de WCF](https://github.com/dotnet/wcf) para consumir servicios WCF desde .NET Core, actualmente la implementación del servidor WCF solo está disponible en .NET Framework. Este escenario no forma parte del plan actual de .NET Core, pero se está valorando para el futuro.

- Servicios relacionados con flujos de trabajo: Windows Workflow Foundation (WF), Workflow Services (WCF y WF en un único servicio) y WCF Data Services (antes conocido como "ADO.NET Data Services") solo están disponibles en .NET Framework. No está previsto incorporar estas tecnologías a .NET Core.

- Compatibilidad con lenguajes: Visual Basic y F# se admiten actualmente en .NET Core, pero no para todos los tipos de proyecto. Para obtener una lista de plantillas de proyecto compatibles, consulte [Opciones de plantilla para dotnet new](../core/tools/dotnet-new.md#arguments).

### <a name="platform-doesnt-support-net-core"></a>Plataforma no compatible con .NET Core

Algunas plataformas de terceros o de Microsoft no son compatibles con .NET Core. Algunos servicios de Azure proporcionan un SDK que aún no está disponible para su consumo en .NET Core. Esta es una circunstancia transitoria, dado que todos los servicios de Azure usan .NET Core. Mientras tanto, puede usar la API REST equivalente en lugar del SDK de cliente.

## <a name="see-also"></a>Vea también

- [Elegir entre ASP.NET y ASP.NET Core](/aspnet/core/choose-aspnet-framework)
- [ASP.NET Core con .NET Framework como destino](/aspnet/core/introduction-to-aspnet-core#aspnet-core-targeting-net-framework)
- [Marcos de trabajo de destino](frameworks.md)
- [Introducción a .NET Core](../core/introduction.md)
- [Portabilidad de .NET Framework a .NET Core](../core/porting/index.md)
- [Introducción a .NET y Docker](../core/docker/introduction.md)
- [Introducción a los componentes de .NET](components.md)
- [Microservicios de .NET: Arquitectura para aplicaciones .NET en contenedor](../architecture/microservices/index.md)

---
title: Compatibilidad con valores altos de PPP
description: Obtenga más información sobre la compatibilidad en Windows Forms para escenarios altos de PPP y PPP dinámicos comunes. También aprenderá a configurar aplicaciones de Windows Forms para la compatibilidad con alta resolución de PPP.
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
ms.openlocfilehash: a9e0766307095da447c772de5a3065c18b7b7154
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325646"
---
# <a name="high-dpi-support-in-windows-forms"></a><span data-ttu-id="606d0-104">Compatibilidad con PPP alta en Windows Forms</span><span class="sxs-lookup"><span data-stu-id="606d0-104">High DPI support in Windows Forms</span></span>

<span data-ttu-id="606d0-105">A partir de la .NET Framework 4,7, Windows Forms incluye mejoras en los escenarios comunes de PPP alto y dinámicos.</span><span class="sxs-lookup"><span data-stu-id="606d0-105">Starting with the .NET Framework 4.7, Windows Forms includes enhancements for common high DPI and dynamic DPI scenarios.</span></span> <span data-ttu-id="606d0-106">Entre ellas se incluyen las siguientes:</span><span class="sxs-lookup"><span data-stu-id="606d0-106">These include:</span></span>

- <span data-ttu-id="606d0-107">Mejoras en el ajuste de escala y diseño de varios controles Windows Forms, como el <xref:System.Windows.Forms.MonthCalendar> control y el <xref:System.Windows.Forms.CheckedListBox> control.</span><span class="sxs-lookup"><span data-stu-id="606d0-107">Improvements in the scaling and layout of a number of Windows Forms controls, such as the <xref:System.Windows.Forms.MonthCalendar> control and the <xref:System.Windows.Forms.CheckedListBox> control.</span></span>

- <span data-ttu-id="606d0-108">Ajuste de escala de un solo paso.</span><span class="sxs-lookup"><span data-stu-id="606d0-108">Single-pass scaling.</span></span>  <span data-ttu-id="606d0-109">En el .NET Framework 4,6 y versiones anteriores, el escalado se realizaba a través de varias fases, lo que hacía que algunos controles se escalaran más de lo necesario.</span><span class="sxs-lookup"><span data-stu-id="606d0-109">In the .NET Framework 4.6 and earlier versions, scaling was performed through multiple passes, which caused some controls to be scaled more than was necessary.</span></span>

- <span data-ttu-id="606d0-110">Compatibilidad con escenarios de PPP dinámicos en los que el usuario cambia los PPP o el factor de escala una vez que se ha iniciado una aplicación Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="606d0-110">Support for dynamic DPI scenarios in which the user changes the DPI or scale factor after a Windows Forms application has been launched.</span></span>

<span data-ttu-id="606d0-111">En las versiones de la .NET Framework a partir del .NET Framework 4,7, la compatibilidad mejorada con PPP alta es una característica opcional.</span><span class="sxs-lookup"><span data-stu-id="606d0-111">In versions of the .NET Framework starting with the .NET Framework 4.7, enhanced high DPI support is an opt-in feature.</span></span> <span data-ttu-id="606d0-112">Debe configurar la aplicación para aprovecharla.</span><span class="sxs-lookup"><span data-stu-id="606d0-112">You must configure your application to take advantage of it.</span></span>

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a><span data-ttu-id="606d0-113">Configuración de la aplicación de Windows Forms para la compatibilidad con alta resolución de PPP</span><span class="sxs-lookup"><span data-stu-id="606d0-113">Configuring your Windows Forms app for high DPI support</span></span>

<span data-ttu-id="606d0-114">Las nuevas características Windows Forms que admiten el reconocimiento de PPP alto solo están disponibles en las aplicaciones que tienen como destino el .NET Framework 4,7 y que se ejecutan en sistemas operativos Windows a partir de Windows 10 Creators Update.</span><span class="sxs-lookup"><span data-stu-id="606d0-114">The new Windows Forms features that support high DPI awareness are available only in applications that target the .NET Framework 4.7 and are running on Windows operating systems starting with the Windows 10 Creators Update.</span></span>

<span data-ttu-id="606d0-115">Además, para configurar la compatibilidad con alta PPP en la aplicación Windows Forms, debe hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="606d0-115">In addition, to configure high DPI support in your Windows Forms application, you must do the following:</span></span>

- <span data-ttu-id="606d0-116">Declare la compatibilidad con Windows 10.</span><span class="sxs-lookup"><span data-stu-id="606d0-116">Declare compatibility with Windows 10.</span></span>

  <span data-ttu-id="606d0-117">Para ello, agregue lo siguiente al archivo de manifiesto:</span><span class="sxs-lookup"><span data-stu-id="606d0-117">To do this, add the following to your manifest file:</span></span>

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- <span data-ttu-id="606d0-118">Habilite el reconocimiento de PPP por monitor en el archivo de *app.config* .</span><span class="sxs-lookup"><span data-stu-id="606d0-118">Enable per-monitor DPI awareness in the *app.config* file.</span></span>

  <span data-ttu-id="606d0-119">Windows Forms introduce un nuevo [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) elemento para admitir nuevas características y personalizaciones agregadas a partir del .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="606d0-119">Windows Forms introduces a new [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) element to support new features and customizations added starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="606d0-120">Agregue lo siguiente al archivo de configuración de la aplicación para aprovechar las nuevas características que admiten un máximo de PPP.</span><span class="sxs-lookup"><span data-stu-id="606d0-120">To take advantage of the new features that support high DPI, add the following to your application configuration file.</span></span>

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>
  ```

  > [!IMPORTANT]
  > <span data-ttu-id="606d0-121">En las versiones anteriores de la .NET Framework, se usaba el manifiesto para agregar compatibilidad con PPP alta.</span><span class="sxs-lookup"><span data-stu-id="606d0-121">In previous versions of the .NET Framework, you used the manifest to add high DPI support.</span></span> <span data-ttu-id="606d0-122">Ya no se recomienda este enfoque, ya que reemplaza los valores definidos en el archivo de app.config.</span><span class="sxs-lookup"><span data-stu-id="606d0-122">This approach is no longer recommended, since it overrides settings defined on the app.config file.</span></span>

- <span data-ttu-id="606d0-123">Llame al <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> método estático.</span><span class="sxs-lookup"><span data-stu-id="606d0-123">Call the static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>

  <span data-ttu-id="606d0-124">Debe ser la primera llamada al método en el punto de entrada de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="606d0-124">This should be the first method call in your application entry point.</span></span> <span data-ttu-id="606d0-125">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="606d0-125">For example:</span></span>

  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a><span data-ttu-id="606d0-126">No participar en las características de PPP altas individuales</span><span class="sxs-lookup"><span data-stu-id="606d0-126">Opting out of individual high DPI features</span></span>

<span data-ttu-id="606d0-127">Establecer el `DpiAwareness` valor en `PerMonitorV2` habilita todas las características de reconocimiento de PPP altas compatibles con las versiones de .NET Framework a partir del .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="606d0-127">Setting the `DpiAwareness` value to `PerMonitorV2` enables all high DPI awareness features supported by .NET Framework versions starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="606d0-128">Normalmente, esto es adecuado para la mayoría de las aplicaciones Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="606d0-128">Typically, this is adequate for most Windows Forms applications.</span></span> <span data-ttu-id="606d0-129">Sin embargo, es posible que desee no participar en una o varias características individuales.</span><span class="sxs-lookup"><span data-stu-id="606d0-129">However, you may want to opt out of one or more individual features.</span></span> <span data-ttu-id="606d0-130">La razón más importante para hacerlo es que el código de aplicación existente ya controla esa característica.</span><span class="sxs-lookup"><span data-stu-id="606d0-130">The most important reason for doing this is that your existing application code already handles that feature.</span></span>  <span data-ttu-id="606d0-131">Por ejemplo, si la aplicación controla el escalado automático, puede que desee deshabilitar la característica de cambio de tamaño automático de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="606d0-131">For example, if your application handles auto scaling, you might want to disable the auto-resizing feature as follows:</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

<span data-ttu-id="606d0-132">Para obtener una lista de claves individuales y sus valores, vea [Windows Forms Agregar elemento de configuración](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span><span class="sxs-lookup"><span data-stu-id="606d0-132">For a list of individual keys and their values, see [Windows Forms Add Configuration Element](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span></span>

## <a name="new-dpi-change-events"></a><span data-ttu-id="606d0-133">Nuevos eventos de cambio de PPP</span><span class="sxs-lookup"><span data-stu-id="606d0-133">New DPI change events</span></span>

<span data-ttu-id="606d0-134">A partir de la .NET Framework 4,7, tres nuevos eventos le permiten controlar mediante programación los cambios de PPP dinámicos:</span><span class="sxs-lookup"><span data-stu-id="606d0-134">Starting with the .NET Framework 4.7, three new events allow you to programmatically handle dynamic DPI changes:</span></span>

- <span data-ttu-id="606d0-135"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, que se desencadena cuando se cambia la configuración de PPP para un control mediante programación después de que se haya producido un evento de cambio de PPP para su control o formulario primario.</span><span class="sxs-lookup"><span data-stu-id="606d0-135"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, which is fired when the DPI setting for a control is changed programmatically after a DPI change event for it's parent control or form has occurred.</span></span>
- <span data-ttu-id="606d0-136"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, que se desencadena cuando se cambia la configuración de PPP para un control mediante programación antes de que se produzca un evento de cambio de PPP para su control o formulario primario.</span><span class="sxs-lookup"><span data-stu-id="606d0-136"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, which is fired when the DPI setting for a control is changed programmatically before a DPI change event for its parent control or form has occurred.</span></span>
- <span data-ttu-id="606d0-137"><xref:System.Windows.Forms.Form.DpiChanged>, que se desencadena cuando cambia el valor de PPP en el dispositivo de pantalla donde se muestra actualmente el formulario.</span><span class="sxs-lookup"><span data-stu-id="606d0-137"><xref:System.Windows.Forms.Form.DpiChanged>, which is fired when the DPI setting changes on the display device where the form is currently displayed.</span></span>

## <a name="new-helper-methods-and-properties"></a><span data-ttu-id="606d0-138">Nuevas propiedades y métodos auxiliares</span><span class="sxs-lookup"><span data-stu-id="606d0-138">New helper methods and properties</span></span>

<span data-ttu-id="606d0-139">El .NET Framework 4,7 también agrega una serie de nuevas propiedades y métodos auxiliares que proporcionan información sobre el ajuste de escala de PPP y permiten realizar el ajuste de escala de PPP.</span><span class="sxs-lookup"><span data-stu-id="606d0-139">The .NET Framework 4.7 also adds a number of new helper methods and properties that provide information about DPI scaling and allow you to perform DPI scaling.</span></span> <span data-ttu-id="606d0-140">Entre ellas se incluyen las siguientes:</span><span class="sxs-lookup"><span data-stu-id="606d0-140">These include:</span></span>

- <span data-ttu-id="606d0-141"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, que convierte un valor de los píxeles lógicos a los de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="606d0-141"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, which converts a value from logical to device pixels.</span></span>

- <span data-ttu-id="606d0-142"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, que escala una imagen de mapa de bits al ppp lógico para un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="606d0-142"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, which scales a bitmap image to the logical DPI for a device.</span></span>

- <span data-ttu-id="606d0-143"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, que devuelve el PPP del dispositivo actual.</span><span class="sxs-lookup"><span data-stu-id="606d0-143"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, which returns the DPI for the current device.</span></span>

## <a name="versioning-considerations"></a><span data-ttu-id="606d0-144">Consideraciones sobre el control de versiones</span><span class="sxs-lookup"><span data-stu-id="606d0-144">Versioning considerations</span></span>

<span data-ttu-id="606d0-145">Además de ejecutarse en .NET Framework 4,7 y Windows 10 Creators Update, la aplicación también puede ejecutarse en un entorno en el que no sea compatible con las mejoras de PPP altas.</span><span class="sxs-lookup"><span data-stu-id="606d0-145">In addition to running on .NET Framework 4.7 and Windows 10 Creators Update, your application may also run in an environment in which it isn't compatible with high DPI improvements.</span></span> <span data-ttu-id="606d0-146">En este caso, deberá desarrollar una reserva para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="606d0-146">In this case, you'll need to develop a fallback for your application.</span></span> <span data-ttu-id="606d0-147">Puede hacer esto para realizar un [dibujo personalizado](./controls/user-drawn-controls.md) con el fin de controlar el escalado.</span><span class="sxs-lookup"><span data-stu-id="606d0-147">You can do this to perform [custom drawing](./controls/user-drawn-controls.md) to handle scaling.</span></span>

<span data-ttu-id="606d0-148">Para ello, también debe determinar el sistema operativo en el que se ejecuta la aplicación.</span><span class="sxs-lookup"><span data-stu-id="606d0-148">To do this, you also need to determine the operating system on which your app is running.</span></span> <span data-ttu-id="606d0-149">Puede hacerlo con código como el siguiente:</span><span class="sxs-lookup"><span data-stu-id="606d0-149">You can do that with code like the following:</span></span>

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

<span data-ttu-id="606d0-150">Tenga en cuenta que la aplicación no detectará correctamente Windows 10 si no aparece como un sistema operativo compatible en el manifiesto de aplicación.</span><span class="sxs-lookup"><span data-stu-id="606d0-150">Note that your application won't successfully detect Windows 10 if it wasn't listed as a supported operating system in the application manifest.</span></span>

<span data-ttu-id="606d0-151">También puede comprobar la versión de la .NET Framework en la que se compiló la aplicación:</span><span class="sxs-lookup"><span data-stu-id="606d0-151">You can also check the version of the .NET Framework that the application was built against:</span></span>

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a><span data-ttu-id="606d0-152">Vea también</span><span class="sxs-lookup"><span data-stu-id="606d0-152">See also</span></span>

- [<span data-ttu-id="606d0-153">Windows Forms Agregar elemento de configuración</span><span class="sxs-lookup"><span data-stu-id="606d0-153">Windows Forms Add Configuration Element</span></span>](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [<span data-ttu-id="606d0-154">Ajustar el tamaño y la escala de los formularios Windows Forms</span><span class="sxs-lookup"><span data-stu-id="606d0-154">Adjusting the Size and Scale of Windows Forms</span></span>](adjusting-the-size-and-scale-of-windows-forms.md)

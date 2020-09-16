---
title: Seguimiento de SQL
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 916c04b03dee296b7e6f5c792f0c4e50fb4203c0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559355"
---
# <a name="sql-tracking"></a><span data-ttu-id="f6472-102">Seguimiento de SQL</span><span class="sxs-lookup"><span data-stu-id="f6472-102">SQL tracking</span></span>

<span data-ttu-id="f6472-103">Este ejemplo muestra cómo escribir un participante de seguimiento SQL personalizado que escribe registros de seguimiento en una base de datos SQL.</span><span class="sxs-lookup"><span data-stu-id="f6472-103">This sample demonstrates how to write a custom SQL tracking participant that writes tracking records to a SQL database.</span></span> <span data-ttu-id="f6472-104">Windows Workflow Foundation (WF) proporciona seguimiento de flujo de trabajo para obtener visibilidad de la ejecución de una instancia de flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="f6472-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="f6472-105">El tiempo de ejecución de seguimiento emite registros de seguimiento de flujo de trabajo durante la ejecución del flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="f6472-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="f6472-106">Para obtener más información sobre el seguimiento del flujo de trabajo, vea [seguimiento y](../workflow-tracking-and-tracing.md)seguimiento del flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="f6472-106">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

## <a name="use-the-sample"></a><span data-ttu-id="f6472-107">Usar el ejemplo</span><span class="sxs-lookup"><span data-stu-id="f6472-107">Use the sample</span></span>

1. <span data-ttu-id="f6472-108">Compruebe que tiene instalado SQL Server 2008, SQL Server 2008 Express o una versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="f6472-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="f6472-109">Los scripts empaquetados con el ejemplo dan por supuesto el uso de una instancia de SQL Express en su equipo local.</span><span class="sxs-lookup"><span data-stu-id="f6472-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="f6472-110">Si tiene una instancia diferente, modifique los scripts de base de datos antes de ejecutar el ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f6472-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2. <span data-ttu-id="f6472-111">Cree la base de datos de seguimiento de SQL Server ejecutando Trackingsetup.cmd en el directorio de scripts (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span><span class="sxs-lookup"><span data-stu-id="f6472-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="f6472-112">De esta forma, se creará una base de datos denominada TrackingSample.</span><span class="sxs-lookup"><span data-stu-id="f6472-112">This creates a database called TrackingSample.</span></span>

   > [!NOTE]
   > <span data-ttu-id="f6472-113">El script crea la base de datos en la instancia predeterminada de SQL Express.</span><span class="sxs-lookup"><span data-stu-id="f6472-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="f6472-114">Si desea realizar la instalación en una instancia de base de datos diferente, modifique el script Trackingsetup.cmd.</span><span class="sxs-lookup"><span data-stu-id="f6472-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>

3. <span data-ttu-id="f6472-115">Abra SqlTrackingSample. sln en Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="f6472-115">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>

4. <span data-ttu-id="f6472-116">Presione **Ctrl** + **MAYÚS** + **B** para compilar la solución.</span><span class="sxs-lookup"><span data-stu-id="f6472-116">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

5. <span data-ttu-id="f6472-117">Presione **F5** para ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f6472-117">Press **F5** to run the application.</span></span>

   <span data-ttu-id="f6472-118">La ventana del explorador se abre y muestra la lista de directorios de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f6472-118">The browser window opens and shows the directory listing for the application.</span></span>

6. <span data-ttu-id="f6472-119">En el explorador, haga clic en StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="f6472-119">In the browser, click StockPriceService.xamlx.</span></span>

7. <span data-ttu-id="f6472-120">El explorador muestra la página StockPriceService, que contiene la dirección WSDL de servicio local.</span><span class="sxs-lookup"><span data-stu-id="f6472-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="f6472-121">Copie esta dirección.</span><span class="sxs-lookup"><span data-stu-id="f6472-121">Copy this address.</span></span>

   <span data-ttu-id="f6472-122">Un ejemplo de la dirección WSDL de servicio local es `http://localhost:65193/StockPriceService.xamlx?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="f6472-122">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>

8. <span data-ttu-id="f6472-123">Con el explorador de archivos, ejecute el cliente de prueba WCF (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="f6472-123">Using File Explorer, run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="f6472-124">Se encuentra en el *directorio Microsoft Visual Studio 10.0 \ Common7\IDE*</span><span class="sxs-lookup"><span data-stu-id="f6472-124">It's located in the *Microsoft Visual Studio 10.0\Common7\IDE directory*.</span></span>

9. <span data-ttu-id="f6472-125">En el cliente de prueba WCF, haga clic en el menú **archivo** y seleccione **Agregar servicio**.</span><span class="sxs-lookup"><span data-stu-id="f6472-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="f6472-126">Pegue la dirección del servicio local en el cuadro de texto.</span><span class="sxs-lookup"><span data-stu-id="f6472-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="f6472-127">Haga clic en **Aceptar** para cerrar el cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="f6472-127">Click **OK** to close the dialog.</span></span>

10. <span data-ttu-id="f6472-128">En el cliente de prueba WCF, haga doble clic en **GetStockPrice**.</span><span class="sxs-lookup"><span data-stu-id="f6472-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="f6472-129">Se abrirá la `GetStockPrice` operación que toma un parámetro, se escribe en el valor `Contoso` y se hace clic en **invocar**.</span><span class="sxs-lookup"><span data-stu-id="f6472-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>

11. <span data-ttu-id="f6472-130">Los registros de seguimiento emitidos se escriben en una base de datos SQL.</span><span class="sxs-lookup"><span data-stu-id="f6472-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="f6472-131">Para ver los registros de seguimiento, abra la base de datos TrackingSample en SQL Management Studio y navegue hasta las tablas.</span><span class="sxs-lookup"><span data-stu-id="f6472-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="f6472-132">La ejecución de una consulta de selección en las tablas muestra los datos dentro de los registros de seguimiento almacenados en las tablas respectivas.</span><span class="sxs-lookup"><span data-stu-id="f6472-132">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>

   <span data-ttu-id="f6472-133">Para obtener más información acerca de SQL Server Management Studio, consulte [introducing SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span><span class="sxs-lookup"><span data-stu-id="f6472-133">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span></span> <span data-ttu-id="f6472-134">Descargue SQL Server Management Studio [aquí](https://aka.ms/ssmsfullsetup).</span><span class="sxs-lookup"><span data-stu-id="f6472-134">Download SQL Server Management Studio [here](https://aka.ms/ssmsfullsetup).</span></span>

## <a name="uninstall-the-sample"></a><span data-ttu-id="f6472-135">Desinstalar el ejemplo</span><span class="sxs-lookup"><span data-stu-id="f6472-135">Uninstall the sample</span></span>

1. <span data-ttu-id="f6472-136">Ejecute el script Trackingcleanup. cmd en el directorio de ejemplo (*\WF\Basic\Tracking\SqlTracking*).</span><span class="sxs-lookup"><span data-stu-id="f6472-136">Run theTrackingcleanup.cmd script in the sample directory (*\WF\Basic\Tracking\SqlTracking*).</span></span>

    > [!NOTE]
    > <span data-ttu-id="f6472-137">Trackingcleanup.cmd intenta eliminar la base de datos en el SQL Express del equipo local.</span><span class="sxs-lookup"><span data-stu-id="f6472-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="f6472-138">Si está utilizando otra instancia del servidor SQL, modifique Trackingcleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="f6472-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f6472-139">Puede que los ejemplos ya estén instalados en su equipo.</span><span class="sxs-lookup"><span data-stu-id="f6472-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f6472-140">Compruebe el siguiente directorio (predeterminado) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f6472-140">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="f6472-141">Si este directorio no existe, vaya a [ejemplos de Windows Communication Foundation (WCF) y Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos.</span><span class="sxs-lookup"><span data-stu-id="f6472-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f6472-142">Este ejemplo se encuentra en el siguiente directorio.</span><span class="sxs-lookup"><span data-stu-id="f6472-142">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a><span data-ttu-id="f6472-143">Vea también</span><span class="sxs-lookup"><span data-stu-id="f6472-143">See also</span></span>

- <span data-ttu-id="f6472-144">[Ejemplos de supervisión de AppFabric](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f6472-144">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>

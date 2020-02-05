---
title: 'Lección 8: Crear un filtro de datos | Microsoft Docs'
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 19ccbdba-e3da-40a4-b652-32c628cf32e5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 991610dacf7a13a467a3058f2bdbcfcc454ee71e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2020
ms.locfileid: "62512397"
---
# <a name="lesson-8-create-a-data-filter"></a>Lección 8: Crear un filtro de datos
Después de agregar una acción de obtención de detalles en el informe primario, el paso siguiente consiste en crear un filtro de los datos de la tabla de datos que definió para el informe secundario.  
  
Puede crear un filtro basado en una tabla **o** un filtro de consulta para el informe de obtención de detalles. Esta lección proporciona instrucciones para ambas opciones.  
  
## <a name="table-based-filter"></a>Filtro basado en una tabla  
Debe completar las tareas siguientes para implementar un filtro basado en una tabla.  
  
-   Agregue una expresión de filtro al Tablix en el informe secundario.  
  
-   Cree una función que seleccione datos sin filtrar de la tabla **PurchaseOrderDetail** .  
  
-   Agregue un controlador de eventos que enlace el DataTable **PurchaseOrderDetail** al informe secundario.  
  
### <a name="to-add-a-filter-expression-to-the-tablix-in-the-child-report"></a>Para agregar una expresión de filtro al Tablix en el informe secundario  
  
1.  Abra el informe secundario.  
  
2.  Seleccione un encabezado de columna de la Tablix, haga clic con el botón derecho en la celda atenuada que aparece en el encabezado de columna y, después, seleccione **Propiedades de Tablix**.  
  
3.  Seleccione en la página **Filtros** y, después, seleccione **Agregar**.  
  
4.  En el campo **Expresión** , seleccione **ProductID** de la lista desplegable. Es la columna a la que se aplica el filtro.  
  
5.  Seleccione el operador igual ( **=** ) en la lista desplegable **Operador** .  
  
6.  Seleccione el botón de expresión junto al campo **Valor** , seleccione **Parámetros** en el área **Categoría** y, después, haga doble clic en **productid** en el área **Valores** . El campo **Establecer expresión para: Valor** ahora debe contener una expresión similar a **=Parameters!productid.Value**.  
  
7.  Seleccione **Aceptar** y de nuevo **Aceptar** en el cuadro de diálogo **Propiedades de Tablix** .  
  
8.  Guarde el archivo .rdlc.  
  
### <a name="to-create-a-function-that-selects-unfiltered-data-from-the-purchaseordedetail-table"></a>Para crear una función que seleccione datos sin filtrar de la tabla PurchaseOrdeDetail.  
  
1.  En el Explorador de soluciones, expanda Default.aspx y haga doble clic en Default.aspx.cs.  
  
2.  Cree una nueva función que acepte un parámetro, **productid**, de tipo Integer, y devuelva un objeto **datatable** y haga lo siguiente.  
  
    1.  Crea una instancia del conjunto de datos, **DataSet2**, que se ha creado en el paso 2 de la [Lección 4: Definir una conexión de datos y una tabla de datos para el informe secundario](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md).  
  
    2.  Cree una conexión a la base de datos de SQL Server para ejecutar la consulta definida en la **Lección 4: Definir una conexión de datos y una tabla de datos para el informe secundario**.  
  
    3.  La consulta devolverá datos sin filtrar.  
  
    4.  Rellene la instancia DataSet con los datos sin filtrar ejecutando la consulta.  
  
    5.  Devolver el DataTable **PurchaseOrderDetail** .  
  
        La función será similar a la siguiente. (Esto es solo para la referencia. Puede seguir cualquier modelo que desee, para capturar los datos necesarios para el informe secundario).  
  
        ```  
        /// <summary>  
            /// Function to query PurchaseOrderDetail table, fetch the  
            /// unfiltered data and bind it with the Child report  
            /// </summary>  
            /// <returns>A dataTable of type PurchaseOrderDetail</returns>  
            private DataTable GetPurchaseOrderDetail()  
            {  
                try  
                {  
                    //Create the instance for the typed dataset, DataSet2 which will   
                    //hold the [PurchaseOrderDetail] table details.  
                    //The dataset was created as part of the tutorial in Step 4.  
                    DataSet2 ds = new DataSet2();  
  
                    //Create a SQL Connection to the AdventureWorks2008 database using Windows Authentication.  
                    using (SqlConnection sqlconn = new SqlConnection("Data Source=.;Initial Catalog=Adventureworks2014;Integrated Security=SSPI"))  
                    {  
                        //Building the dynamic query with the parameter ProductID.  
                        SqlDataAdapter adap = new SqlDataAdapter("SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail ", sqlconn);  
                        //Executing the QUERY and fill the dataset with the PurchaseOrderDetail table data.  
                        adap.Fill(ds, "PurchaseOrderDetail");  
                    }  
  
                    //Return the PurchaseOrderDetail table for the Report Data Source.  
                    return ds.PurchaseOrderDetail;  
                }  
                catch  
                {  
                    throw;  
                }  
            }  
        ```  
  
### <a name="to-add-an-event-handler-that-binds-the-purchaseorderdetail-datatable-to-the-child-report"></a>Para agregar un controlador de eventos que enlaza el DataTable PurchaseOrderDetail al informe secundario.  
  
1.  Abra el archivo Default.aspx en la vista del diseñador.  
  
2.  Haga clic con el botón derecho en el control ReportViewer y, después, seleccione **Propiedades**.  
  
3.  En la página **Propiedades** , seleccione el icono **Eventos** .  
  
4.  Haga doble clic en el evento **Obtención de detalles** .  
  
    De este modo agregará una sección del controlador de eventos en el código, que será similar al bloque siguiente.  
  
    ```  
    protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
    {  
    }  
    ```  
  
5.  Complete el controlador de eventos. Debe incluir la funcionalidad siguiente.  
  
    1.  Capture la referencia al objeto de informe secundario del parámetro *DrillthroughEventArgs* .  
  
    2.  Llame a la función **GetPurchaseOrderDetail**.  
  
    3.  Enlace el DataTable **PurchaseOrderDetail** con el origen de datos correspondiente del informe.  
  
        El código de controlador de eventos completo será similar al siguiente.  
  
        ```  
        protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
            {  
                try  
                {  
                     //Get the instance of the Target report.  
                    LocalReport report = (LocalReport)e.Report;  
  
                     //Binding the DataTable to the Child report dataset.  
                    //The name DataSet1 which can be located from,   
                    //Go to Design view of Child.rdlc, Click View menu -> Report Data  
                    //You'll see this name under DataSet2.  
                    report.DataSources.Add(new ReportDataSource("DataSet1", GetPurchaseOrderDetail()));  
                }  
                catch (Exception ex)  
                {  
                    Response.Write(ex.Message);  
                }  
            }  
        ```  
  
6.  Guarde el archivo.  
  
## <a name="query-filter"></a>Filtro de consulta  
Debe completar las tareas siguientes para implementar un filtro de consulta.  
  
-   Cree una función que seleccione datos filtrados de la tabla **PurchaseOrderDetail** .  
  
-   Agregue un controlador de eventos que recupere los valores de los parámetros y enlace el DataTable **PurchaseOrdeDetail** al informe secundario.  
  
### <a name="to-create-a-function-that-selects-filtered-data-from-the-purchaseorderdetail-table"></a>Para crear una función que seleccione datos filtrados de la tabla PurchaseOrderDetail.  
  
1.  En el Explorador de soluciones, expanda Default.aspx y haga doble clic en Default.aspx.cs.  
  
2.  Cree una nueva función que acepte un parámetro, **productid**, de tipo Integer, devuelva un objeto **datatable** y haga lo siguiente.  
  
    1.  Crea una instancia del conjunto de datos, **DataSet2**, que se ha creado en el paso 2 de la [Lección 4: Definir una conexión de datos y una tabla de datos para el informe secundario](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md).  
  
    2.  Cree una conexión a la base de datos de SQL Server para ejecutar la consulta definida en la **Lección 4: Definir una conexión de datos y una tabla de datos para el informe secundario**.  
  
    3.  La consulta incluirá un parámetro, **productid**, para asegurarse de que los datos devueltos se filtran en función del **ProductID** seleccionado en el informe primario.  
  
    4.  Rellene la instancia DataSet con los datos filtrados ejecutando la consulta.  
  
    5.  Devolver el DataTable **PurchaseOrderDetail** .  
  
        La función será similar a la siguiente. (Esto es solo para la referencia. Puede seguir cualquier modelo que desee, para capturar los datos necesarios para el informe secundario).  
  
        ```  
        /// <summary>  
            /// Function to query PurchaseOrderDetail table and filter the  
            /// data for a specific ProductID selected in the Parent report.  
            /// </summary>  
            /// <param name="productid">Parameter passed from the Parent report to filter data.</param>  
            /// <returns>A dataTable of type PurchaseOrderDetail</returns>  
            private DataTable GetPurchaseOrderDetail(int productid)  
            {  
                try  
                {  
                    //Create the instance for the typed dataset, DataSet2 which will   
                    //hold the [PurchaseOrderDetail] table details.  
                    //The dataset was created as part of the tutorial in Step 4.  
                    DataSet2 ds = new DataSet2();  
  
                    //Create a SQL Connection to the AdventureWorks2008 database using Windows Authentication.  
                    using (SqlConnection sqlconn = new SqlConnection("Data Source=.;Initial Catalog=Adventureworks2014;Integrated Security=SSPI"))  
                    {  
                        //Building the dynamic query with the parameter ProductID.  
                        SqlCommand cmd = new SqlCommand("SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail where ProductID = @ProductID", sqlconn);  
                  
                        // Sets the productid parameter.  
                        cmd.Parameters.Add((new SqlParameter("@ProductID", SqlDbType.Int)).Value = productid);  
  
                        SqlDataAdapter adap = new SqlDataAdapter(cmd);  
                        //Executing the QUERY and fill the dataset with the PurchaseOrderDetail table data.  
                        adap.Fill(ds, "PurchaseOrderDetail");  
                    }  
  
                    //Return the PurchaseOrderDetail table for the Report Data Source.  
                    return ds.PurchaseOrderDetail;  
                }  
                catch  
                {  
                    throw;  
                }  
            }  
        ```  
  
### <a name="to-add-an-event-handler-that-retrieves-parameter-values-and-binds-the-purchaseordedetail-datatable-to-the-child-report"></a>Para agregar un controlador de eventos que recupere los valores de los parámetros y enlace el DataTable PurchaseOrdeDetail al informe secundario.  
  
1.  Abra el archivo Default.aspx en la vista del diseñador.  
  
2.  Haga clic con el botón derecho en el control ReportViewer y, después, seleccione **Propiedades**.  
  
3.  En el panel **Propiedades** , haga clic en el icono **Eventos** .  
  
4.  Haga doble clic en el evento **Obtención de detalles** .  
  
    De este modo agregará una sección del controlador de eventos en el código, que será similar a la siguiente.  
  
    ```  
    protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
    {  
    }  
    ```  
  
5.  Complete el controlador de eventos. Debe incluir la funcionalidad siguiente.  
  
    1.  Capture la referencia al objeto de informe secundario del parámetro *DrillthroughEventArgs* .  
  
    2.  Obtenga la lista de parámetros del informe secundario del objeto de informe secundario capturado.  
  
    3.  Recorra en iteración la colección de parámetros y recupere el valor del parámetro, **ProductID**, que se ha pasado desde el informe primario.  
  
    4.  Llame a la función **GetPurchaseOrderDetail**y pase el valor del parámetro **ProductID**.  
  
    5.  Enlace el DataTable **PurchaseOrderDetail** con el origen de datos correspondiente del informe.  
  
        El código de controlador de eventos completo será similar al siguiente.  
  
        ```  
        protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
            {  
                try  
                {  
                    //Variable to store the parameter value passed from the MainReport.  
                    int productid = 0;  
  
                    //Get the instance of the Target report.  
                    LocalReport report = (LocalReport)e.Report;  
  
                    //Get all the parameters passed from the main report to the target report.  
                    //OriginalParametersToDrillthrough actually returns a Generic list of   
                    //type ReportParameter.  
                    IList<ReportParameter> list = report.OriginalParametersToDrillthrough;  
  
                    //Parse through each parameters to fetch the values passed along with them.  
                    foreach (ReportParameter param in list)  
                    {  
                        //Since we know the report has only one parameter and it is not a multivalued,   
                        //we can directly fetch the first value from the Values array.  
                        productid = Convert.ToInt32(param.Values[0].ToString());  
                    }  
  
                    //Binding the DataTable to the Child report dataset.  
                    //The name DataSet1 which can be located from,   
                    //Go to Design view of Child.rdlc, Click View menu -> Report Data  
                    //You'll see this name under DataSet2.  
                    report.DataSources.Add(new ReportDataSource("DataSet1", GetPurchaseOrderDetail(productid)));  
                }  
                catch (Exception ex)  
                {  
                    Response.Write(ex.Message);  
                }  
            }  
        ```  
  
6.  Guarde el archivo.  
  
## <a name="next-task"></a>Tarea siguiente  
Ha creado correctamente un filtro de datos para la tabla de datos que definió para el informe secundario. A continuación, compilará y ejecutará la aplicación del sitio Web. Vea [Lección 9: Generar y ejecutar la aplicación](../reporting-services/lesson-9-build-and-run-the-application.md).  
  
  
  


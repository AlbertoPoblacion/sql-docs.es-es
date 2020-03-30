---
title: 'Lección 2: Modificar las propiedades del origen de datos de informe | Microsoft Docs'
ms.date: 05/23/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: c962b0ff-ce8a-4742-8262-dc730901afcf
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 466415ebd4075afd5dda83e95a498a32b50af453
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/29/2020
ms.locfileid: "62651742"
---
# <a name="lesson-2-modifying-the-report-data-source-properties"></a>Lesson 2: Modifying the Report Data Source Properties
En esta lección de [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] , usará el portal web para seleccionar un informe que se entregará a los destinatarios. La suscripción controlada por datos que va a definir distribuirá el informe **Sales Order** creado en el tutorial [Crear un informe de tabla básico &#40;Tutorial de SSRS&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md).  En los pasos siguientes, modificará la información de conexión del origen de datos que el informe utiliza para obtener los datos. Solo los informes que usan **credenciales almacenadas** para obtener acceso a un origen de datos del informe se pueden distribuir a través de una suscripción controlada por datos. Las credenciales almacenadas son necesarias para el procesamiento desatendido de informes.  
  
También modificará el conjunto de datos y el informe para usar un parámetro que filtrar el informe en `[Order]` de modo que la suscripción pueda dar como resultado diferentes instancias del informe para pedidos concretos y formatos de representación.  
  
## <a name="to-modify-the-data-source-to-use-stored-credentials"></a><a name="bkmk_modify_datasource"></a>Para modificar el origen de datos de modo que use credenciales almacenadas  
  
1.  Vaya al portal web de [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] con privilegios de administrador, por ejemplo, haga clic con el botón derecho en el icono de Internet Explorer y haga clic en **Ejecutar como administrador**.  
 
2.    Vaya a la dirección URL del portal web.  Por ejemplo:   
    `https://<server name>/reports`.  
    `https://localhost/reports`
 **Nota:** La dirección URL del *portal* web es "Reports", no la dirección URL del *servidor* de informes de "Reportserver".  
3.  Busque la carpeta que contiene el informe **Sales Orders** y, en el menú contextual del informe, haga clic en **Administrar**.  
 
 ![ssrs_tutorial_datadriven_manage_report](../reporting-services/media/ssrs-tutorial-datadriven-manage-report.png)
  
3.  Haga clic en **Orígenes de datos** en el panel izquierdo.  
  
4.  Compruebe que el **Tipo de conexión** es **Microsoft SQL Server**.  
  
5.  Compruebe que La cadena de conexión es la siguiente y que supone que la base de datos de ejemplo está en un servidor de bases de datos local:  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2014  
    ```  
  
6.  Haga clic en **Usar las siguientes credenciales**.  
  
7. En el **Tipo de credenciales**, seleccione **Nombre de usuario y contraseña de Windows**
8. Escriba su nombre de usuario (con el formato *dominio\usuario*) y la contraseña. Si no dispone de permisos para tener acceso a la base de datos AdventureWorks2014, especifique un inicio de sesión que disponga de ellos.  
    
9. Haga clic en **Probar conexión** para comprobar que puede conectarse al origen de datos.  
  
10. Haga clic en **Save**(Guardar).
11. Haga clic en **Cancelar**  
  
11. Visualice el informe para comprobar que se ejecuta con las credenciales que ha especificado. .  
  
## <a name="to-modify-the-adventureworksdataset"></a><a name="bkmk_modify_dataset"></a>Para modificar AdventureWorksDataset  
 En los pasos siguientes modificará el conjunto de datos para usar un parámetro para filtrar el conjunto de datos según un número de pedido.
1.  Abra el informe **Sales Orders** en [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]  
  
2.  Haga clic con el botón derecho en el conjunto de datos `AdventureWorksDataset` y haga clic en **Propiedades del conjunto de datos**.  
    ![ssrs_tutorial_datadriven_datasetproperties](../reporting-services/media/ssrs-tutorial-datadriven-datasetproperties.png)  
3.  Agregue la instrucción `WHERE (UPPER(SalesOrderNumber) =UPPER(@OrderNumber) or  @OrderNumber IS NULL)` antes que la instrucción `Group By` . La sintaxis de la consulta completa es la siguiente:  
  
    ```  
    SELECT soh.OrderDate AS Date, soh.SalesOrderNumber AS [Order], pps.Name AS Subcat, pp.Name AS Product, SUM(sd.OrderQty) AS Qty, SUM(sd.LineTotal)  AS LineTotal  
    FROM Sales.SalesPerson AS sp INNER JOIN  
      Sales.SalesOrderHeader AS soh ON sp.BusinessEntityID = soh.SalesPersonID INNER JOIN  
       Sales.SalesOrderDetail AS sd ON sd.SalesOrderID = soh.SalesOrderID INNER JOIN  
       Production.Product AS pp ON sd.ProductID = pp.ProductID  
    INNER JOIN  
       Production.ProductSubcategory AS pps ON pp.ProductSubcategoryID = pps.ProductSubcategoryID   
    INNER JOIN  
        Production.ProductCategory AS ppc ON ppc.ProductCategoryID = pps.ProductCategoryID  
  
    WHERE (UPPER(SalesOrderNumber) =UPPER(@OrderNumber) or  @OrderNumber IS NULL)  
  
    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name, soh.SalesPersonID  
    HAVING (ppc.Name = 'Clothing')  
    ```  
  
4.  Haga clic en **Aceptar**  
 En los pasos siguientes, agregará un parámetro al informe.  El parámetro de informe proporciona el parámetro de conjunto de datos. 
## <a name="to-add-a-report-parameter-and-republish-the-report"></a><a name="bkmk_add_reportparameter"></a>Para agregar un parámetro de informe y volver a publicarlo  
  
1.  En el panel **Datos del informe** , expanda la carpeta de parámetros y haga doble clic en el parámetro **Ordernumber** .  Se creó automáticamente como parte de los pasos anteriores cuando se agregó el parámetro al conjunto de datos. haga clic en **Nuevo** y, después, en **Parámetro...**  
 ![ssrs_tutorial_datadriven_parameter](../reporting-services/media/ssrs-tutorial-datadriven-parameter.png) 
2.  Compruebe que el **Nombre** es `OrderNumber`.  
  
3.  Compruebe que el **Inicio** es `OrderNumber`.  
  
4.  Seleccione **Permitir valor en blanco ("")** .  
  
5.  Seleccione **Permitir valor NULL**.  
  
6.  Haga clic en **OK**.  
  
7.  Haga clic en la pestaña **Vista previa** para ejecutar el informe. Observe el cuadro de entrada de parámetros en la parte superior del informe. Puede:  
  
    -   Haga clic en Ver informe para ver el informe completo sin usar un parámetro.  
  
    -   Cancele la selección de la opción **Null** y escriba un número de pedido, por ejemplo *so71949*y, después, haga clic en **Ver informe** para ver solo el único pedido del informe.  
    ![ssrs_tutorial_datadriven_reportviewer_parameter](../reporting-services/media/ssrs-tutorial-datadriven-reportviewer-parameter.png) 
 
  
## <a name="re-deploy-the-report"></a><a name="bkmk_redeploy"></a>Volver a implementar el informe  
  
1.  Volver a implementar el informe de modo que la configuración de la suscripción de la lección siguiente pueda usar los cambios efectuados en esta lección. Para obtener más información sobre las propiedades del proyecto que se usan en el tutorial de tablas, vea la sección "Para publicar el informe en el servidor de informes (opcional)" de la [Lección 6: Agregar grupos y totales &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).  
  
2.  En la barra de herramientas, haga clic en **Generar** y, a continuación, haga clic en **Tutorial de implementación**.  
  
## <a name="next-steps"></a>Pasos siguientes  
+ Configuró correctamente el informe para obtener datos usando credenciales almacenadas y los datos se pueden filtrar con un parámetro. 
+ En la siguiente lección, configurará la suscripción mediante las páginas del portal web Suscripción controlada por datos. Consulte la [Lección 3: Definir una suscripción controlada por datos](../reporting-services/lesson-3-defining-a-data-driven-subscription.md).  
  
## <a name="see-also"></a>Consulte también  
[Administrar orígenes de datos de informe](../reporting-services/report-data/manage-report-data-sources.md)  
[Especificación de información de credenciales y conexión para los orígenes de datos de informes](../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
[Crear una suscripción controlada por datos &#40;Tutorial de SSRS&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md)  
[Crear un informe de tabla básico &#40;Tutorial de SSRS&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  
  
  
  


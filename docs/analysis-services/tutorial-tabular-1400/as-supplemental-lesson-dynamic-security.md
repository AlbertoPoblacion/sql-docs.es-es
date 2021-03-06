---
title: "Lección complementaria de Analysis Services tutorial: seguridad dinámica | Documentos de Microsoft"
description: "Describe cómo usar la seguridad dinámica utilizando filtros de fila en el tutorial de Analysis Services."
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: 
author: Minewiskan
manager: kfile
editor: 
tags: 
ms.assetid: 
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: na
ms.date: 02/20/2018
ms.author: owend
ms.openlocfilehash: 4f304535ab43563b64757ccfc812498df4467762
ms.sourcegitcommit: 7ed8c61fb54e3963e451bfb7f80c6a3899d93322
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2018
---
# <a name="supplemental-lesson---dynamic-security"></a>Lección complementaria - seguridad dinámica

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

En esta lección complementaria, creará una función adicional que implemente seguridad dinámica. La seguridad dinámica proporciona seguridad de nivel de fila basada en el nombre de usuario o el identificador de inicio de sesión del usuario que ha iniciado sesión actualmente. 
  
Para implementar seguridad dinámica, agregar una tabla al modelo que contiene los nombres de usuario de los usuarios que pueden conectarse con el modelo y examinar los datos y objetos del modelo. El modelo que crea con este tutorial está en el contexto de Adventure Works; Sin embargo, para completar esta lección, debe agregar una tabla que contiene los usuarios de su propio dominio. No es necesario las contraseñas para los nombres de usuario que se agregan. Para crear una tabla de EmployeeSecurity, con una pequeña muestra de los usuarios de su propio dominio, utilice la función de pegar pegar datos de empleados desde una hoja de cálculo de Excel. En un escenario real, la tabla que contiene los nombres de usuario normalmente sería una tabla de una base de datos real como origen de datos; Por ejemplo, una tabla DimEmployee real.  
  
Para implementar seguridad dinámica, debe utilizar dos funciones DAX: [función USERNAME (DAX)](http://msdn.microsoft.com/22dddc4b-1648-4c89-8c93-f1151162b93f) y [función LOOKUPVALUE (DAX)](http://msdn.microsoft.com/73a51c4d-131c-4c33-a139-b1342d10caab). Estas funciones, aplicadas en una fórmula de filtro de columna, se definen en un nuevo rol. Mediante el uso de la función LOOKUPVALUE, la fórmula especifica un valor de la tabla EmployeeSecurity. La fórmula, a continuación, pasa el que el valor a la función de nombre de usuario, que especifica el nombre de usuario del usuario que ha iniciado sesión pertenece a este rol. El usuario puede examinar los datos especificados por los filtros de fila del rol. En este escenario, puede especificar que los empleados de ventas solo pueden examinar los datos de ventas de Internet de los territorios de ventas en el que son miembros.  
  
Las tareas que son únicas de este escenario de modelo tabular de Adventure Works, pero que no se aplicarían necesariamente en un escenario real, se identifican como tales. Cada tarea incluye información adicional que describe el propósito de la tarea.  
  
Tiempo estimado para completar esta lección: **30 minutos**  
  
## <a name="prerequisites"></a>Requisitos previos  

En este artículo de lección complementaria forma parte de un tutorial de modelado tabular, que se debe completar en orden. Antes de realizar las tareas de esta lección complementaria, debe haber completado todas las lecciones anteriores.  
  
## <a name="add-the-dimsalesterritory-table-to-the-aw-internet-sales-tabular-model-project"></a>Agregar la tabla dimSalesTerritory al proyecto de modelo tabular AW Internet Sales  

Para implementar seguridad dinámica para este escenario de Adventure Works, debe agregar dos tablas adicionales al modelo. La primera tabla que agregará es DimSalesTerritory (como Sales Territory) de la misma base de datos AdventureWorksDW. Posteriormente, se aplica un filtro de fila a la tabla SalesTerritory que define los datos concretos que puede examinar el usuario con sesión iniciada.  
  
#### <a name="to-add-the-dimsalesterritory-table"></a>Para agregar la tabla dimSalesTerritory  
  
1.  En el Explorador de modelos tabulares > **orígenes de datos**, haga clic en la conexión y, a continuación, haga clic en **importar nuevas tablas**.  

    Si aparece el cuadro de diálogo Credenciales de suplantación, escriba las credenciales de suplantación que utilizó en la lección 2: Agregar datos.
  
2.  En el navegador, seleccione la **DimSalesTerritory** de tabla y, a continuación, haga clic en **Aceptar**.    
  
3.  En el Editor de consultas, haga clic en el **DimSalesTerritory** de consulta y, a continuación, quitar **SalesTerritoryAlternateKey** columna.  
  
7.  Haga clic en **Importar**.  
  
    La nueva tabla se agrega al área de trabajo del modelo. Objetos y datos de la tabla de origen DimSalesTerritory, a continuación, se importan en el MT ventas AW.  
  
9. Después de la tabla se ha importado correctamente, haga clic en **cerrar**.  

## <a name="add-a-table-with-user-name-data"></a>Agregar una tabla con datos de nombre de usuario  

La tabla DimEmployee de la base de datos de ejemplo AdventureWorksDW contiene usuarios del dominio AdventureWorks. Los nombres de usuario no existen en su propio entorno. Debe crear una tabla en el modelo que contenga una pequeña muestra (al menos tres) de usuarios reales de su organización. A continuación, agregar estos usuarios como miembros a la nueva función. No necesita las contraseñas de los nombres de usuario de ejemplo, pero necesita nombres de usuario de Windows reales de su propio dominio.  
  
#### <a name="to-add-an-employeesecurity-table"></a>Para agregar una tabla EmployeeSecurity  
  
1.  Abra Microsoft Excel para crear una hoja de cálculo.  
  
2.  Copie la siguiente tabla, incluida la fila de encabezado, y péguela en la hoja de cálculo.  

    ```
      |EmployeeId|SalesTerritoryId|FirstName|LastName|LoginId|  
      |---------------|----------------------|--------------|-------------|------------|  
      |1|2|<user first name>|<user last name>|\<domain\username>|  
      |1|3|<user first name>|<user last name>|\<domain\username>|  
      |2|4|<user first name>|<user last name>|\<domain\username>|  
      |3|5|<user first name>|<user last name>|\<domain\username>|  
    ```

3.  Reemplace el nombre, apellido y dominio ombre de usuario con los nombres e identificadores de inicio de sesión de tres usuarios de su organización. Colocar el mismo usuario en las dos primeras filas de EmployeeId 1, que muestra este usuario pertenece a más de un territorio de ventas. Deje los campos EmployeeId y SalesTerritoryId tal como están.  
  
4.  Guarde la hoja de cálculo como **SampleEmployee**.  
  
5.  En la hoja de cálculo, seleccione todas las celdas con datos de empleados, incluidos los encabezados, a continuación, haga clic en los datos seleccionados y, a continuación, haga clic en **copia**.  
  
6.  En SSDT, haga clic en el **editar** menú y, a continuación, haga clic en **pegar**.  
  
    Si está atenuado pegar, haga clic en cualquier columna de cualquier tabla en la ventana del Diseñador de modelos e inténtelo de nuevo.  
  
7.  En el **vista previa de pegado** cuadro de diálogo **nombre de la tabla**, tipo **EmployeeSecurity**.  
  
8.  En **datos se peguen**, compruebe los datos incluyen todos los datos de usuario y los encabezados de la hoja de cálculo SampleEmployee.  
  
9. Compruebe que esté seleccionada la opción **Usar primera fila como encabezados de columna** y haga clic en **Aceptar**.  
  
    Se crea una nueva tabla denominada EmployeeSecurity con datos de empleado copiados desde la hoja de cálculo SampleEmployee.  
  
## <a name="create-relationships-between-factinternetsales-dimgeography-and-dimsalesterritory-table"></a>Crear relaciones entre la tabla FactInternetSales, DimGeography y DimSalesTerritory  

La tabla FactInternetSales y DimGeography, DimSalesTerritory todos los contienen una columna común, SalesTerritoryId. La columna SalesTerritoryId en la tabla DimSalesTerritory contiene valores con un identificador distinto para cada territorio de ventas.  
  
#### <a name="to-create-relationships-between-the-factinternetsales-dimgeography-and-the-dimsalesterritory-table"></a>Para crear relaciones entre los FactInternetSales y DimGeography, la tabla DimSalesTerritory  
  
1.  En la vista de diagrama, en la **DimGeography** de tabla, haga clic y mantenga el **SalesTerritoryId** columna, a continuación, arrastre el cursor hasta el **SalesTerritoryId** columna en el **DimSalesTerritory** de tabla y, a continuación, suelte.  
  
2.  En el **FactInternetSales** de tabla, haga clic y mantenga el **SalesTerritoryId** columna, a continuación, arrastre el cursor hasta el **SalesTerritoryId** columna en el **DimSalesTerritory** de tabla y, a continuación, suelte.  
  
    Observe que la propiedad Active de esta relación es False, lo que significa que está inactivo. La tabla FactInternetSales ya tiene otra relación activa.  
  
## <a name="hide-the-employeesecurity-table-from-client-applications"></a>Ocultar la tabla de EmployeeSecurity de las aplicaciones cliente  

En esta tarea, oculta la tabla EmployeeSecurity, evitando que aparezca en la lista de campos de la aplicación cliente. Tenga en cuenta que al ocultar una tabla no significa protegerla. Los usuarios todavía pueden consultar datos de la tabla de EmployeeSecurity si saben cómo. Para proteger los datos de la tabla EmployeeSecurity, impedían que los usuarios puedan consultar sus datos, aplicar un filtro en una tarea posterior.  
  
#### <a name="to-hide-the-employeesecurity-table-from-client-applications"></a>Para ocultar la tabla de EmployeeSecurity de las aplicaciones cliente  
  
-   En el diseñador de modelos en la vista de diagrama, haga clic con el botón derecho en el encabezado de tabla **Empleado** y, después, haga clic en **Ocultar en herramientas de cliente**.  
  
## <a name="create-a-sales-employees-by-territory-user-role"></a>Crear empleados de ventas por el rol de usuario de territorio  

En esta tarea, creará un rol de usuario. Este rol incluye un filtro de fila define qué filas de la tabla DimSalesTerritory son visibles para los usuarios. A continuación, se aplica el filtro en la dirección de la relación de uno a varios a todas las demás tablas relacionadas a DimSalesTerritory. También aplica un filtro que protege toda la tabla EmployeeSecurity de consultas por cualquier usuario que sea miembro del rol.  
  
> [!NOTE]  
> El rol de empleados de ventas por territorio que creará en esta lección solo permitirá a los miembros examinar (o consultar) los datos de ventas del territorio de ventas al que pertenezcan. Si agrega un usuario como miembro a los empleados de ventas por el rol de territorio que también existe como un miembro de un rol creado en [lección 11: crear Roles](../tutorial-tabular-1400/as-lesson-11-create-roles.md), obtendrá una combinación de permisos. Cuando un usuario es miembro de varios roles, los permisos y los filtros de fila definidos para cada uno de ellos son acumulativos. Es decir, el usuario tiene los mayores permisos determinados por la combinación de roles.  
  
#### <a name="to-create-a-sales-employees-by-territory-user-role"></a>Para crear empleados de ventas por el rol de usuario de Territorio  
  
1.  En SSDT, haga clic en el **modelo** menú y, a continuación, haga clic en **Roles**.  
  
2.  En **Administrador de roles**, haga clic en **nuevo**.  
  
    Se agrega a la lista un nuevo rol con el permiso Ninguno.  
  
3.  Haga clic en el nuevo rol y, a continuación, en la **nombre** columna, cambiar el nombre de la función para **empleados de ventas por territorio**.  
  
4.  En la columna **Permisos** , haga clic en la lista desplegable y, después, seleccione el permiso **Lectura** .  
  
5.  Haga clic en el **miembros** ficha y, a continuación, haga clic en **agregar**.  
  
6.  En el **Seleccionar usuario o grupo** cuadro de diálogo **escriba lo nombres de objeto para seleccionar**, escriba el primer nombre de usuario de ejemplo que utilizó al crear la tabla EmployeeSecurity. Haga clic en **Comprobar nombres** para comprobar que el nombre de usuario es válido y haga clic en **Aceptar**.  
  
    Repita este paso, agregando los demás nombres de usuario de ejemplo que utilizó al crear la tabla EmployeeSecurity.  
  
7.  Haga clic en el **filtros de fila** ficha.  
  
8.  Para el **EmployeeSecurity** tabla, en la **filtro DAX** columna, escriba la siguiente fórmula:  
  
    ```
      =FALSE()  
    ```
  
    Esta fórmula especifica que todas las columnas se resuelven en la condición booleana falsa. No hay columnas de la tabla EmployeeSecurity pueden ser consultadas por un miembro de los empleados de ventas por el rol de usuario de territorio.  
  
9. Para el **DimSalesTerritory** tabla, escriba la siguiente fórmula:  

    ```  
    ='Sales Territory'[Sales Territory Id]=LOOKUPVALUE('Employee Security'[Sales Territory Id], 
      'Employee Security'[Login Id], USERNAME(), 
      'Employee Security'[Sales Territory Id], 
      'Sales Territory'[Sales Territory Id]) 
    ```
  
    En esta fórmula, la función LOOKUPVALUE devuelve todos los valores de la columna DimEmployeeSecurity [SalesTerritoryId], donde el EmployeeSecurity [LoginId] es el mismo que el inicio de sesión nombre de usuario de Windows actuales y EmployeeSecurity [SalesTerritoryId] es el mismo que el DimSalesTerritory [SalesTerritoryId].  
  
    El conjunto de identificadores devuelven por LOOKUPVALUE de territorio de ventas, a continuación, se usa para restringir las filas que se muestra en la tabla DimSalesTerritory. Se muestran solo las filas donde está el SalesTerritoryID para la fila en el conjunto de identificadores devueltos por la función LOOKUPVALUE.  
  
10. En el Administrador de roles, haga clic en **Aceptar**.  
  
## <a name="test-the-sales-employees-by-territory-user-role"></a>Probar los empleados de ventas por el rol de usuario de territorio  

En esta tarea, usa la característica analizar en Excel en SSDT para probar la eficacia de los empleados de ventas por el rol de usuario de territorio. Especifique uno de los nombres de usuario que se ha agregado a la tabla EmployeeSecurity y como un miembro del rol. Este nombre de usuario, a continuación, se utiliza como el nombre de usuario efectivo en la conexión creada entre Excel y el modelo.  
  
#### <a name="to-test-the-sales-employees-by-territory-user-role"></a>Para probar los empleados de ventas por el rol de usuario de territorio  
  
1.  En SSDT, haga clic en el **modelo** menú y, a continuación, haga clic en **analizar en Excel**.  
  
2.  En el cuadro de diálogo **Analizar en Excel** , en **Especifique el nombre de usuario o rol que se va a usar al conectarse al modelo**, seleccione **Otro usuario de Windows**y, después, haga clic en **Examinar**.  
  
3.  En el **Seleccionar usuario o grupo** cuadro de diálogo **escriba el nombre de objeto a seleccionar**, escriba un nombre de usuario que se incluyen en la tabla EmployeeSecurity y, a continuación, haga clic en **comprobar nombres**.  
  
4.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Seleccionar usuario o grupo** y, después, haga clic en **Aceptar** para cerrar el cuadro de diálogo **Analizar en Excel** .  
  
    Excel se abre con un nuevo libro. Automáticamente se crea una tabla dinámica. La lista PivotTable Fields incluye la mayoría de los campos de datos disponibles en el nuevo modelo.  
  
    Tenga en cuenta que la tabla EmployeeSecurity no está visible en la lista PivotTable Fields. Hid esta tabla de las herramientas de cliente en una tarea anterior.  
  
5.  En el **campos** lista **∑ Internet Sales** (medidas), seleccione la **InternetTotalSales** medida. La medida se introduce en el **valores** campos.  
  
6.  Seleccione el **SalesTerritoryId** columna desde la **DimSalesTerritory** tabla. La columna se escribe en el **etiquetas de fila** campos.  
  
    Observe que las cifras de ventas por Internet solo aparecen para la región a la que pertenece el nombre de usuario efectivo que usó. Si selecciona otra columna, como la ciudad de la tabla DimGeography como campo de etiqueta de fila, se muestran solo las ciudades del territorio de ventas al que pertenece el usuario efectivo.  
    Este usuario no se puede examinar o consultar los datos de ventas de Internet de territorios distintos de aquel al que pertenecen. Esta restricción es debido a que el filtro de fila definida para la tabla DimSalesTerritory, de los empleados de ventas por el rol de usuario de territorio, protege los datos para todos los datos relacionados con otros territorios de ventas.  
  
## <a name="see-also"></a>Vea también  

[Función USERNAME (DAX)](https://msdn.microsoft.com/library/hh230954.aspx)  
[Función LOOKUPVALUE (DAX)](https://msdn.microsoft.com/library/gg492170.aspx)  
[Función CUSTOMDATA (DAX)](https://msdn.microsoft.com/library/hh213140.aspx)  
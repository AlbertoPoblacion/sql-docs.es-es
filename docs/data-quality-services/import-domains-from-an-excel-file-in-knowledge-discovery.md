---
title: Importar dominios desde un archivo de Excel a la detección del conocimiento | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 4d3a3940-6c2a-4dc4-90eb-86f26012c165
author: lrtoyou1223
ms.author: lle
manager: jroth
ms.openlocfilehash: 0256881ffbf3a1729c89cd3a82522fd3e684ebf6
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66776503"
---
# <a name="import-domains-from-an-excel-file-in-knowledge-discovery"></a>Importar dominios desde un archivo de Excel a la detección del conocimiento

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  En este tema se describe cómo importar uno o varios dominios desde un archivo de Excel a la actividad de detección de conocimiento de [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). El proceso de importación simplifica el proceso de generación del conocimiento, lo que permite ahorrar tiempo y esfuerzo. Permite a los usuarios que disponen de datos en un archivo de Excel o un archivo de texto crear una base de conocimiento con dichos datos. (Vea [Importar valores desde un archivo de Excel a un dominio](../data-quality-services/import-values-from-an-excel-file-into-a-domain.md) para obtener más información sobre cómo importar valores a un dominio de una base de conocimiento existente). No se admite la exportación a un archivo Excel.  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Prerequisites"></a> Requisitos previos  
 Para importar dominios desde un archivo de Excel, es necesario tener instalado Excel en el equipo en el que está instalado [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] ; también se debe haber creado un archivo de Excel con valores de dominio (vea [How the import works](#How)), así como haber creado y abierto una base de conocimiento en la que importar el dominio.  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 Debe disponer del rol dqs_kb_editor o dqs_administrator en la base de datos DQS_MAIN para poder importar dominios desde un archivo de Excel.  
  
##  <a name="Import"></a> Importar dominios desde un archivo de Excel a una base de conocimiento  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Ejecute la aplicación Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  En la página de inicio de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , siga uno de estos procedimientos:  
  
    -   Cree una nueva base de conocimiento en la que realizar la importación; para ello, haga clic en **Nueva base de conocimiento**, escriba un nombre para la base de conocimiento, seleccione **Ninguno** para **Crear base de conocimiento a partir de**, seleccione la actividad **Detección de conocimiento** y, a continuación, haga clic en **Crear**.  
  
    -   Abra una base de conocimiento existente en la que realizar la importación; para ello, haga clic en **Abrir base de conocimiento**, seleccione la base de conocimiento, seleccione **Detección de conocimiento**y, a continuación, haga clic en **Siguiente**.  
  
3.  En la página **Asignación** , seleccione **Archivo de Excel** en **Origen de datos**.  
  
4.  Haga clic en **Examinar** en la línea **Archivo de Excel** .  
  
5.  En el cuadro de diálogo **Seleccione un archivo de Excel** , desplácese a la carpeta que contiene el archivo de Excel desde el que desea realizar la importación, seleccione dicho archivo y, a continuación, haga clic en **Abrir**.  
  
6.  En la lista desplegable **Hoja de cálculo** , seleccione la hoja de cálculo del archivo de Excel desde la que desea realizar la importación.  
  
7.  Seleccione **Usar la primera fila como encabezado** si desea que la primera fila se considere como un encabezado de datos, y si desea que los valores de la primera fila se utilicen como nombres de columna. Anule la selección de **Usar la primera fila como encabezado** si desea que la primera fila se considere como un valor de datos, en cuyo caso DQS utilizará los nombres del encabezado de Excel (letras en orden alfabético) para las columnas.  
  
8.  Seleccione una columna y asígnela un dominio existente, o bien cree un nuevo dominio haciendo clic en el icono **Crear un dominio** , utilice el cuadro de diálogo **Crear un dominio** para crearlo y, a continuación, asígnelo a la columna. El tipo de datos del dominio debe coincidir con el tipo de datos de la columna. Repita el proceso para todas las columnas de la hoja de cálculo.  
  
9. Haga clic en **Siguiente**.  
  
10. En la página **Detectar** , haga clic en **Iniciar** para analizar los datos de la hoja de cálculo de Excel.  
  
    > [!NOTE]  
    >  Si abandona la página antes de que se hayan cargado los datos, el proceso de carga de archivos terminará.  
  
11. Compruebe que el análisis se ha realizado correctamente y, a continuación, haga clic en **Siguiente**.  
  
12. En la página **Administrar valores del dominio** , compruebe que aparecen los dominios correctos en la lista **Dominios** y que la tabla de dominios contiene valores.  
  
13. Haga clic en **Finalizar**y, a continuación, haga clic en **Publicar** para publicar la base de conocimiento, o en **No** para no publicarla.  
  
14. Compruebe que la base de conocimiento se ha publicado y haga clic en **Aceptar**.  
  
##  <a name="FollowUp"></a> Seguimiento: después de importar dominios desde un archivo de Excel  
 Después de importar dominios desde un archivo de Excel, puede agregar conocimiento a dichos dominios o utilizarlos en un proyecto de limpieza o de búsqueda de coincidencias, en función del contenido de los dominios. Para más información, vea [Realizar la detección de conocimiento](../data-quality-services/perform-knowledge-discovery.md), [Administrar un dominio](../data-quality-services/managing-a-domain.md), [Administrar un dominio compuesto](../data-quality-services/managing-a-composite-domain.md), [Crear una directiva de coincidencia](../data-quality-services/create-a-matching-policy.md), [Limpieza de datos](../data-quality-services/data-cleansing.md) o [Coincidencia de datos](../data-quality-services/data-matching.md).  
  
##  <a name="How"></a> How the import works  
 En la operación de importación, DQS interpreta un archivo de Excel de la manera siguiente:  
  
-   Una columna representa un dominio  
  
-   Una fila representa un registro de datos  
  
-   La primera fila puede representar los nombres de dominio o el primer valor o registro de datos, dependiendo del valor de la casilla **Usar la primera fila como encabezado** .  
  
 Se aplican las reglas siguientes a la operación de importación:  
  
-   Esta operación importa valores de dominio en una base de conocimiento. No importa reglas de dominio ni directivas de coincidencia.  
  
-   El archivo de Excel puede tener la extensión .xlsx, .xls o .csv. Es necesario tener instalado Microsoft Excel en el equipo de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] para poder importar valores de dominio o un dominio completo. Se admiten las versiones 2003 y posteriores de Excel. Si se utiliza la versión de 64 bits de Excel, solo se admitirán los archivos de Excel 2003; los archivos de Excel 2007 o 2010 no son compatibles.  
  
-   Los archivos de Excel de tipo .xlsx no se admiten en una instalación de 64 bits de Excel. Si utiliza Excel de 64 bits, guarde el archivo de hoja de cálculo como un archivo .xls.  
  
-   En los archivos .xlsx y .xls, el tipo de datos de la columna está determinado por el tipo de datos más frecuente de las ocho primeras filas. Si una celda no se ajusta a dicho tipo de datos, se le asignará un valor NULL.  
  
-   En los archivos .csv, el tipo de datos está determinado por el tipo de datos más frecuente de las ocho primeras filas.  
  
-   Los valores de una hoja de cálculo de Excel que no se ajusten a una regla de dominio se importarán como valores no válidos.  
  
-   Si el archivo de Excel no tiene el formato correcto o está dañado, la operación de importación generará un error.  
  
  

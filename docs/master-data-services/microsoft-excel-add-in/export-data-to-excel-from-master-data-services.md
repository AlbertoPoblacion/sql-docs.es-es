---
title: Exportar datos a Excel desde Master Data Services | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: microsoft-excel-add-in
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dd29389b-928c-4e50-995c-c6af27f97805
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 67b5a7bf5d2546ceb2d7f9ff3c15b3175d18112e
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2018
---
# <a name="export-data-to-excel-from-master-data-services"></a>Export Data to Excel from Master Data Services
  En el [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], debe exportar los datos del repositorio MDS para poder trabajar con ellos.  
  
 Si quiere filtrar el conjunto de datos antes de cargarlo, consulte [Filtrar los datos antes de exportar &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md) en su lugar.  
  
## <a name="prerequisites"></a>Prerequisites  
 Para realizar este procedimiento:  
  
-   Debe disponer de permiso de acceso al área funcional **Explorador** .  
  
### <a name="to-export-data-from-mds-into-excel"></a>Para exportar datos de MDS en Excel  
  
1.  Abra Excel y, en la pestaña **Datos maestros** , conéctese a un repositorio MDS. Para obtener más información, consulte [Conectarse a un repositorio MDS &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  En el panel **Explorador de datos maestros** , seleccione un modelo y una versión. La lista de entidades se rellena.  
  
    -   Si el panel **Explorador de datos maestros** no está visible, en el grupo **Conectar y cargar** , haga clic en **Mostrar explorador**.  
  
    -   Si el panel **Explorador de datos maestros** está deshabilitado, se debe a que la hoja existente ya contiene datos administrados por MDS. Para habilitar el panel, abra una nueva hoja de cálculo.  
  
3.  En el panel **Explorador de datos maestros** , en la lista de entidades, haga doble clic en la entidad que quiera cargar.  
  
    > [!NOTE]  
    >  -   Solo se carga en Excel el primer millón de miembros. Para filtrar la lista antes de la carga, en la cinta de opciones, en el grupo **Conectar y cargar** , haga clic en **Filtrar**.  
    > -   En las columnas que son listas restringidas (atributos basados en dominio), solo se cargan los 25 000 primeros valores. Puede cambiar este número en la propiedad MaximumDbaEntitySize en el archivo de excelusersettings.config ubicado en el equipo en el que está instalado Excel. Este archivo se encuentra en C:\Usuarios\\<usuario\>\AppData\Local\Microsoft\Microsoft SQL Server\130\MasterDataServices\\.  
    >   
    >      Si un atributo basado en dominio tiene un número de valores que excede el valor de la propiedad MaximumDbEntitySize, no se carga la lista de valores.  
  
    > [!NOTE]  
    >  Al cargar datos delimitados con texto mediante el complemento para Microsoft Excel con Excel de 32 bits y los valores de las propiedades **Cell Count to Load** (Recuento de celdas que se cargarán) y **Cell Count to Publish** (Recuento de celdas que se publicarán) se establecen en un máximo de 1000, se producirá un error de memoria insuficiente. Tiene que usar Excel de 64 bits para poder usar los valores máximos en **Cell Count to Load** (Recuento de celdas que se cargarán) y **Cell Count to Publish**(Recuento de celdas que se publicarán).  
  
## <a name="next-steps"></a>Next Steps  
 [Importación de datos de Excel en Master Data Services &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>Ver también  
 [Información general: Exportar datos a Excel &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Cuadro de diálogo Filtrar &#40;Complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)   
 [Información general: Importación de datos desde Excel &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  

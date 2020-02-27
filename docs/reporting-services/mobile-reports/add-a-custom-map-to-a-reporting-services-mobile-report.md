---
title: Agregar un mapa personalizado a un informe de Reporting Services móvil | Microsoft Docs
ms.date: 01/31/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: fd259b95-bb58-4eb1-a436-6aa12fc6f5f2
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9410aac6b74fbb515010517a2fe0667f3c197802
ms.sourcegitcommit: 1b0906979db5a276b222f86ea6fdbe638e6c9719
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2020
ms.locfileid: "76971407"
---
# <a name="add-a-custom-map-to-a-reporting-services-mobile-report"></a>Agregar un mapa personalizado a un informe de Reporting Services móvil
Los mapas personalizados requieren dos archivos:  
* Un archivo .SHP para geometrías de formas  
* Un archivo .DBF para metadatos  
  
Obtenga más información sobre los [Mapas personalizados en informes para dispositivos móviles de Reporting Services](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md).  
  
Almacene ambos archivos en la misma carpeta. Los nombres de los dos archivos deben coincidir (por ejemplo, canada.shp y canada.dbf). La primera columna de metadatos (archivo DBF) se usa para comparar con el valor de clave del nombre de la forma correspondiente (clave), que se usará para rellenar el mapa con datos.
  
## <a name="load-a-custom-map"></a>Cargar un mapa personalizado  
  
1. En la pestaña **Diseño**, seleccione un tipo de mapa: **Mapa término degradado**, **Mapa térmico de detención de rango** o **Mapa de burbujas**, arrástrelo a la superficie de diseño y desígnele el tamaño que desee.  
  
   ![SSMRP_MapsGallery](../../reporting-services/mobile-reports/media/ssmrp-mapsgallery.png)  
  
2. En la vista **Diseño** > panel **Propiedades visuales** > **Mapa**, seleccione **Mapa personalizado de archivo**.   
  
   ![SSMRP_SelectCustomMap](../../reporting-services/mobile-reports/media/ssmrp-selectcustommap.png)  
  
3. En el cuadro de diálogo **Abrir** , vaya a la ubicación de los archivos SHP y DBF y seleccione ambos.   
  
   ![SSMRP_SelectDBFandSHP](../../reporting-services/mobile-reports/media/ssmrp-selectdbfandshp.png)  
  
## <a name="connect-data-to-a-custom-map"></a>Conectar datos a un mapa personalizado  
Cuando agregue un mapa personalizado a su informe por primera vez, [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)] lo rellena con datos geográficos simulados.  
  
![SSMRP_MapsData](../../reporting-services/mobile-reports/media/ssmrp-mapsdata.png)  
  
Mostrar datos reales en el mapa personalizado es igual que mostrarlos en los mapas integrados. Siga los pasos que aparecen en [Mapas de informes de Reporting Services móviles](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md) para mostrar los datos.  
  
### <a name="see-also"></a>Consulte también  
- [Mapas personalizados en informes móviles de Reporting Services](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md)  
- [Mapas de informes móviles de Reporting Services](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)  
- [Create and publish mobile reports with SQL Server Mobile Report Publisher (Creación y publicación de informes móviles con el Publicador de informes de SQL Server Mobile)](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)   
  
  
  
  

---
title: Buscar Infopackage | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7c0cb7a4-cd07-44cc-85cb-eb1ad91f85fd
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 08b40a56d9a6c8bc3c3fed0940cc9afdef115a05
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2019
ms.locfileid: "58275054"
---
# <a name="look-up-infopackage"></a>Buscar InfoPackage
  Use el cuadro de diálogo **Buscar InfoPackage** para buscar un InfoPackage que se haya definido en el sistema de SAP Netweaver BW. Cuando aparezca la lista de InfoPackages, seleccione el InfoPackage que desee y el destino rellenará las opciones asociadas a los valores necesarios.  
  
 El destino de SAP BW de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW usa el cuadro de diálogo **Buscar cadena de procesos** . Para obtener más información acerca del destino de SAP BW, vea [SAP BW Destination](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  La documentación de Microsoft Connector 1.1 for SAP BW da por supuesto que se está familiarizado con el entorno SAP Netweaver BW. Para obtener más información acerca de SAP Netweaver BW, o sobre cómo configurar los objetos y los procesos de SAP Netweaver BW, vea la documentación de SAP.  
  
 **Para abrir el cuadro de diálogo Buscar InfoPackage**  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], abra el paquete de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] que contiene el destino SAP BW.  
  
2.  En la pestaña **Flujo de datos** , haga doble clic en el destino de SAP BW.  
  
3.  En **Editor de destino SAP BW**, haga clic en **Administrador de conexiones** para abrir la página **Administrador de conexiones** del editor.  
  
4.  En la página **Administrador de conexiones** , en el cuadro del grupo **InfoPackage/InfoSource** , haga clic en **Buscar** para mostrar el cuadro de diálogo **Buscar InfoPackage** .  
  
## <a name="lookup-options"></a>Opciones de búsqueda  
 En los campos de búsqueda, puede filtrar los resultados mediante el carácter comodín de asterisco (*) o mediante una cadena parcial en combinación con el carácter comodín de asterisco. Sin embargo, si deja un campo de búsqueda vacío, la operación de búsqueda solamente se corresponderá con cadenas vacías en ese campo.  
  
 **InfoPackage**  
 Escriba el nombre del InfoPackage que desea buscar o un nombre parcial con el carácter comodín de asterisco (*). O bien, use el carácter comodín de asterisco por sí solo para incluir todos los InfoPackages.  
  
 **InfoSource**  
 Escriba el nombre del InfoSource que desea buscar o un nombre parcial con el carácter comodín de asterisco (*). O bien, use el carácter comodín de asterisco por sí solo para incluir todos los InfoPackages independientemente del InfoSource.  
  
 **Sistema de origen**  
 Escriba el nombre del sistema de origen o un nombre parcial con el carácter comodín de asterisco (*). O bien, use el carácter comodín de asterisco por sí solo para incluir todos los InfoPackages independientemente de los sistemas de origen.  
  
 **Buscar**  
 Permite buscar InfoPackages coincidentes que se hayan definido en el sistema SAP Netweaver BW.  
  
## <a name="lookup-results"></a>Buscar resultados  
 Después de hacer clic en el botón Buscar, aparece una lista de InfoPackages del sistema SAP Netweaver BW en una tabla con los siguientes encabezados de columna.  
  
 **InfoPackage**  
 Permite mostrar el nombre del InfoPackage que se haya definido en el sistema de SAP Netweaver BW.  
  
 **Tipo**  
 Permite mostrar el tipo de InfoPackage. En la siguiente tabla se muestran los posibles valores para el tipo.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|de transacciones|Datos de transacción.|  
|Atr.|Datos de atributo.|  
|Textos|Textos.|  
  
 **Descripción**  
 Permite mostrar la descripción del InfoPackage.  
  
 **InfoSource**  
 Permite mostrar el nombre del InfoSource, en su caso, que está asociado al InfoPackage.  
  
 **Source System**  
 Permite mostrar el nombre del sistema de origen.  
  
 Cuando aparezca la lista de InfoPackages, seleccione el InfoPackage que desee y el destino rellenará las opciones asociadas a los valores necesarios.  
  
## <a name="see-also"></a>Consulte también  
 [Editor de destino de SAP BW &#40;página Administrador de conexiones&#41;](../../integration-services/data-flow/sap-bw-destination-editor-connection-manager-page.md)   
 [Ayuda F1 de Microsoft Connector 1.1 for SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  

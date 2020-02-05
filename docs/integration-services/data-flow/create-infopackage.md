---
title: Crear InfoPackage | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9cd4a848-409f-4681-a390-1c49a2aadbd7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 25f1497b7801c7891681324b12fa9a5eda4eb842
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "71293208"
---
# <a name="create-infopackage"></a>Crear InfoPackage

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Use el cuadro de diálogo **Crear nuevo InfoPackage** para crear un nuevo InfoPackage en el sistema SAP Netweaver BW.  
  
 Puede abrir el cuadro de diálogo **Crear InfoPackage** desde la página **Administrador de conexiones** del **Editor de destino de SAP BW**. Para más información acerca del destino de SAP BW, consulte [SAP BW Destination](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  La documentación de Microsoft Connector 1.1 for SAP BW da por supuesto que se está familiarizado con el entorno SAP Netweaver BW. Para obtener más información acerca de SAP Netweaver BW, o sobre cómo configurar los objetos y los procesos de SAP Netweaver BW, vea la documentación de SAP.  
  
 **Para abrir el cuadro de diálogo Crear InfoPackage**  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], abra el paquete de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] que contiene el destino SAP BW.  
  
2.  En la pestaña **Flujo de datos** , haga doble clic en el destino de SAP BW.  
  
3.  En **Editor de destino SAP BW**, haga clic en **Administrador de conexiones** para abrir la página **Administrador de conexiones** del editor.  
  
4.  En la página **Administrador de conexiones** , en el cuadro del grupo **Crear objetos de SAP BW** , seleccione **InfoPackage**y, a continuación, haga clic en **Crear**.  
  
## <a name="options"></a>Opciones  
 **InfoSource**  
 Permite escribir el nombre del InfoSource en el que se va a basar el nuevo InfoPackage.  
  
 **Descripción breve**  
 Permite escribir una descripción para el nuevo InfoPackage.  
  
 **Sistema de origen**  
 Permite seleccionar el sistema origen con el que se va asociar el nuevo InfoPackage.  
  
 **Atributos**  
 Permite indicar que el InfoPackage cargará los datos del atributo.  
  
 **Textos**  
 Permite indicar que el InfoPackage cargará los datos de texto.  
  
 **Transacción**  
 Permite indicar que el InfoPackage cargará los datos de transacciones.  
  
 **Guardar y activar**  
 Permite guardar y activar el nuevo InfoPackage.  
  
## <a name="see-also"></a>Consulte también  
 [Ayuda F1 de Microsoft Connector for SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  

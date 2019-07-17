---
title: Configurar el tamaño máximo del archivo de carga (PowerPivot para SharePoint) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 15ce366acc4244db16f0b58bbdc8226e9327416c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "68164281"
---
# <a name="configure-maximum-file-upload-size-power-pivot-for-sharepoint"></a>Configuración del tamaño de carga máximo de archivos (PowerPivot para SharePoint)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] contienen grandes cantidades de datos que resultan en archivos que superan el tamaño de archivo máximo permitido en las cargas de SharePoint. Al intentar cargar un archivo que supera el límite superior, obtendrá el siguiente error en SharePoint:  
  
-   “El archivo especificado es mayor que el tamaño de archivo máximo admitido.”  
  
 Para aumentar el tamaño de archivo, empiece por ajustar el tamaño máximo del libro de Servicios de Excel en 50 megabytes. De esta forma, alinea los límites de tamaño de archivo máximos para Excel a los de las aplicaciones web de SharePoint (establecidos en 50 megabytes de forma predeterminada en SharePoint 2010 y en 200 en SharePoint 2013). Si los archivos superan 50 megabytes de tamaño, aumente los límites de tamaño de archivo para Servicios de Excel y la aplicación web.  
  
 Debe ser administrador de SharePoint para cambiar el tamaño máximo de la carga de archivo.  
  
### <a name="configure-maximum-file-size-for-excel-services"></a>Configurar el tamaño de archivo máximo para Servicios de Excel  
  
1.  En Administración central, en Administración de aplicaciones, haga clic en **Administrar aplicaciones de servicio**.  
  
2.  Haga clic en el nombre de la aplicación de Excel Services.  
  
3.  Haga clic en **Ubicaciones de archivos de confianza**.  
  
4.  Haga clic en la ubicación para modificar las propiedades. De forma predeterminada, Servicios de Excel considera la aplicación web predeterminada un sitio de confianza. Si usa la aplicación web predeterminada, haga clic en **http://** para abrir la página de configuración de esta ubicación.  
  
5.  Desplácese a **Propiedades del libro**.  
  
6.  En Tamaño máximo del libro, aumente el tamaño de archivo de 10 (el valor predeterminado) a 50 o un tamaño mayor que contenga los archivos con los que trabajan.  
  
     De forma predeterminada, 50 megabytes es el tamaño máximo de carga de archivo para las aplicaciones web de SharePoint. Si establece Tamaño máximo de archivo en un número mayor de 50 megabytes, siga los pasos del procedimiento siguiente para aumentar el valor de Tamaño máximo de carga de la aplicación web de SharePoint al mismo valor.  
  
     El valor máximo que puede especificar es 2 gigabytes (o 2047 megabytes como se especifica en Administración central).  
  
7.  Haga clic en **Aceptar**.  
  
### <a name="configure-maximum-file-size-for-a-sharepoint-web-application"></a>Configurar el tamaño máximo de archivo para una aplicación web de SharePoint  
  
1.  En Administración central, en Administración de aplicaciones, haga clic en **Administrar las aplicaciones web**.  
  
    > [!NOTE]  
    >  Siga estos pasos únicamente si aumentó el valor de Tamaño máximo del libro en Servicios de Excel.  
  
2.  Seleccione la aplicación (por ejemplo, **SharePoint - 80**).  
  
3.  En la cinta de Aplicaciones web, haga clic en la flecha abajo en el botón Configuración general.  
  
4.  Haga clic en **Configuración general**.  
  
5.  Desplácese a **Tamaño máximo de carga**.  
  
6.  Establezca la propiedad en el mismo número o uno mayor que el Tamaño máximo del libro de Excel Services.  
  
7.  Haga clic en **Aceptar**.  
  
  

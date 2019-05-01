---
title: Configuración global (registro) (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 835b09b5-eb42-47ea-b46e-e115d4d6461f
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 2cc49bbd3d2927431da2c16debbe0f35dbf4bb79
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63453562"
---
# <a name="global-settings-logging-accesstosql"></a>Configuración global (registro) (AccessToSQL)
Use la **configuración Global** cuadro de diálogo para especificar la configuración de registro para SSMA. Normalmente, desea cambiar esta configuración solo cuando se trabaja con servicios de soporte técnico.  
  
Para obtener acceso a este cuadro de diálogo, en el **herramientas** menú, seleccione **configuración Global** y, a continuación, haga clic en el **registro** situado en la parte inferior del panel izquierdo.  
  
## <a name="options"></a>Opciones  
**Nivel de mensajes**  
Las siguientes opciones están disponibles en **mensajes nivel**:  
  
|Opción|Descripción|  
|----------|---------------|  
|**[todas las categorías]**|Se usa para establecer el nivel de registro para todas las opciones siguientes.|  
|**Collector**|Recopila metadatos sobre el esquema de origen y lo guarda en el proyecto.|  
|**Convertidor de tipos**|Convierte las estructuras de objetos de base de datos de origen, como tablas y procedimientos almacenados, en correspondiente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] estructuras.|  
|**Migrador de datos**|Migra los datos de la base de datos de origen en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Formatter**|Subcomponente del convertidor que genera scripts para el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esquema.|  
|**Interfaz gráfica de usuario**|Mensajes que aparecen cuando se usa la herramienta SSMA.|  
|**Linker**|Resuelve los identificadores de SQL y se proporciona información a otros componentes.|  
|**Otro**|Todos los mensajes que no están en cualquier otra categoría.|  
|**Parser**|Analiza el esquema de origen.|  
|**Sincronizador**|En los objetos de base de datos del origen de carga [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**TreeConverter**|Convierte los objetos en los metadatos de origen en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] metadatos.|  
  
En cada opción **mensajes nivel**, configure uno de los siguientes niveles de registro para SSMA:  
  
|||  
|-|-|  
|**Error irrecuperable**|Escribir solo mensajes de error grave en el registro.|  
|**Error**|Escribir error y mensajes de error grave en el registro.|  
|**Advertencia**|Escribir mensajes de error grave, error y advertencia en el registro.|  
|**Info**|Escribir informativo, advertencia, error y mensajes de error grave en el registro.|  
|**Depuración**|Escribir todos los mensajes, incluidos los mensajes, en el registro de depuración.|  
  
**Ruta de acceso de archivo de registro**  
La ruta de acceso y nombre de los archivos de registro SSMA. Para especificar un nombre diferente, haga clic en la ruta de acceso actual y, a continuación, haga clic en el (**...** ) botón.  
  
**Tamaño del archivo de registro**  
El tamaño máximo del archivo de registro en KB. El tamaño mínimo es de 10 KB. El tamaño predeterminado es 10240 KB.  
  
**Número total de archivos de registro**  
Cuando se llena un registro, SSMA se cambie el nombre del archivo de registro y comenzar una nueva. Con esta configuración, especifique el número máximo de archivos de registro para mantener. El valor mínimo es 2.  
  

---
title: Tabla de ensayo de miembros consolidados
ms.custom: ''
ms.date: 04/01/2016
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], attributes staging table
- attributes staging table [Master Data Services]
ms.assetid: 070681ed-be99-49ae-93bd-6402f2134ace
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b7b700f4bcdd453f6a2ec6f437fe29370423d5ac
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "73729617"
---
# <a name="consolidated-member-staging-table-master-data-services"></a>Tabla de ensayo de miembros consolidados (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Use la tabla de almacenamiento provisional de miembros consolidados (stg.name_Consolidated) de la base de datos de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] para crear, actualizar, desactivar y eliminar miembros consolidados. También puede usarla para actualizar valores de atributos de miembros consolidados.  
  
##  <a name="TableColumns"></a> Columnas de la tabla  
 En la tabla siguiente se explica para qué se usa cada uno de los campos de la tabla de ensayo Consolidated.  
  
|Nombre de la columna|Descripción|  
|-----------------|-----------------|  
|**ID**|Identificador asignado automáticamente. No especifique ningún valor en este campo. Si no se ha procesado el lote, este campo está en blanco.|  
|**ImportType**<br /><br /> Necesario|Determina qué se debe hacer si los datos almacenados provisionalmente coinciden con datos que ya existen en la base de datos de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .<br /><br /> **0**: crear nuevos miembros. Reemplazar los datos de MDS existentes con datos almacenados provisionalmente, pero solo si los datos almacenados provisionalmente no son NULL. Los valores NULL se pasan por alto. Para cambiar un valor de atributo a NULL, use **~NULL~** .<br /><br /> **1**: crear miembros nuevos únicamente. Todas las actualizaciones de datos MDS existentes producen un error.<br /><br /> **2**: crear nuevos miembros. Reemplazar los datos de MDS con datos almacenados provisionalmente. Si importa valores NULL, sobrescribirán los valores de MDS existentes.<br /><br /> **3**: desactivar el miembro, según el valor de Code. Se conservan todos los atributos, pertenencias a jerarquías y colecciones, y transacciones pero ya no están disponibles en la interfaz de usuario. Si se utiliza el miembro como valor de atributo basado en dominio de otro miembro, la desactivación producirá un error.<br /><br /> **4**: eliminar definitivamente el miembro, según el valor de Code. Todos los atributos, pertenencias a jerarquías y colecciones, y transacciones se eliminan de forma permanente. Si se utiliza el miembro como valor de atributo basado en dominio de otro miembro, la eliminación producirá un error.|  
|**ImportStatus_ID**<br /><br /> Necesario|Estado del proceso de importación. Los valores posibles son:<br /><br /> **0**, que se especifica para indicar que el registro está listo para el almacenamiento provisional.<br /><br /> **1**, que se asigna e indica automáticamente que el proceso de almacenamiento provisional del registro ha sido correcto.<br /><br /> **2**, que se asigna automáticamente e indica que el proceso de almacenamiento provisional del registro no ha sido correcto.|  
|**Batch_ID**<br /><br /> Solo lo necesita el servicio web|Identificador asignado automáticamente que agrupa los registros para el almacenamiento provisional. A todos los miembros del lote se les asigna este identificador, que se muestra en la columna [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Id. **de la interfaz de usuario de** .<br /><br /> Si no se ha procesado el lote, este campo está en blanco.|  
|**BatchTag**<br /><br /> Obligatorio, excepto para el servicio web|Nombre único para el lote, de hasta 50 caracteres.|  
|**HierarchyName**<br /><br /> Necesario|Nombre de jerarquía explícita. Cada miembro consolidado solo puede pertenecer a una jerarquía.|  
|**ErrorCode**|Muestra un código de error. Para todos los registros con un **ImportStatus_ID** de **2**, consulte [Errores del proceso de almacenamiento provisional &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md).|  
|**código**<br /><br /> Obligatorio, excepto cuando los códigos se generan de forma automática para **ImportType1** o **2**; consulte [Creación automática de código &#40;Master Data Services&#41;](../master-data-services/automatic-code-creation-master-data-services.md) para obtener más información|Código único del miembro.|  
|**Nombre**<br /><br /> Opcional|Nombre del miembro.|  
|**NewCode**|Úselo solo si va a cambiar el código de miembro.|  
|\<nombre_atributo>|Existe una columna para cada atributo de la entidad. Úsela con un **ImportType** de **0** o **2**. Para los atributos de forma libre, especifique el nuevo texto o valor de cadena para el atributo. Para los atributos basados en dominio, especifique el código del miembro que será el atributo. Para los atributos de vínculo, la dirección URL debe comenzar con **https://** .<br /><br /> <br /><br /> Nota: No puede almacenar de forma provisional los atributos de archivo.|  
  
## <a name="see-also"></a>Vea también  
 [Información general: importación de datos de tablas &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [Ver los errores que se producen durante el almacenamiento provisional &#40;Master Data Services&#41;](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md)   
 [Errores del proceso de almacenamiento provisional &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md)  
  
  

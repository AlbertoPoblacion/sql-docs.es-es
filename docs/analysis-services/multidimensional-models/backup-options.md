---
title: Opciones de copia de seguridad | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 62f5bf26f80ea1018a5a3330efa0f055021ff0f5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62717814"
---
# <a name="backup-options"></a>Opciones de copia de seguridad
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Existen varias formas de hacer una copia de seguridad de las bases de datos de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , pero todas ellas tienen en común la necesidad de disponer de permisos de administrador de servidor y administrador de base de datos. Puede abrir el cuadro de diálogo **Copia de seguridad** en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], seleccionar las opciones adecuadas y, a continuación, ejecutar la copia de seguridad desde el mismo cuadro de diálogo. También puede crear un script mediante la configuración que ya está especificada en el archivo. A continuación, el script puede guardarse y ejecutarse siempre que sea necesario.  
  
## <a name="backup-and-synchronize"></a>Hacer una copia de seguridad y sincronizar  
 Si la base de datos reside en una instancia remota de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], puede utilizar la característica de sincronización para realizar una copia de seguridad de la base de datos en la instancia local. Las compilaciones de desarrollo de una base de datos pueden aplicarse a un entorno de producción de esta manera. También puede utilizarse el mecanismo convencional de copias de seguridad y restauración basadas en archivos para trasladar la compilación de desarrollo a un entorno de producción, pero la sincronización proporciona funcionalidad adicional. Por ejemplo, puede establecer una configuración de seguridad diferente para los equipos de desarrollo y de producción. La sincronización le ofrecerá la opción de mantener esa configuración y sincronizar todos los objetos que no son roles. Asimismo, la sincronización realiza normalmente una actualización incremental de los objetos que son diferentes en los equipos origen y destino. La copia de seguridad incremental no está disponible cuando se utiliza la característica de copia de seguridad/restauración. Para más información, consulte [Synchronize Analysis Services Databases](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md).  
  
> [!IMPORTANT]  
>  La cuenta de servicio de Analysis Services debe tener permiso para escribir en la ubicación de copia de seguridad especificada para cada archivo. Además, el usuario debe tener uno de los roles siguientes: rol de administrador en la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o ser miembro de un rol de base de datos con permisos de Control total (Administrador) en la base de datos de la que se va a hacer copia de seguridad.  
  
## <a name="see-also"></a>Vea también  
 [Cuadro de diálogo Copia de seguridad de la base de datos &#40;Analysis Services - Datos multidimensionales&#41;](http://msdn.microsoft.com/library/7811ce7d-6c37-4189-bfa6-ef36fb4932db)   
 [Realizar una copia de seguridad y restaurar las bases de datos de Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)   
 [Elemento de copia de seguridad &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla)   
 [Restaurar, sincronizar y realizar copias de seguridad de bases de datos &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  

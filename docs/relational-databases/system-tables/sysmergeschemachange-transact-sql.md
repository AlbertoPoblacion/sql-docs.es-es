---
title: sysmergeschemachange (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysmergeschemachange_TSQL
- sysmergeschemachange
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergeschemachange system table
ms.assetid: ae9ce16e-6ee9-4c7c-8210-a9bf2c7efdf0
author: stevestein
ms.author: sstein
ms.openlocfilehash: e7225fae192ab256c2c2660fcb1554cd01818907
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029819"
---
# <a name="sysmergeschemachange-transact-sql"></a>sysmergeschemachange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene información acerca de los artículos publicados generados por el Agente de instantáneas. Esta tabla se almacena en las bases de datos de publicación y de suscripciones.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**pubid**|**uniqueidentifier**|Id. de la publicación.|  
|**artid**|**uniqueidentifier**|Id. del artículo.|  
|**schemaversion**|**int**|Número del último cambio de esquema.|  
|**schemaguid**|**uniqueidentifier**|Id. único del último esquema.|  
|**schematype**|**int**|Tipo de cambio de esquema:<br /><br /> **-1** = no válido.<br /><br /> **1** = comando SQL.<br /><br /> **2** = script de esquema.<br /><br /> **3** = programa nativo de copia masiva (bcp).<br /><br /> **4** = carácter BCP.<br /><br /> **5** = última generación registrada.<br /><br /> **6** = última generación enviada.<br /><br /> **7** = directorio.<br /><br /> **8** = prioridad.<br /><br /> **9** = período de retención.<br /><br /> **10** = script de desencadenadores.<br /><br /> **11** = modificar tabla.<br /><br /> **12** = reinicializar todo.<br /><br /> **13** = ALTER TABLE (que no sean de[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]).<br /><br /> **14** = reinicializar con carga.<br /><br /> **15** = restricción e índice de secuencia de comandos.<br /><br /> **16** = limpieza de metadatos.<br /><br /> **17** = actualizar última generación enviada.<br /><br /> **18** = nivel de compatibilidad con versiones anteriores.<br /><br /> **19** = validar información del suscriptor.<br /><br /> **20** = bien particionada.<br /><br /> **21** = solucionador personalizado.<br /><br /> **22** = orden de procesamiento del artículo.<br /><br /> **23** = publicado en una publicación transaccional.<br /><br /> **24** = compensación por errores.<br /><br /> **25** = carpeta de instantáneas alternativa.<br /><br /> **26** = solo descarga.<br /><br /> **27** = seguimiento de eliminaciones.<br /><br /> **40** = script de creación previa a la instantánea.<br /><br /> **45** = script posterior a la creación de la instantánea.<br /><br /> **46** = script de usuario y a petición.<br /><br /> **50** = encabezado de instantánea de comenzar.<br /><br /> **51** = final del encabezado de instantánea.<br /><br /> **52** = finalizador de instantáneas.<br /><br /> **53** = dirección de protocolo de transferencia de archivos (FTP).<br /><br /> **54** = puerto FTP.<br /><br /> **55** = subdirectorio FTP.<br /><br /> **56** = instantánea comprimida.<br /><br /> **57** = inicio de sesión FTP.<br /><br /> **58** = contraseña FTP.<br /><br /> **60** = script de creación previa del sistema.<br /><br /> **61** = esquema de procedimiento almacenado.<br /><br /> **62** = esquema de la vista.<br /><br /> **63** = esquema de función definido por el usuario.<br /><br /> **64** = índices de vistas.<br /><br /> **65** = propiedades extendidas.<br /><br /> **66** = validar.<br /><br /> **67** = comando SQL previo a la instantánea.<br /><br /> **71** = validación de la instantánea dinámica.<br /><br /> **80** = sistema tabla nativo BCP 9.0.<br /><br /> **81** = caracteres de tabla del sistema BCP 9.0.<br /><br /> **82** = sistema nativo BCP 9.0 (solo global) de la tabla.<br /><br /> **83** = caracteres de tabla del sistema BCP 9.0 (solo global).<br /><br /> **84** = sistema nativo BCP 9.0 (ligera) de la tabla.<br /><br /> **85** = caracteres de tabla del sistema (ligera) de BCP 9.0.<br /><br /> **128** = BCP dinámica (bit).<br /><br /> **131** = BCP nativa dinámica.<br /><br /> **132** = BCP de caracteres dinámica.<br /><br /> **208** = dinámico tabla del sistema nativo BCP 9.0.<br /><br /> **209** = caracteres de tabla del sistema dinámica BCP 9.0.<br /><br /> **210** = dinámico nativo BCP 9.0 (solo global) de tabla del sistema.<br /><br /> **211** = caracteres de tabla del sistema dinámica BCP 9.0 (solo global).<br /><br /> **212** = dinámico nativo BCP 9.0 (ligera) de tabla del sistema.<br /><br /> **213** = caracteres de tabla del sistema dinámica (ligera) de BCP 9.0.<br /><br /> **300** = acciones de lenguaje de definición de datos (DDL).<br /><br /> **1024** = control de instantáneas incrementales.<br /><br /> **1049** = carpeta de instantáneas incrementales.<br /><br /> **1074** = Incremental de encabezado de inicio de la instantánea.<br /><br /> **1075** = encabezado de instantánea incremental final.<br /><br /> **1076** = finalizador de instantáneas incrementales.<br /><br /> **1077** = dirección FTP incremental.<br /><br /> **1078** = puerto FTP incremental.<br /><br /> **1079** = subdirectorio FTP incremental.<br /><br /> **1080** = instantánea comprimida incremental.<br /><br /> **1081** = inicio de sesión FTP incremental.<br /><br /> **1082** = contraseña FTP incremental.|  
|**schematext**|**nvarchar(2000)**|El nombre del archivo de script o un comando que incluye un nombre de archivo.|  
|**schemastatus**|**tinyint**|Indica si hay pendiente algún cambio de esquema para el artículo. Puede ser uno de estos valores:<br /><br /> **0** = inactivo.<br /><br /> **1** = activo.<br /><br /> Cuando hay pendiente un cambio de esquema, este valor se establece en **1**.|  
|**schemasubtype**|**int**|El subtipo de cambio de esquema:<br /><br /> **1** = ADDCOLUMN<br /><br /> **2** = DROPCOLUMN<br /><br /> **3** = ALTERCOLUMN<br /><br /> **4** = ADDPRIMARYKEY<br /><br /> **5** = ADDUNIQUE<br /><br /> **6** = ADDREFERENCE<br /><br /> **7** = DROPCONSTRAINT<br /><br /> **8** = ADDDEFAULT<br /><br /> **9** = ADDCHECK<br /><br /> **10** = DISABLETRIGGER<br /><br /> **11** = ENABLETRIGGER<br /><br /> **12** = DISABLETRIGGER<br /><br /> **13** = ENABLETRIGGER<br /><br /> **14** = ENABLECONSTRAINT<br /><br /> **15** = DISABLECONSTRAINT<br /><br /> **16** = ENABLECONSTRAINT<br /><br /> **17** = DISABLECONSTRAINT|  
  
## <a name="see-also"></a>Vea también  
 [Las tablas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vistas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  

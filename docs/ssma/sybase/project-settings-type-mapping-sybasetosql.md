---
title: Configuración del proyecto (asignación de tipo) (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 2698fb3a-f9e6-4e04-94e0-dad289d7ed0a
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 148180d95bcbff1626069e72fb66dd9a3ca859c9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62667925"
---
# <a name="project-settings-type-mapping-sybasetosql"></a>Configuración del proyecto (asignación de tipo) (SybaseToSQL)
La página de asignación de tipos de la **configuración del proyecto** cuadro de diálogo contiene la configuración que permiten personalizar cómo SSMA convierte tipos de datos de Sybase Adaptive Server Enterprise (ASE) en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipos de datos.  
  
Está disponible en la página de asignación de tipos de la **configuración del proyecto** y **configuración de proyecto predeterminada** cuadros de diálogo.  
  
-   Para especificar la configuración de asignación de tipo para todos los proyectos SSMA futuros, en el **herramientas** menú, seleccione **la configuración predeterminada del proyecto**, seleccione el tipo de proyecto de migración para que la configuración es necesaria para verse o ha cambiado de **versión de destino de migración** lista desplegable y, a continuación, seleccione **Type Mapping** en la parte inferior del panel izquierdo.  
  
-   Para especificar la configuración para el proyecto actual, en el **herramientas** menú, seleccione **configuración del proyecto**y, a continuación, seleccione **Type Mapping** en la parte inferior del panel izquierdo.  
  
## <a name="options"></a>Opciones  
**Tipo de origen**  
El tipo de datos asignado de ASE.  
  
**Tipo de destino**  
El destino [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo de datos para el tipo de datos especificado de ASE.  
  
Consulte la tabla en la sección siguiente para el valor predeterminado SSMA para Sybase asignación de tipos.  
  
**Agregar**  
Haga clic para agregar un tipo de datos a la lista de asignación.  
  
**Editar**  
Haga clic para editar el tipo de datos seleccionado en la lista de asignación.  
  
**Quitar**  
Haga clic para quitar la asignación de tipos de datos seleccionados de la lista de asignación.  
  
**Valores predeterminados**  
Haga clic para restablecer la lista de asignación de tipo para los valores predeterminados SSMA.  
  
## <a name="default-type-mapping"></a>Asignación de tipos predeterminados  
La tabla siguiente contiene la asignación de tipos predeterminada entre ASE y [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipos de datos.  
  
|Tipo de datos de ASE|Tipo de datos de SQL Server|  
|-----------------|------------------------|  
|**bigint**|**bigint**|  
|**binario**|**binario**|  
|**binary[\*..8000]**|**binary[\*]**|  
|**binary[8001..\*]**|**varbinary(max)**|  
|**bit**|**bit**|  
|**char**|**char**|  
|**char varying**|**varchar**|  
|**char varying [\*... 8000]**|**varchar[\*]**|  
|**char varying [8001..\*]**|**ntext**|  
|**char[\*..8000]**|**char[\*]**|  
|**char[8001..\*;]**|**ntext**|  
|**character**|**char**|  
|**variable de carácter**|**varchar**|  
|**variable de carácter [\*... 8000]**|**varchar[\*]**|  
|**variable de carácter [8001..\*]**|**ntext**|  
|**caracteres [\*... 8000]**|**char[\*]**|  
|**character[8001..\*]**|**ntext**|  
|**date**|**date**|  
|**datetime**|**datetime2[3]**|  
|**dec**|**decimal**|  
|**dec[\*..\*]**|**decimal[\*]**|  
|**dec[\*..\*][\*..\*]**|**decimal[\*][\*]**|  
|**decimal**|**decimal**|  
|**decimal[\*..\*]**|**decimal[\*]**|  
|**decimal[\*..\*][\*..\*]**|**decimal[\*][\*]**|  
|**doble precisión**|**float[53]**|  
|**float**|**float[53]**|  
|**float [\*... 15]**|**float[24]**|  
|**float[16..\*]**|**float[53]**|  
|**image**|**image**|  
|**int**|**int**|  
|**integer**|**int**|  
|**longsysname**|**nvarchar[255]**|  
|**money**|**money**|  
|**carácter nacional**|**nchar**|  
|**carácter nacional [\*... 4000]**|**nchar[\*]**|  
|**variable de Car. nacional**|**nvarchar**|  
|**National char varying [\*... 4000]**|**nvarchar[\*]**|  
|**National char varying [4001..\*]**|**nvarchar(max)**|  
|**carácter nacional [4001..\*]**|**nvarchar(max)**|  
|**carácter nacional**|**nchar**|  
|**carácter nacional [\*... 4000]**|**nchar[\*]**|  
|**carácter nacional [4001..\*]**|**nvarchar(max)**|  
|**national character varying de**|**nvarchar**|  
|**national character varying de [\*... 4000]**|**nvarchar[\*]**|  
|**national character varying de [4001..\*]**|**nvarchar(max)**|  
|**varchar nacional**|**nvarchar**|  
|**National varchar [\*... 4000]**|**nvarchar[\*]**|  
|**National varchar [4001..\*]**|**nvarchar(max)**|  
|**nchar**|**nchar**|  
|**nchar varying**|**nvarchar**|  
|**nchar varying [\*... 4000]**|**nvarchar[\*]**|  
|**nchar varying[4001..\*]**|**nvarchar(max)**|  
|**nchar[\*..4000]**|**nchar[\*]**|  
|**nchar[4001..\*]**|**nvarchar(max)**|  
|**numeric**|**numeric**|  
|**numeric[\*..\*]**|**numeric[\*]**|  
|**numeric[\*..\*][\*..\*]**|**numeric[\*][\*]**|  
|**nvarchar**|**nvarchar**|  
|**nvarchar[\*..4000]**|**nvarchar[\*]**|  
|**nvarchar[4001..\*]**|**nvarchar(max)**|  
|**real**|**float[24]**|  
|**smalldatetime**|**smalldatetime**|  
|**smallint**|**smallint**|  
|**smallmoney**|**smallmoney**|  
|**sysname**|**nvarchar[128]**|  
|**sysname[\*..\*]**|**nvarchar[255]**|  
|**texto**|**texto**|  
|**time**|**time[3]**|  
|**timestamp**|**rowversion**|  
|**tinyint**|**tinyint**|  
|**unichar**|**nchar**|  
|**variable UNICHAR**|**nvarchar**|  
|**variable UNICHAR [\*... 4000]**|**nvarchar[\*]**|  
|**unichar varying[4001..\*]**|**nvarchar(max)**|  
|**unichar[\*..4000]**|**nchar[\*]**|  
|**unichar[4001..\*]**|**nvarchar(max)**|  
|**unitext**|**nvarchar(max)**|  
|**univarchar**|**nvarchar**|  
|**univarchar[\*..4000]**|**nvarchar[\*]**|  
|**univarchar[4001..\*]**|**nvarchar(max)**|  
|**bigint sin signo**|**numeric[20][0]**|  
|**int sin signo**|**bigint**|  
|**smallint sin signo**|**int**|  
|**tinyint sin signo**|**tinyint**|  
|**varbinary**|**varbinary**|  
|**varbinary[\*..8000]**|**varbinary[\*]**|  
|**varbinary[8001..\*]**|**varbinary(max)**|  
|**varchar**|**varchar**|  
|**varchar[\*..8000]**|**varchar[\*]**|  
|**varchar[8001..\*]**|**ntext**|  
  

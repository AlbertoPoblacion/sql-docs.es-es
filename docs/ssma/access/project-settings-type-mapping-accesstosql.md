---
title: Configuración del proyecto (asignación de tipo) (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access data types
- data types, default mappings
- default data type mappings
- Project Settings dialog box, Type Mapping
- SQL Server data types
- Type Mapping settings
ms.assetid: b87b9683-abed-4677-8c50-18bdba704655
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 8a695217909641c737b7780fc4f8b80b2cb08152
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63299130"
---
# <a name="project-settings-type-mapping-accesstosql"></a>Configuración del proyecto (asignación de tipo) (AccessToSQL)
La configuración del proyecto de asignación de tipos le permite establecer asignaciones de tipos predeterminadas para el proyecto SSMA. También puede especificar asignaciones de tipos para objetos de base de datos individual. Para obtener más información, consulte [tipos de datos de destino y origen de asignación](mapping-source-and-target-data-types-accesstosql.md).  
  
Asignación de tipos está disponible en el **configuración del proyecto** y **configuración de proyecto predeterminada** cuadros de diálogo:  
  
-   Use la **configuración del proyecto** cuadro de diálogo para establecer las opciones de configuración para el proyecto actual. Para obtener acceso a la configuración de asignación de tipo en el **herramientas** menú, seleccione **configuración del proyecto**y, a continuación, haga clic en **asignación de tipo** en el panel izquierdo.  
  
-   Use la **configuración de proyecto predeterminada** cuadro de diálogo para establecer las opciones de configuración para todos los proyectos. Para acceder a la configuración de asignación de tipo en el **herramientas** menú, seleccione **la configuración predeterminada del proyecto**, seleccione el tipo de proyecto de migración para los que es necesaria para ver o cambiar de configuración  **Versión de destino de migración** lista desplegable y, a continuación, haga clic en **Type Mapping** en el panel izquierdo.  
  
## <a name="options"></a>Opciones  
**Tipo de origen**  
El tipo de datos de acceso para asignar.  
  
**Tipo de destino**  
El destino [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o tipo de datos de SQL Azure para el tipo de datos de acceso especificado.  
  
En la tabla siguiente se muestra la asignación predeterminada entre los tipos de datos de origen y de destino.  
  
|Tipo de datos de Access|Tipo de datos de SQL Server|  
|--------------------|------------------------|  
|**binario [\*... \*]**|**varbinary[\*]**|  
|**boolean**|**bit**|  
|**byte**|**tinyint**|  
|**currency**|**money**|  
|**date**|**datetime**|  
|**decimal**|**float**|  
|**double**|**float**|  
|**guid**|**uniqueidentifier**|  
|**integer**|**smallint**|  
|**long**|**int**|  
|**longbinary**|**varbinary(max)**|  
|**memo**|**nvarchar(max)**|  
|**memorando** : para Access 97|**ntext**|  
|**single**|**real**|  
|**text[\*..\*]**|**nvarchar[\*]**|  
|**texto [\*... \*]** : para Access 97|**varchar[\*]**|  
  
**Agregar**  
Haga clic para agregar un tipo de datos a la lista de asignación.  
  
**Editar**  
Haga clic para editar un tipo de datos en la lista de asignación.  
  
**Quitar**  
Haga clic para quitar la asignación de tipos de datos seleccionados de la lista de asignación.  
  
**Valores predeterminados**  
Haga clic para restablecer todas las asignaciones de tipo de datos a los valores predeterminados SSMA.  
  
## <a name="see-also"></a>Vea también  
[Asignación de tipos de datos de origen y de destino](mapping-source-and-target-data-types-accesstosql.md)  
[Reference(Access) de interfaz de usuario](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  

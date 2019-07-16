---
title: Configuración del proyecto (Azure SQL DB) (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 57002374-0d4d-43c1-b4e9-cbec02355a9c
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 98430a626a628d4c8cc040b53a9cf24ad1752048
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68028781"
---
# <a name="project-settings-azure-sql-db--sybasetosql"></a>Configuración del proyecto (Azure SQL DB ) (SybaseToSQL)
La configuración del proyecto de base de datos de SQL Azure le permite configurar el sufijo de la base de datos de Azure SQL DB para agregarse en el cuadro de diálogo de conexión y también permite implementar el mecanismo de latidos de conexión de Azure SQL DB.  
  
El panel de Azure SQL DB está disponible en el **configuración del proyecto** y **configuración de proyecto predeterminada** cuadros de diálogo.  
  
-   Utilice el cuadro de diálogo de configuración del proyecto para establecer las opciones de configuración para el proyecto actual. Para obtener acceso a la configuración de la base de datos de SQL Azure, en el **herramientas** menú, seleccione **configuración del proyecto**, haga clic en **General** en la parte inferior del panel izquierdo y a continuación, seleccione  **Azure SQL DB**.  
  
-   Utilice el cuadro de diálogo Configuración de proyecto predeterminada para establecer las opciones de configuración para todos los proyectos. Para obtener acceso a la configuración de la base de datos de SQL Azure, en el **herramientas** menú, seleccione **DefaultProject configuración**, haga clic en **General** en la parte inferior del panel izquierdo y, a continuación, seleccione **Azure SQL DB**.  
  
## <a name="connectivity"></a>Conectividad  
**Intervalo de latidos**  
  
Especifica un intervalo de tiempo que se usará para el mecanismo de latidos para mantener activa en la conexión de base de datos de SQL Azure "minutos: formato de segundos.  
  
**Valor predeterminado**:' 4:45 '  
  
El valor debe especificarse en estoy: formato de ss (por ejemplo, ' 4:45 ' o ' 0:50 ').  
  
**Sufijo de servidor de base de datos de SQL Azure**  
  
Especifica un sufijo del servidor de base de datos de SQL Azure  
  
**Valor predeterminado**: 'database.windows.net'.  
  

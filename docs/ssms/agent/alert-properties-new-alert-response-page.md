---
title: 'Propiedades de alerta: Nueva alerta (página Respuesta) | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.alert.response.f1
ms.assetid: 72daf008-f9ea-4077-b217-5048e7759d3e
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: da2d50d1601567c15622350a461d32b2e21ebd37
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2019
ms.locfileid: "65099506"
---
# <a name="alert-properties---new-alert-response-page"></a>Propiedades de alerta - Nueva alerta (página Respuesta)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> En [Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la mayoría de las características de agente SQL Server son compatibles actualmente, aunque no todas. Vea [Diferencias de T-SQL en Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) para obtener más información.

Use esta página para especificar el trabajo que desea ejecutar y obtener una lista de operadores a los que se notificará en respuesta a una alerta del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  

## <a name="options"></a>Opciones  
**Ejecutar trabajo**  
Habilita las opciones **Lista de trabajos**, **Nuevo trabajo** y **Ver trabajo** .  
  
**Nuevo trabajo**  
Abre el cuadro de diálogo **Nuevo trabajo** . Este botón no está disponible si la opción **Ejecutar trabajo** no está seleccionada.  
  
**Ver trabajo**  
Permite ver o modificar el trabajo seleccionado. Esta opción no está disponible si **Ejecutar trabajo** no está seleccionada.  
  
**Notificar a los operadores**  
Habilita los controles que le permiten agregar, quitar o cambiar operadores.  
  
**Lista de operadores**  
Enumera los operadores a los que se notificará cuando se produzca una alerta. Para especificar un método de notificación, seleccione la casilla **Correo electrónico**, **Buscapersonas**o **Net send** que aparece después del nombre del operador. Esta opción no está disponible si **Notificar a los operadores** no está seleccionada.  
  
**Correo electrónico**  
Utiliza el correo electrónico para notificar al operador.  
  
**Buscapersonas**  
Utiliza la dirección de correo electrónico del buscapersonas para notificar al operador.  
  
**Net send**  
Use **net send** para notificar al operador.  
  
**Nuevo operador**  
Muestra el cuadro de diálogo **Nuevo operador** , que se puede usar para crear un nuevo operador.  
  
**Ver operador**  
Muestra el cuadro de diálogo **Propiedades** para el operador seleccionado actualmente. Puede ver y modificar las propiedades del operador en el cuadro de diálogo **Propiedades del operador**.  
  
## <a name="see-also"></a>Consulte también  
[Alertas](../../ssms/agent/alerts.md)  
[Create an Alert Using Severity Level](../../ssms/agent/create-an-alert-using-severity-level.md)  
[Alertas](../../ssms/agent/alerts.md)  
[Edit an Alert](../../ssms/agent/edit-an-alert.md)  
[Delete an Alert](../../ssms/agent/delete-an-alert.md)  
  

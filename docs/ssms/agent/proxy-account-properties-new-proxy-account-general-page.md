---
title: Propiedades de cuenta de proxy - Nueva cuenta de proxy (página General) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.proxy.general.f1
ms.assetid: 5cd81265-bf59-413b-8397-150ddc70d0c7
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e1dabf36ad4e7c1d24b3fd1d4f5510ec711d715b
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68266816"
---
# <a name="proxy-account-properties---new-proxy-account-general-page"></a>Propiedades de cuenta de proxy - Nueva cuenta de proxy (página General)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> En [Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la mayoría de las características de agente SQL Server son compatibles actualmente, aunque no todas. Vea [Diferencias de T-SQL en Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) para obtener más información.

Utilice esta página para ver y cambiar las propiedades de una cuenta de proxy del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Opciones  
**Nombre del proxy**  
Escriba el nombre del proxy.  
  
**Nombre de credencial**  
Escriba el nombre de la credencial para el proxy.  
  
> [!NOTE]  
> El nombre de la credencial proporcionada debe ser el nombre de una credencial existente. Para obtener más información acerca de la creación de credenciales, vea [Procedimientos para: crear un proxy (SQL Server Management Studio)](https://msdn.microsoft.com/c1e77e91-2a69-40d9-b8b3-97cffc710586)  
  
**...**  
Inicia el cuadro de diálogo **Seleccionar credencial** .  
  
**Descripción**  
Escriba la descripción del proxy.  
  
**Active los siguientes subsistemas:**  
Seleccione los subsistemas a los que tiene acceso la cuenta de proxy.  
  
**Volver a asignar pasos de trabajo a**  
Seleccione el proxy al que se reasignan los pasos de trabajo. Esta lista se habilita cuando se revoca el acceso a un subsistema al que el proxy tenía acceso anteriormente.  
  
## <a name="see-also"></a>Consulte también  
[Crear un proxy del Agente SQL Server](../../ssms/agent/create-a-sql-server-agent-proxy.md)  
  

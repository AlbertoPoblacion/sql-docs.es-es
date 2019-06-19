---
title: catalog.deploy_packages | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 8e861df6-d103-4d84-8438-e822533f6849
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d4ee8e7d796016f07339f5ef083fe1fde23d859d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65716370"
---
# <a name="catalogdeploypackages"></a>catalog.deploy_packages 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Implementa uno o más paquetes en una carpeta en el catálogo de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] o actualiza un paquete existente que se ha implementado previamente.  
  
## <a name="syntax"></a>Sintaxis  
  
```sql  
[catalog].[deploy_packages]     [ @folder_name = ] folder_name,    [ @project_name = ] project_name,    [ @packages_table = ] packages_table,     [ @operation_id OUTPUT ] operation_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [ @folder_name = ] *folder_name*  
 Nombre de la carpeta. *folder_name* es **nvarchar(128)** .  
  
 [ @project_name = ] *project_name*  
 Nombre del proyecto en la carpeta. *project_name* es **nvarchar(128)** .  
  
 [ @packages_table = ] *packages_table*  
 Contenido binario de archivos de paquete de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (.dtsx). *packages_table* es **[catalog].[Package_Table_Type]**  
  
 [ @operation_id = ] *operation_id*  
 Devuelve el identificador único para la operación de implementación. *operation_id* es **bigint**.  
  
## <a name="return-code-value"></a>Valor de código de retorno  
 0 (correcto)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 None  
  
## <a name="permissions"></a>Permisos  
 Este procedimiento almacenado necesita uno de los permisos siguientes:  
  
-   Permisos CREATE_OBJECTS en el proyecto o permisos MODIFY en el paquete para actualizar un paquete.  
  
-   Pertenencia al rol de base de datos de **ssis_admin**  
  
-   Pertenencia al rol de servidor de **sysadmin**  
  
## <a name="errors-and-warnings"></a>Errores y advertencias  
 La siguiente lista describe algunas condiciones que pueden hacer que este procedimiento almacenado produzca un error:  
  
-   Un parámetro hace referencia a un objeto que no existe, intenta crear un objeto que ya existe o no es válido por algún otro motivo.  
  
-   El usuario no tiene permisos suficientes  
  
  

---
description: Importar directivas (cuadro de diálogo)
title: Importar directivas (cuadro de diálogo) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql13.swb.dmf.importpolicy.f1
ms.assetid: 78ab5f6e-2f13-4788-937e-8892ef4e2345
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 8cd6f4223d3cf23d9ccd98f5b8e4f787872132f3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2020
ms.locfileid: "88423699"
---
# <a name="import-policies-dialog-box"></a>Importar directivas (cuadro de diálogo)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Utilice este cuadro de diálogo para importar una o varias directivas (y su condición a la que se hace referencia) que se guardaron como archivos XML, en la instancia de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] actual.  
  
## <a name="options"></a>Opciones  
 **Archivos para importar**  
 Para importar una directiva desde un archivo XML, escriba la ruta de acceso y el nombre del archivo, o use el botón Examinar (**...**).  
  
 **Reemplazar duplicados con elementos importados**  
 Seleccione esta opción para sobrescribir cualquier directiva o condición existente del mismo nombre si ya existe en esta instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Una condición con una directiva dependiente no se puede sobrescribir a menos que la directiva dependiente se esté sobrescribiendo también. Si no se selecciona esta opción, una condición existente que está utilizando la misma expresión de condición no producirá un error.  
  
 **Estado de directiva**  
 Seleccione el estado que desea para la directiva importada:  
  
-   **Conservar el estado de las directivas al importar**  
  
-   **Habilitar todas las directivas al importar**  
  
-   **Deshabilitar todas las directivas al importar**  
  
## <a name="see-also"></a>Consulte también  
 [Administrar servidores mediante administración basada en directivas](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Importar una directiva de administración basada en directivas](../../relational-databases/policy-based-management/import-a-policy-based-management-policy.md)   
 [Exportar una directiva de administración basada en directivas](../../relational-databases/policy-based-management/export-a-policy-based-management-policy.md)  
  
  

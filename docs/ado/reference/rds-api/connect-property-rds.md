---
title: Propiedad Connect (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Connect property [ADO]
ms.assetid: dbad5e77-b213-4eb8-aecf-d60f203fdb59
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ba8b5aa1f59fbb161da878f5930f83d2f6ff0bdd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67964565"
---
# <a name="connect-property-rds"></a>Propiedad Connect (RDS)
Indica el nombre de la base de datos desde el que se ejecutan las operaciones de consulta y actualización.  
  
 Puede establecer el **Connect** propiedad en tiempo de diseño en el [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) etiquetas de objeto del objeto, o en tiempo de ejecución de secuencias de comandos de código (por ejemplo, VBScript).  
  
> [!IMPORTANT]
>  A partir de Windows 8 y Windows Server 2012, componentes de servidor RDS ya no están incluidos en el sistema operativo de Windows (consulte Windows 8 y [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) para obtener más detalles). Componentes de cliente RDS se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan. Deben migrar las aplicaciones que usan RDS a [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Design time: <PARAM NAME="Connect" VALUE="ConnectionString">  
Run time: DataControl.Connect = "ConnectionString"  
```  
  
#### <a name="parameters"></a>Parámetros  
 *ConnectionString*  
 Una cadena de conexión válida. Para obtener información general sobre las cadenas de conexión, vea el [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) propiedad o la documentación del proveedor.  
  
> [!NOTE]
>  Si especifica MS Remote como el proveedor para el **RDS. DataControl** crearía un escenario de cuatro niveles. Escenarios de más de tres niveles no se han probado y no deberían ser necesario.  
  
 *DataControl*  
 Una variable de objeto que representa un **RDS. DataControl** objeto.  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo (VBScript) de la propiedad de conexión](../../../ado/reference/rds-api/connect-property-example-vbscript.md)   
 [Método Query (RDS)](../../../ado/reference/rds-api/query-method-rds.md)   
 [Método Refresh (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [Método SubmitChanges (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)



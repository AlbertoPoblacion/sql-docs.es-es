---
title: "Método setSelectMethod (SQLServerDataSource) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDataSource.setSelectMethod
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 7934276d-5ac9-4cbc-a2a0-2c65c93733ac
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1348b8e7724edb9366ffff07594874dcc8d5c2b0
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="setselectmethod-method-sqlserverdatasource"></a>Método setSelectMethod (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Establece el tipo de cursor predeterminado que se utiliza para todos los conjuntos de resultados que se crean mediante este [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public void setSelectMethod(java.lang.String selectMethod)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *selectMethod*  
  
 A **cadena** valor que contiene el tipo de cursor predeterminado.  
  
## <a name="remarks"></a>Comentarios  
 El cursor selectMethod es el tipo de cursor predeterminado que se utiliza en un conjunto de resultados. Esta propiedad es útil cuando se estén abordando grandes conjuntos de resultados y no se quiera almacenar el conjunto de resultados entero del lado cliente. Si se establece la propiedad en "cursor", podrá crear un cursor en el lado del servidor que puede capturar fragmentos más pequeños de cada vez. Si no se establece la propiedad selectMethod, [getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md) devuelve el valor predeterminado "Direct".  
  
## <a name="see-also"></a>Vea también  
 [Miembros SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Clase SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

---
title: "setNString (método) (int, java.lang.String) | Documentos de Microsoft"
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
ms.assetid: b7da6d44-f5b1-44f8-95f5-40179968b1b0
caps.latest.revision: "18"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3b84ef0d56dfb73670571020e911b200afaac1db
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="setnstring-method-int-javalangstring"></a>Método setNString (int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Establece el parámetro designado para especificado **cadena** objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public final void setNString(int parameterIndex,  
                                                  java.lang.String value)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *parameterIndex*  
  
 Un **int** que indica el índice del parámetro.  
  
 *value*  
  
 A **cadena** objeto que contiene el valor del parámetro.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método se debería utilizar para **NCHAR**, **NVARCHAR**, **NTEXT**, y **XML** tipos de datos.  
  
 Este método setNString especificado por el método setNString en la interfaz java.sql.PreparedStatement.  
  
## <a name="see-also"></a>Vea también  
 [Miembros SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  

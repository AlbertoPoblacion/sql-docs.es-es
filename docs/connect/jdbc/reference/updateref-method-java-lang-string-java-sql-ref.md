---
title: Método updateRef (java.lang.String, java.sql.Ref) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateRef (java.lang.String, java.sql.Ref)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7740d17d-282f-4f1d-91f9-c68a873b069a
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a07f14422a1e4d6db9c9715ac766b9265fdeb86c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66778454"
---
# <a name="updateref-method-javalangstring-javasqlref"></a>Método updateRef (java.lang.String, java.sql.Ref)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Actualiza la columna designada con un valor java.sql.Ref según el nombre de la columna.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public void updateRef(java.lang.String columnName,  
                      java.sql.Ref x)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *columnName*  
  
 Valor **String** que contiene el nombre de columna.  
  
 *x*  
  
 Un objeto de Ref.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notas  
 Este método updateRef especificado por el método updateRef en la interfaz java.sql.ResultSet.  
  
## <a name="see-also"></a>Consulte también  
 [Método updateRef &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateref-method-sqlserverresultset.md)   
 [Miembros SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Clase SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

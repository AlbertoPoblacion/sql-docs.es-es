---
title: Método setRef (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setRef
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1a09bbf9-6f8f-4a21-85d2-2182111b5ce7
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: fbddeef54d5deef75cc7ae87bbb03fd010d2d19c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796767"
---
# <a name="setref-method-sqlserverpreparedstatement"></a>Método setRef (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Establece el parámetro designado para el objeto Ref determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public final void setRef(int i,  
                         java.sql.Ref x)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *i*  
  
 Valor **int** que indica el número de parámetro.  
  
 *x*  
  
 Un objeto de Ref.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notas  
 El método setRef especifica este método setRef en la interfaz java.sql.PreparedStatement.  
  
## <a name="see-also"></a>Consulte también  
 [Miembros de SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Clase SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  

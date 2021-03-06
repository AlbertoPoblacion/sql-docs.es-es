---
title: Funciones de descriptor de acceso de datos | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- data-accessor functions [XQuery]
ms.assetid: 31bad04f-7c74-4773-9f83-612704fdd21c
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7a6b3cc974ae32047d88e1355a870cc97806c22d
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="data-accessor-functions"></a>Funciones del descriptor de acceso a datos
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  En los temas expuestos en esta sección se ofrecen descripciones y ejemplos de código para las funciones del descriptor de acceso a datos.  
  
## <a name="understanding-fndata-fnstring-and-text"></a>Información acerca de fn:data (), fn:string () y text()  
 XQuery tiene una función **fn:Data()** para extraer valores escalares con tipo de nodos, una prueba de nodo **text()** para devolver los nodos de texto y la función **fn:String()** que devuelve el valor de cadena de un nodo. Su uso puede resultar confuso. A continuación, se presentan las directrices para usarlas correctamente en [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. La instancia XML \<age > 12 \< /age > se utiliza con fines ilustrativos.  
  
-   XML sin tipo: la expresión de ruta de acceso /age/text() devuelve el nodo de texto "12". La función fn:data(/age) devuelve el valor de cadena "12", igual que fn:string(/age).  
  
-   XML con tipo: La expresión /age/text() devuelve un error estático para cualquier tipada simple \<age > elemento. Por otro lado, fn:data (/edad) devuelve el entero 12. La función fn:string(/age) produce la cadena "12".  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [cadena Function &#40; XQuery &#41;](../xquery/data-accessor-functions-string-xquery.md)  
  
-   [Función de datos &#40; XQuery &#41;](../xquery/data-accessor-functions-data-xquery.md)  
  
## <a name="see-also"></a>Vea también  
 [Expresiones de ruta de acceso &#40; XQuery &#41;](../xquery/path-expressions-xquery.md)  
  
  

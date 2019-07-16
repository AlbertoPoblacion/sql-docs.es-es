---
title: Aplicaciones personalizadas | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], custom applications
- custom applications [ODBC]
- interoperability [ODBC], levels
ms.assetid: f28178d9-ecd6-4e8c-9644-9bb624999dcb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 240bdf074fbe7fd28f5aafff5c1bbab7651d0c71
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067475"
---
# <a name="custom-applications"></a>Aplicaciones personalizadas
Aplicaciones personalizadas suelen realizan una tarea específica para algunos de los DBMS. Por ejemplo, una aplicación puede recuperar datos de un DBMS único y generar un informe, o pueden transferir datos entre varios de los DBMS. Lo que estas aplicaciones tienen en común es que estos DBMS se conocen antes de la aplicación está escrita y están poco probable que cambien el estado de la aplicación.  
  
 Por lo tanto, la aplicación personalizada requiere poca o ninguna interoperabilidad. El desarrollador de aplicaciones puede elegir un controlador único para cada DBMS y el código directamente a estos controladores. La aplicación sin ningún riesgo puede contener código específico del controlador para aprovechar las capacidades de los controladores e incluso puede realizar llamadas a la API de base de datos nativa para usar la funcionalidad no admitida por ODBC.  
  
 La preocupación de interoperabilidad principal de la mayoría de las aplicaciones personalizada es si el DBMS de destino se cambia en el futuro. Si es así, se puede simplificar este proceso al escribir código más interoperable para empezar. Sin embargo, este tipo de cambio de DBMS es poco frecuente y generalmente implica una gran cantidad de trabajo. Por este motivo, los desarrolladores de aplicaciones personalizadas que rara vez eligen aumentar la interoperabilidad a costa de funcionalidad; Normalmente, elegir codificar esa funcionalidad cuando cambian los DBMS.

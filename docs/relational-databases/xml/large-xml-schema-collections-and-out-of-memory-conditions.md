---
title: Las condiciones de memoria insuficiente y las grandes colecciones de esquemas XML | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- out-of-memory conditions
- XML schema collections [SQL Server], large
ms.assetid: 29b9d839-aaaf-48fb-be17-840c751f36f1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ed4c37b0768fa0869209f8795c81a57e76b5b93b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68026632"
---
# <a name="large-xml-schema-collections-and-out-of-memory-conditions"></a>Las condiciones de memoria insuficiente y las grandes colecciones de esquemas XML.
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Se puede producir una condición de memoria insuficiente durante una llamada a la función XML_SCHEMA_NAMESPACE() integrada de una colección de esquemas XML de gran tamaño o cuando intenta quitar colecciones de esquemas XML de gran tamaño. A continuación, se exponen las soluciones que se pueden aplicar en estos casos:  
  
-   Cuando la carga del sistema no es muy importante, use el comando DROP_XML_SCHEMA_COLLECTION. Si no funciona correctamente, ponga la base de datos en modo de usuario único mediante la instrucción ALTER DATABASE y vuelva a probar DROP XML SCHEMA COLLECTION. Si la colección de esquemas XML existe en **master**, **model**o **tempdb**, se deberá reiniciar el servidor para el modo de usuario único.  
  
-   Cuando llame a XML_SCHEMA_NAMESPACE, puede intentar recuperar un solo espacio de nombres XML, intentar realizar la llamada cuando la carga del sistema es menos importante o realizarla en modo de usuario único.  
  
## <a name="see-also"></a>Consulte también  
 [Requisitos y limitaciones de las colecciones de esquemas XML en el servidor](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  

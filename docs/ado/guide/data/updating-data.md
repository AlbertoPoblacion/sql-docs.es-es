---
title: Actualización de datos | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ADO], about data updates
- updating data [ADO], about updating data
ms.assetid: 6508e4e9-e33a-4dad-b340-5d632fd78a91
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5bd3b72e897b8ae12441c7cf28d1995eb45318d1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67923690"
---
# <a name="updating-data"></a>Actualizar datos
Comportamiento de actualización y la funcionalidad depende en gran medida actualizar modo (tipo de bloqueo), el tipo de cursor y la ubicación del cursor.  
  
 Use la **actualización** método para guardar los cambios realizados en el registro actual de un **Recordset** objetos desde que se llama el **AddNew** método o cambiando los valores de campo en un registro existente. El **Recordset** objeto debe admitir las actualizaciones.  
  
 Si el **Recordset** objeto admite la actualización por lotes, puede almacenar en caché los cambios de varios a uno o más registros localmente hasta que llame a la **UpdateBatch** método. Si está modificando el registro actual o agregando un nuevo registro al llamar a la **UpdateBatch** método, ADO llamará automáticamente a la **actualización** método para guardar los cambios pendientes en el registro actual antes de transmitir los cambios por lotes al proveedor.  
  
 El registro actual permanece actual después de llamar a la **actualización** o **UpdateBatch** métodos.  
  
 Esta sección contiene los temas siguientes.  
  
-   [Modo inmediato](../../../ado/guide/data/immediate-mode.md)  
  
-   [Modo por lotes](../../../ado/guide/data/batch-mode.md)  
  
-   [Procesamiento de transacciones](../../../ado/guide/data/transaction-processing.md)

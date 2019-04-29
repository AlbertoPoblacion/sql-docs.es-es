---
title: Modo de confirmación automática | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- auto-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: c8de5b60-d147-492d-b601-2eeae8511d00
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 491fb8db9e37cfb3bfa07881958fe7828e6bb911
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63048432"
---
# <a name="auto-commit-mode"></a>Modo de confirmación automática
*En el modo de confirmación automática,* cada operación de base de datos es una transacción que se confirma cuando se realiza. Este modo es adecuado para muchas transacciones reales que se componen de una sola instrucción SQL. No es necesario delimitar o especificar la finalización de estas transacciones. En las bases de datos sin compatibilidad con transacciones, modo de confirmación automática es el único modo admitido. En estas bases de datos, las instrucciones se confirman cuando se ejecutan y no hay ninguna manera de revertir ellos; por lo tanto, están siempre en modo de confirmación automática.  
  
 Si el DBMS subyacente no admite transacciones de modo de confirmación automática, el controlador puede emular confirmando manualmente cada instrucción SQL que se ejecuta.  
  
 Si un lote de instrucciones SQL se ejecuta en modo de confirmación automática, es específica del origen de datos cuando se confirman las instrucciones del lote. Se pueden confirmar mientras se ejecutan o como un todo después de haber ejecutado el lote completo. Algunos orígenes de datos pueden admitir tanto de estos comportamientos y pueden proporcionar una manera de seleccionar uno o los demás. En concreto, si se produce un error en medio del lote, es específica del origen de datos si las instrucciones ejecutadas ya se ha confirmado o revertidas. Por lo tanto, las aplicaciones interoperables que usan los lotes y requieran que se confirma o revierte como un todo deben ejecutar lotes solo en modo de confirmación manual.

---
title: 'Ejemplo: Cambio de nombre del elemento &lt;row&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, renaming <row> example
ms.assetid: b042292a-0b6e-40a3-b254-71c06e626706
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 275b1c6c138b11fa6330dc61fbfbfd2014a229c5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006805"
---
# <a name="example-renaming-the-ltrowgt-element"></a>Ejemplo: Cambio de nombre del elemento &lt;row&gt;
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  El modo RAW genera un elemento para cada fila del conjunto de resultados `<row>`. Opcionalmente, se puede indicar otro nombre para este elemento especificando un argumento opcional para el modo RAW, como se muestra en esta consulta. La consulta devuelve un elemento <`ProductModel`> para cada fila del conjunto de filas.  
  
## <a name="example"></a>Ejemplo  
  
```  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122  
FOR XML RAW ('ProductModel'), ELEMENTS  
GO  
```  
  
 Éste es el resultado. Dado que se agrega la directiva `ELEMENTS` en la consulta, el resultado está centrado en elementos.  
  
```  
<ProductModel>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</ProductModel>   
```  
  
## <a name="see-also"></a>Consulte también  
 [Usar el modo RAW con FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  

---
title: Funciones de XQuery con el tipo de datos xml | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, functions
- xml data type [SQL Server], XQuery
- functions [SQL Server], XQuery
ms.assetid: 8df0877d-a03f-4ca9-b84e-908c4bb42b5e
author: rothja
ms.author: jroth
ms.openlocfilehash: e885b537fbc86f3b70a8142c5513dbf16cb1c158
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67945995"
---
# <a name="xquery-functions-against-the-xml-data-type"></a>Funciones de XQuery con el tipo de datos xml
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  En este tema y sus temas secundarios describen las funciones que puede usar al especificar XQuery en el **xml** tipo de datos. Para las especificaciones del W3C, vea [ http://www.w3.org/TR/2004/WD-xpath-functions-20040723 ](https://go.microsoft.com/fwlink/?LinkId=4873).  
  
 Las funciones de XQuery pertenecen a la http://www.w3.org/2004/07/xpath-functions espacio de nombres. Las especificaciones de W3C utilizan el prefijo de espacio de nombres "fn": para describir estas funciones. No es necesario especificar explícitamente el prefijo de espacio de nombres "fn": cuando se utilicen estas funciones. Debido a esto y para facilitar la lectura, los prefijos de espacio de nombres no se suelen usar en esta documentación.  
  
 En la tabla siguiente se enumera las funciones de XQuery que se admiten con la **xml**tipo de datos.  
  
|Category|Nombre de la función|  
|--------------|-------------------|  
|[Funciones en valores numéricos](https://msdn.microsoft.com/library/d5740a32-b174-43b9-b64d-1cc6edc50cff)|[ceiling](../xquery/numeric-values-functions-ceiling.md)|  
||[floor](../xquery/numeric-values-functions-floor.md)|  
||[redondear](../xquery/numeric-values-functions-round.md)|  
|[Funciones de XQuery en valores de cadena](https://msdn.microsoft.com/library/2dccefef-5d90-4f56-bda7-4c1954d8a730)|[concat](../xquery/functions-on-string-values-concat.md)|  
||[contiene](../xquery/functions-on-string-values-contains.md)|  
||[substring](../xquery/functions-on-string-values-substring.md)|  
||[Función de letra minúscula &#40;XQuery&#41;](../xquery/functions-on-string-values-lower-case.md)|  
||[string-length](../xquery/functions-on-string-values-string-length.md)|  
||[Función mayúsculas &#40;XQuery&#41;](../xquery/functions-on-string-values-upper-case.md)|  
|Funciones usadas en valores booleanos|[not](../xquery/functions-on-boolean-values-not-function.md)|  
|[Funciones usadas en nodos](https://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)|[number](../xquery/functions-on-nodes-number.md)|  
||[Función local-name (XQuery)](../xquery/functions-on-nodes-local-name.md)|  
||[Función namespace-uri (XQuery)](../xquery/functions-on-nodes-namespace-uri.md)|  
|[Funciones de contexto](https://msdn.microsoft.com/library/f7d8af33-9de9-450c-a667-23dee3129b5f)|[last](../xquery/context-functions-last-xquery.md)|  
||[position](../xquery/context-functions-position-xquery.md)|  
|[Funciones usadas en secuencias](https://msdn.microsoft.com/library/672d2795-53ab-49c2-bf24-bc81a47ecd3f)|[vacío](../xquery/functions-on-sequences-empty.md)|  
||[distinct-values](../xquery/functions-on-sequences-distinct-values.md)|  
||[Id. de función (XQuery)](../xquery/functions-on-sequences-id.md)|  
|[Funciones de agregado &#40;XQuery&#41;](https://msdn.microsoft.com/library/be647ef1-291e-4a5d-ab18-07c759efe176)|[Recuento](../xquery/aggregate-functions-count.md)|  
||[avg](../xquery/aggregate-functions-avg.md)|  
||[min](../xquery/aggregate-functions-min.md)|  
||[max](../xquery/aggregate-functions-max.md)|  
||[sum](../xquery/aggregate-functions-sum.md)|  
|[Funciones de constructor &#40;XQuery&#41;](../xquery/constructor-functions-xquery.md)|[Funciones de constructor](../xquery/constructor-functions-xquery.md)|  
|[Funciones del descriptor de acceso a datos](../xquery/data-accessor-functions.md)|[string](../xquery/data-accessor-functions-string-xquery.md)|  
||[data](../xquery/data-accessor-functions-data-xquery.md)|  
|[Funciones de Constructor booleano &#40;XQuery&#41;](https://msdn.microsoft.com/library/fa907f39-d4b7-4495-b829-c788928e0f64)|[Función True (XQuery)](../xquery/boolean-constructor-functions-true-xquery.md)|  
||[Función false (XQuery)](../xquery/boolean-constructor-functions-false-xquery.md)|  
|[Funciones relacionadas con QNames &#40;XQuery&#41;](https://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)|[Expanded-QName (XQuery)](../xquery/functions-related-to-qnames-expanded-qname.md)|  
||[local-nombre-de-QName (XQuery)](../xquery/functions-related-to-qnames-local-name-from-qname.md)|  
||[espacio de nombres-uri-from-QName (XQuery)](../xquery/functions-related-to-qnames-namespace-uri-from-qname.md)|  
|[Funciones de extensión de SQL Server XQuery](https://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)|[función SQL:Column() (XQuery)](../xquery/xquery-extension-functions-sql-column.md)|  
||[función SQL:variable() (XQuery)](../xquery/xquery-extension-functions-sql-variable.md)|  
  
## <a name="see-also"></a>Vea también  
 [métodos del tipo de datos xml](../t-sql/xml/xml-data-type-methods.md)   
 [Referencia del lenguaje XQuery &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)   
 [Datos XML &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)  
  
  

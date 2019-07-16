---
title: Función Contains (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- contains function (XQuery)
- fn:contains function
ms.assetid: 2c88c015-04fc-429b-84b2-835596a28b65
author: rothja
ms.author: jroth
ms.openlocfilehash: 54b3603c18d814276d700a220fbee5e16ed77502
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67899025"
---
# <a name="functions-on-string-values---contains"></a>Funciones usadas en valores de cadena: contains
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Devuelve un valor de tipo xs: Boolean indicando si el valor de *$arg1* contiene un valor de cadena especificado por *$arg2*.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
fn:contains ($arg1 as xs:string?, $arg2 as xs:string?) as xs:boolean?  
```  
  
## <a name="arguments"></a>Argumentos  
 *$arg1*  
 Valor de cadena que se va a comprobar.  
  
 *$arg2*  
 Subcadena que se va a buscar.  
  
## <a name="remarks"></a>Comentarios  
 Si el valor de *$arg2* es una cadena de longitud cero, la función devuelve **True**. Si el valor de *$arg1* es una cadena de longitud cero y el valor de *$arg2* no es una cadena de longitud cero, la función devuelve **False**.  
  
 Si el valor de *$arg1* o *$arg2* es una secuencia vacía, el argumento se trata como la cadena de longitud cero.  
  
 La función contains() usa la intercalación de punto de código Unicode predeterminada de XQuery para la comparación de cadenas.  
  
 El valor de subcadena especificado para *$arg2* debe ser menor o igual que 4000 caracteres. Si el valor especificado es mayor que 4000 caracteres, se produce una condición de error dinámica y la función contains() devuelve una secuencia vacía en lugar de un valor booleano de **True** o **False**. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] no genera errores dinámicos en expresiones XQuery.  
  
 Para obtener las comparaciones entre mayúsculas y minúsculas, el [mayúsculas](../xquery/functions-on-string-values-upper-case.md) o se pueden usar funciones en minúsculas.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Caracteres adicionales (pares suplentes)  
 El comportamiento de pares suplentes en las funciones XQuery depende del nivel de compatibilidad de la base de datos y, en algunos casos, del URI del espacio de nombres predeterminado de las funciones. Para obtener más información, vea la sección "XQuery funciones detectan los caracteres suplentes" en el tema [cambios recientes en las características del motor de base de datos en SQL Server 2016](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md). Consulte también [nivel de compatibilidad de ALTER DATABASE &#40;Transact-SQL&#41; ](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) y [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Ejemplos  
 Este tema proporciona ejemplos de XQuery con instancias XML almacenadas en varias columnas de tipo xml en la base de datos AdventureWorks.  
  
### <a name="a-using-the-contains-xquery-function-to-search-for-a-specific-character-string"></a>A. Utilizar la función contains() de XQuery para buscar una cadena de caracteres específica  
 La consulta siguiente busca los productos que contengan la palabra Aerodynamic en las descripciones resumidas. La consulta devuelve el identificador de producto y la <`Summary`> (elemento) para dichos productos.  
  
```  
--The product model description document uses  
--namespaces. The WHERE clause uses the exit()  
--method of the xml data type. Inside the exit method,  
--the XQuery contains()function is used to  
--determine whether the <Summary> text contains the word  
--Aerodynamic.   
  
USE AdventureWorks  
GO  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT ProductModelID, CatalogDescription.query('  
      <Prod>  
         { /pd:ProductDescription/@ProductModelID }  
         { /pd:ProductDescription/pd:Summary }  
      </Prod>  
 ') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
   /pd:ProductDescription/pd:Summary//text()  
    [contains(., "Aerodynamic")]') = 1  
```  
  
 Resultados  
  
 `ProductModelID Result`  
  
 `-------------- ---------`  
  
 `28     <Prod ProductModelID="28">`  
  
 `<pd:Summary xmlns:pd=`  
  
 `"https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">`  
  
 `<p1:p xmlns:p1="http://www.w3.org/1999/xhtml">`  
  
 `A TRUE multi-sport bike that offers streamlined riding and`  
  
 `a revolutionary design. Aerodynamic design lets you ride with`  
  
 `the pros, and the gearing will conquer hilly roads.</p1:p>`  
  
 `</pd:Summary>`  
  
 `</Prod>`  
  
## <a name="see-also"></a>Vea también  
 [Funciones de XQuery con el tipo de datos xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  

---
title: 'Apéndice B: Las tablas de transición de estado de ODBC | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- state transitions [ODBC]
- transitioning states [ODBC], about state transitions
- state transitions [ODBC], about state transitions
ms.assetid: 15088dbe-896f-4296-b397-02bb3d0ac0fb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7ceb128aec3a4cbe5ef7180483eb2a033ae57138
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67996243"
---
# <a name="appendix-b-odbc-state-transition-tables"></a>Apéndice B: Tablas de transición de estado de ODBC
Las tablas de este apéndice muestran cómo hacen que las transiciones del entorno, conexión, instrucción y Estados de descriptor funciones ODBC. El estado del entorno, conexión, instrucción o descriptor determina normalmente cuando se pueden llamar funciones que usan el tipo de identificador (entorno, conexión, instrucción o descriptor) correspondiente. Los Estados del entorno, conexión, instrucción y descriptor se superponen aproximadamente como se muestra en las siguientes ilustraciones. Por ejemplo, la superposición de conexión exacta Estados C5 y C6 y Estados de instrucción que s1 a través de S12 es depende del origen de datos, ya que las transacciones comienzan en momentos diferentes en distintos orígenes de datos, y depende del estado de descriptor D1i (implícitamente asignados descriptor) en el estado de la instrucción que está asociado el descriptor de, al estado D1e (asignado explícitamente descriptor) es independiente del estado de cualquier instrucción. Para obtener una descripción de cada estado, vea [transiciones de entorno](../../../odbc/reference/appendixes/environment-transitions.md), [transiciones de conexión](../../../odbc/reference/appendixes/connection-transitions.md), [transiciones de instrucción](../../../odbc/reference/appendixes/statement-transitions.md), y [transiciones de Descriptor ](../../../odbc/reference/appendixes/descriptor-transitions.md), más adelante en este apéndice.  
  
 Los Estados del entorno y la conexión se superponen como sigue:  
  
 ![Estados del entorno y la conexión se superponen](../../../odbc/reference/appendixes/media/app01.gif "app01")  
  
 Los Estados de conexión y la instrucción se superponen como sigue:  
  
 ![Estados de conexión y la instrucción se superponen](../../../odbc/reference/appendixes/media/app02.gif "app02")  
  
 Los Estados de instrucción y el descriptor se superponen como sigue:  
  
 ![Estados de instrucción y el descriptor se superponen](../../../odbc/reference/appendixes/media/app03.gif "app03")  
  
 Los Estados de conexión y el descriptor se superponen como sigue:  
  
 ![Estados de conexión y el descriptor se superponen](../../../odbc/reference/appendixes/media/app04.gif "app04")  
  
 Cada entrada en una tabla de transición puede ser uno de los siguientes valores:  
  
-   **--** -El estado no se modifica después de ejecutar la función.  
  
-   **E**  

     **_n_**  , **C_n_** , **S_n_** , o **D_n_** -el estado del entorno, conexión, instrucción o descriptor pasa al estado especificado.  
 
-   **(IH)**  : Un identificador no válido se pasó a la función. Si el identificador era un identificador nulo o un identificador válido de un tipo incorrecto: por ejemplo, se pasó un identificador de conexión cuando se requiere un identificador de instrucción: la función devuelva SQL_INVALID_HANDLE; en caso contrario, el comportamiento es indefinido y probablemente irrecuperable. Este error se muestra solo cuando es sólo posible resultado de llamar a la función en el estado especificado. Este error no cambia el estado y siempre se detecta mediante el Administrador de controladores, como se indica entre paréntesis.  
  
-   **NS** -estado siguiente. La transición de la instrucción es el mismo que si la instrucción no había pasado por los Estados asincrónicos. Por ejemplo, suponga que una instrucción que crea un conjunto de resultados entra en estado S11 en estado S1 porque **SQLExecDirect** devuelve SQL_STILL_EXECUTING. La notación de NS en estado S11 significa que las transiciones para la instrucción son los mismos que los de una instrucción en estado S1 que crea un conjunto de resultados. Si **SQLExecDirect** devuelve un error, la instrucción permanece en estado S1; si se realiza correctamente, la instrucción se mueve al estado S5; si necesita datos, la instrucción se mueve al estado S8; y si todavía se está ejecutando, permanece en estado S11.  

-   **_XXXXX_**  o **(*XXXXX*)** : SQLSTATE, que está relacionado con la tabla de transición; SQLSTATE detectado por el Administrador de controladores se incluyen entre paréntesis. La función devuelve SQL_ERROR y el valor de SQLSTATE especificado, pero no cambia el estado. Por ejemplo, si **SQLExecute** se llama antes de **SQLPrepare**, devuelve SQLSTATE HY010 (función de error de secuencia).  

> [!NOTE]  
>  Las tablas no muestran errores no relacionados con las tablas de transición que no cambian el estado. Por ejemplo, cuando **SQLAllocHandle** se llama en el estado del entorno E1 y devuelve SQLSTATE HY001 (error de asignación de memoria), el entorno permanece en estado E1; esto no se muestra en la tabla de transiciones de entorno para  **SQLAllocHandle**.  
  
 Si el entorno, conexión, instrucción o descriptor puede mover a más de un estado, se muestra cada posible estado y una o varias de las notas al pie explican las condiciones en las que realiza cada transición. Las notas al pie siguientes pueden aparecer en cualquier tabla.  
  
|Nota al pie|Significado|  
|--------------|-------------|  
|b|Antes o después. El cursor se coloca antes del inicio del conjunto de resultados o después del final del conjunto de resultados.|  
|c|Función actual. La función actual se estaba ejecutando de forma asincrónica.|  
|d|Necesita los datos. La función devuelve SQL_NEED_DATA.|  
|e|Error. La función devuelve SQL_ERROR.|  
|i|Fila no válida. El cursor se coloca en una fila en el resultado se había eliminados conjunto y la fila o se ha producido un error en una operación en la fila. Si existiera la matriz de Estados de fila, el valor de la matriz de estado de fila para la fila era SQL_ROW_DELETED o SQL_ROW_ERROR. (La matriz de Estados de fila está indicada por el atributo de instrucción SQL_ATTR_ROW_STATUS_PTR.)|  
|NF|No se encontró. La función devuelve SQL_NO_DATA. Esto no es aplicable cuando **SQLExecDirect**, **SQLExecute**, o **SQLParamData** devuelve SQL_NO_DATA después de ejecutar una búsqueda instrucción update o delete.|  
|np|No preparado. No se ha preparado la instrucción.|  
|nr|No hay resultados. La instrucción no puede o no ha creado un conjunto de resultados.|  
|o|Otra función. Otra función se estaba ejecutando de forma asincrónica.|  
|p|Preparado. Se ha preparado la instrucción.|  
|r|Resultados. La instrucción se o ha creado un conjunto de resultados (posiblemente vacía).|  
|s|Correcto. La función devuelve SQL_SUCCESS_WITH_INFO o SQL_SUCCESS.|  
|v|Fila válida. El cursor se coloca en una fila del conjunto de resultados y tenía insertó correctamente la fila se actualizó correctamente, o cualquier otra operación en la fila se había completado correctamente. Si existiera la matriz de Estados de fila, el valor de la matriz de estado de fila para la fila era SQL_ROW_ADDED, SQL_ROW_SUCCESS o SQL_ROW_UPDATED. (La matriz de Estados de fila está indicada por el atributo de instrucción SQL_ATTR_ROW_STATUS_PTR.)|  
|x|En ejecución. La función devuelve SQL_STILL_EXECUTING.|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 En este ejemplo, la fila de la transición de estado del entorno de tabla para **SQLFreeHandle** cuando *HandleType* es SQL_HANDLE_ENV es como sigue.  
  
|E0<br /><br /> Sin asignar|E1<br /><br /> asignado|E2<br /><br /> Conexión|  
|------------------------|----------------------|-----------------------|  
|(IH)|E0|(HY010)|  
  
 Si **SQLFreeHandle** se llama en el estado del entorno E0 con *HandleType* establecido en SQL_HANDLE_ENV, el Administrador de controladores devuelva SQL_INVALID_HANDLE. Si se llama en estado E1 con *HandleType* establecido en SQL_HANDLE_ENV, el entorno se mueve al estado E0 si la función se realiza correctamente y permanece en estado E1 si se produce un error en la función. Si se llama en estado E2 con *HandleType* establecido en SQL_HANDLE_ENV, el Administrador de controladores siempre devuelve SQL_ERROR y SQLSTATE HY010 (función de error de secuencia) y el entorno permanece en estado E2.  
  
 Para comprender las tablas de transición de estado, es necesario comprender qué elemento (entorno, conexión, instrucción o descriptor) hacen referencia. Supongamos que una función acepta el identificador de un elemento del tipo X. La tabla de transiciones de estado X para esa función describe cómo llamar a la función con el identificador de un elemento de tipo X, afecta a ese elemento. Por ejemplo, **SQLDisconnect** acepta un identificador de conexión. La tabla de transiciones de estado de conexión para **SQLDisconnect** describe cómo **SQLDisconnect** afecta al estado de la conexión para el que se llama.  
  
 Supongamos que una función acepta el identificador de un elemento de tipo S, donde Y no es igual a X. La tabla de transiciones de estado X para esa función describe cómo llamar a la función con un identificador de tipo X que está asociado con el elemento de tipo Y, afecta al elemento de tipo Y. Por ejemplo, la instrucción transición tabla de estado para **SQLDisconnect** describe cómo **SQLDisconnect** afecta al estado de una instrucción cuando se llama con el identificador de la conexión con el que el instrucción está asociada.  
  
 Este apéndice contiene los temas siguientes.  
  
-   [Transiciones de entorno](../../../odbc/reference/appendixes/environment-transitions.md)  
  
-   [Transiciones de conexión](../../../odbc/reference/appendixes/connection-transitions.md)  
  
-   [Transiciones de instrucción](../../../odbc/reference/appendixes/statement-transitions.md)  
  
-   [Transiciones de descriptor](../../../odbc/reference/appendixes/descriptor-transitions.md)

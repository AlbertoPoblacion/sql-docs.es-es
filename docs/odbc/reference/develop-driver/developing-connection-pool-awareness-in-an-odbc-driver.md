---
title: Desarrollar el conocimiento de la agrupación de conexiones en un controlador ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c63d5cae-24fc-4fee-89a9-ad0367cddc3e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b82e56dd7998ca19ce9e401369cd8d2f52b58573
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62636241"
---
# <a name="developing-connection-pool-awareness-in-an-odbc-driver"></a>Desarrollar el conocimiento de la agrupación de conexiones en un controlador ODBC
En este tema se trata los detalles del desarrollo de un controlador ODBC que contiene información sobre cómo el controlador debe proporcionar servicios de agrupación de conexiones.  
  
## <a name="enabling-driver-aware-connection-pooling"></a>Habilitar la agrupación de conexiones dependientes del controlador  
 Un controlador debe implementar las siguientes funciones de interfaz de proveedor de servicios (SPI) de ODBC:  
  
-   SQLSetConnectAttrForDbcInfo  
  
-   SQLSetConnectInfo  
  
-   SQLSetDriverConnectInfo  
  
-   SQLGetPoolID  
  
-   SQLRateConnection  
  
-   SQLPoolConnect  
  
-   SQLCleanupConnectionPoolID  
  
 Consulte [referencia de la interfaz de proveedor de servicios (SPI) de ODBC](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md) para obtener más información.  
  
 Un controlador también debe implementar las siguientes funciones existentes para que se puede habilitar la agrupación dependientes del controlador:  
  
|Función|Funcionalidad agregada|  
|--------------|-------------------------|  
|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)<br /><br /> [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)<br /><br /> [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|Compatibilidad con el nuevo tipo de identificador: SQL_HANDLE_DBC_INFO_TOKEN (consulte la siguiente descripción).|  
|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|Compatibilidad con el nuevo atributo solo para establecer conexión: SQL_ATTR_DBC_INFO_TOKEN para restablecer la conexión (consulte la siguiente descripción).|  
  
> [!NOTE]  
>  Funciones en desuso, como **SQLError** y **SQLSetConnectOption** no se admiten para la agrupación de conexiones dependientes del controlador.  
  
## <a name="the-pool-id"></a>El identificador del grupo  
 El identificador del grupo es un identificador de específicas del controlador de longitud de puntero para representar un determinado grupo de conexiones que se pueden usar indistintamente. Dado un conjunto de información de conexión, un controlador debe ser capaz de deducir rápidamente el identificador de grupo correspondiente.  
  
 Por ejemplo, el identificador del grupo debe codificar la información de nombre y las credenciales del servidor. Sin embargo, el nombre de la base de datos no es necesario porque un controlador puede reutilizar una conexión y, a continuación, cambie la base de datos en menos tiempo que establecer una conexión nueva.  
  
 Un controlador debe definir un conjunto de atributos claves que conformarán el identificador de grupo. El valor de estos atributos clave puede proceder de los atributos de conexión, la cadena de conexión y el DSN. En caso de que hay algún conflicto de estos orígenes, la directiva de resolución existente, específicos del controlador debe usarse para la compatibilidad con versiones anteriores.  
  
 El Administrador de controladores se utilizará un grupo diferente para diferentes identificadores del grupo. Todas las conexiones en el mismo grupo son reutilizables. El Administrador de controladores nunca volverá a usar una conexión con un identificador de otro grupo.  
  
 Por lo tanto, los controladores deben asignar un identificador de grupo único para cada grupo de conexiones con el mismo valor en sus atributos claves definidos. Si un controlador utiliza el mismo identificador de grupo para las dos conexiones con diferentes valores en sus atributos claves, el Administrador de controladores se colocará todavía en el mismo grupo (el Administrador de controladores sabe nada acerca de los atributos claves específicos del controlador). Esto significa que el controlador necesita informar al administrador de controladores que no es reutilizable dentro de una conexión con un conjunto diferente de atributos clave [función SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md). Esto puede reducir el rendimiento y no se recomienda.  
  
 El Administrador de controladores no volverá a usar una conexión asignada en otro entorno de controlador, incluso si coincide con toda la información de conexión. El Administrador de controladores usará un grupo diferente para un entorno diferente, incluso cuando las conexiones tienen el mismo identificador de grupo. Por lo tanto, el identificador del grupo es local en su entorno de controlador.  
  
 La función para obtener el identificador del grupo desde el controlador es [función SQLGetPoolID](../../../odbc/reference/syntax/sqlgetpoolid-function.md).  
  
## <a name="the-connection-rating"></a>La clasificación de conexión  
 En comparación con establecimiento de una conexión nueva, puede obtener un mejor rendimiento al restablecer la información de conexión (por ejemplo, la base de datos) en una conexión agrupada. Por lo tanto, es posible que no desea que el nombre de la base de datos en el conjunto de atributos de clave. En caso contrario, puede tener un grupo independiente para cada base de datos que no puedan ser buena en aplicaciones de niveles intermedio, donde los clientes usar distintas cadenas de conexión diferentes.  
  
 Cada vez que se reutiliza una conexión que tiene algún error de coincidencia de atributo, debe restablecer los atributos que no coincidentes en función de la nueva solicitud de aplicación, para que la conexión devuelta es idéntica a la solicitud de aplicación (vea la explicación del atributo SQL_ATTR _DBC_INFO_TOKEN en [función SQLSetConnectAttr](https://go.microsoft.com/fwlink/?LinkId=59368)). Sin embargo, al restablecer los atributos puede disminuir el rendimiento. Por ejemplo, el restablecimiento de una base de datos requiere una llamada de red al servidor. Volver a usar una conexión que coincide perfectamente, por lo tanto, si está disponible.  
  
 Una función de clasificación en el controlador puede evaluar una conexión existente con una nueva solicitud de conexión. Por ejemplo, puede determinar la función del controlador clasificación:  
  
-   Si la conexión existente coincide perfectamente con la solicitud.  
  
-   Si hay solo algunos insignificantes discrepancias, como el tiempo de espera de conexión, que no requieren comunicación con el servidor para restablecer.  
  
-   Si hay algunos atributos no coincidentes que requieren una comunicación con el servidor para restablecer pero todavía daría como resultado un mejor rendimiento que establecer una nueva conexión.  
  
-   Si el no coincidentes se ha producido para un atributo que llevará mucho tiempo restablecer (el desarrollador del controlador es posible que considere la posibilidad de agregar este atributo en el conjunto de atributos clave, que se usa para generar el identificador del grupo).  
  
 Una puntuación entre 0 y 100 es posible, donde 0 significa no reutilice y 100 significa que coincide perfectamente. [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md) es la función para la evaluación de una conexión.  
  
## <a name="new-odbc-handle---sqlhandledbcinfotoken"></a>Nuevo identificador ODBC - SQL_HANDLE_DBC_INFO_TOKEN  
 Para admitir la agrupación de conexiones dependientes del controlador, el controlador necesita información de conexión para calcular el identificador de grupo. El controlador también necesita información de conexión para comparar las nuevas solicitudes de conexión con las conexiones en el grupo.  Cada vez que no se puede reutilizar conexión en el grupo, el controlador tiene que establecer una conexión nueva, por lo tanto, que requieren información de conexión.  
  
 Dado que la información de conexión puede proceder de varios orígenes (cadena de conexión, los atributos de conexión y DSN), el controlador que tenga analizar la cadena de conexión y resolver el conflicto entre estos orígenes en cada una de la llamada de función anterior.  
  
 Por lo tanto, se introduce un nuevo controlador ODBC: SQL_HANDLE_DBC_INFO_TOKEN. Con SQL_HANDLE_DBC_INFO_TOKEN, un controlador no debe analizar la cadena de conexión y resolver conflictos en la información de conexión de más de una vez. Puesto que se trata de una estructura de datos específicos del controlador, el controlador puede almacenar datos como la información de conexión o Id. de grupo  
  
 Este identificador se usa solo como una interfaz entre el Administrador de controladores y el controlador. Una aplicación no puede asignar directamente a este identificador.  
  
 El identificador de elemento primario de este identificador es de tipo SQL_HANDLE_ENV, lo que significa que el controlador puede obtener la información del entorno desde el controlador HENV durante la resolución de la información de conexión.  
  
 Cada vez que reciba una nueva solicitud de conexión, el Administrador de controladores asignará un identificador de tipo SQL_HANDLE_DBC_INFO_TOKEN para almacenar información de conexión, una vez que confirma que el controlador admite reconocimiento de la agrupación de conexiones. Cuando termine de utilizar el identificador (pero antes de devolver algunas devuelven códigos distinto de SQL_STILL_EXECUTING desde [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) o [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)), el Administrador de controladores liberará el identificador. Por lo tanto, el identificador se creó después de la llamada SQLAllocHandle y se destruye después de la llamada SQLFreeHandle. El Administrador de controladores garantiza que el identificador se liberará antes de liberar su HENV asociado (al [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) o [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) devuelve un error).  
  
 El controlador debe modificar las siguientes funciones para aceptar el nuevo tipo de identificador SQL_HANDLE_DBC_INFO_TOKEN:  
  
1.  [SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
2.  [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)  
  
3.  [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
4.  [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
 El Administrador de controladores garantiza que varios subprocesos no usará el mismo identificador SQL_HANDLE_DBC_INFO_TOKEN simultáneamente. Por lo tanto, el modelo de sincronización de este identificador puede ser muy simple dentro del controlador. El Administrador de controladores no tienen un bloqueo de entorno antes de asignar y liberar SQL_HANDLE_DBC_INFO_TOKEN.  
  
 El Administrador de controladores **SQLAllocHandle** y **SQLFreeHandle** no aceptará este nuevo tipo de identificador.  
  
 SQL_HANDLE_DBC_INFO_TOKEN puede contener información confidencial, como las credenciales. Por lo tanto, un controlador de forma segura debe borrar el búfer de memoria (con [SecureZeroMemory](https://msdn.microsoft.com/library/windows/desktop/aa366877\(v=vs.85\).aspx)) que contiene la información confidencial antes de liberar este identificador con **SQLFreeHandle**. Cada vez que se cierra el identificador de entorno de la aplicación, se cerrará todos los grupos de conexión asociada.  
  
## <a name="driver-manager-connection-pool-rating-algorithm"></a>Grupo de conexiones del Administrador de controladores algoritmo de clasificación  
 Esta sección describe el algoritmo de clasificación para la agrupación de conexiones de administrador de controladores. Los desarrolladores de controladores pueden implementar el mismo algoritmo para la compatibilidad con versiones anteriores. Este algoritmo es posible que no sea la mejor. Debe ajustar este algoritmo basa la implementación (en caso contrario, no hay ninguna razón para implementar esta característica).  
  
 El Administrador de controladores se devolverán una calificación de entera de 0 a 100 para cada conexión del grupo. 0 significa que no se puede reutilizar la conexión y 100 indica que coincide con una solución perfecta. Suponga que la solicitud de conexión se denomina hRequest y la conexión existente del grupo se denomina hCandidate. Si cualquiera de las condiciones siguientes es false, no se puede reutilizar el hCandidate conexión agrupada para hRequest (el Administrador de controladores asignará una clasificación de 0).  
  
-   hCandidate y hRequest proceden de la API de UNICODE (por ejemplo, SQLDriverConnectW) o las API de ANSI (por ejemplo, SQLDriverConnectA). (Los controladores UNICODE pueden comportamiento diferente según la API de ANSI y UNICODE API (consulte el atributo de conexión SQL_ATTR_ANSI_APP)).  
  
-   hCandidate y hRequest se crean mediante la misma función; SQLDriverConnect o SQLConnect.  
  
-   La cadena de conexión utilizada para abrir hCandidate debe ser el mismo que hRequest, cuando se usa SQLDriverConnect.  
  
-   El nombre de usuario ServerName (o DSN) y la contraseña usada para abrir hCandidate debe ser el mismo que el que se usa para abrir hRequest cuando se usa SQLConnect.  
  
-   El identificador de seguridad (SID) del subproceso actual debe ser el mismo como el SID se utiliza para abrir hCandidate.  
  
-   Controlador que resulta caro dar de alta y dar de baja (consulte la explicación SQL_DTC_TRANSITION_COST en [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)), reutilizar *hRequest* no debe requerir una inscripción adicional ni unenlistment.  
  
 En la tabla siguiente muestra la asignación de puntuación para diferentes escenarios.  
  
|Comparación de los atributos de conexión entre la conexión agrupada y la solicitud|Ninguna alta / unenlistment|Requerir la inscripción adicional / Unenlistment|  
|---------------------------------------------------------------------------------------|-----------------------------------|----------------------------------------------|  
|Catálogo (SQL_ATTR_CURRENT_CATALOG) es diferente|60|50|  
|Algunos atributos de conexión son diferentes, pero el catálogo es el mismo|90|70|  
|Todos los atributos de conexión coincide perfectamente|100|80|  
  
## <a name="sequence-diagram"></a>Diagrama de secuencia  
 Este diagrama de secuencia muestra el mecanismo de agrupación básico descrito en este tema. Solo muestra el uso de [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) pero la [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) caso es similar.  
  
 ![Diagrama de secuencia](../../../odbc/reference/develop-driver/media/odbc_seq_dia.gif "odbc_seq_dia")  
  
## <a name="state-diagram"></a>Diagrama de estado  
 Este diagrama de estado muestra la información token objeto de conexión, que se describe en este tema. El diagrama solo muestra [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) pero la [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) caso es similar. Puesto que el Administrador de controladores que deba controlar los errores en cualquier momento, el Administrador de controladores puede llamar a [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md) para cualquier estado.  
  
 ![Diagrama de estado](../../../odbc/reference/develop-driver/media/odbc_state_diagram.gif "odbc_state_diagram")  
  
## <a name="see-also"></a>Vea también  
 [Agrupación de conexiones dependientes del controlador](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Referencia de la interfaz del proveedor de servicios (SPI) de ODBC](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)

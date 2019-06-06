---
title: Índice de propiedades dinámicas de ADO | Microsoft Docs
ms.prod: sql
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- dynamic properties [ADO], index
ms.assetid: 80d389dd-46ef-459f-b0d4-6f712fc4f32d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8dd1263d19972124166e1e11d91c8370fc3a9ff0
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66696734"
---
# <a name="ado-dynamic-property-index"></a>Índice de propiedades dinámicas de ADO
Proveedores de datos, los proveedores de servicios y componentes de servicio pueden agregar propiedades dinámicas a la **propiedades** colecciones de la no abierto [conexión](../../../ado/reference/ado-api/connection-object-ado.md) y [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objetos. Un proveedor determinado también puede insertar propiedades adicionales cuando se abren estos objetos. Algunas de estas propiedades se muestran en el [propiedades dinámicas de ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md) sección. Aparecen más bajo los proveedores concretos en el [Apéndice A: Proveedores](../../../ado/guide/appendixes/appendix-a-providers.md) sección.  
  
 Las tablas siguientes son cross-indexes de nombres ADO y OLE DB para cada propiedad dinámica del proveedor OLE DB estándar. Los proveedores pueden agregar más propiedades a las enumeradas aquí. Para obtener la información específica acerca de las propiedades dinámicas específicas del proveedor, consulte la documentación del proveedor.  
  
 Referencia de la base de datos del programador de OLE se refiere a un nombre de la propiedad ADO con el término "Description". Para obtener más información acerca de estas propiedades estándares, busque o examine el índice en el [documentación de OLE DB](https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx)para la propiedad de OLE DB por su nombre.  
  
## <a name="connection-dynamic-properties"></a>Propiedades dinámicas de conexión  
  
|Nombre de la propiedad ADO|Nombre de propiedad OLE DB|  
|-----------------------|--------------------------|  
|Sesiones activas|DBPROP_ACTIVESESSIONS|  
|Anulación asincrónica|DBPROP_ASYNCTXNABORT|  
|Confirmación asíncrona|DBPROP_ASYNCTNXCOMMIT|  
|Niveles de aislamiento de confirmación automática|DBPROP_SESS_AUTOCOMMITISOLEVELS|  
|Ubicación del catálogo|DBPROP_CATALOGLOCATION|  
|Término de catálogo|DBPROP_CATALOGTERM|  
|Definición de columna|DBPROP_COLUMNDEFINITION|  
|Tiempo de espera de la conexión|DBPROP_INIT_TIMEOUT|  
|Catálogo actual|DBPROP_CURRENTCATALOG|  
|Origen de datos|DBPROP_INIT_DATASOURCE|  
|Data Source Name|DBPROP_DATASOURCENAME|  
|Objeto de origen de datos modelo de subprocesos|DBPROP_DSOTHREADMODEL|  
|Nombre DBMS|DBPROP_DBMSNAME|  
|Versión DBMS|DBPROP_DBMSVER|  
|Propiedades extendidas|DBPROP_INIT_PROVIDERSTRING|  
|Compatibilidad GROUP BY|DBPROP_GROUPBY|  
|Compatibilidad con tablas heterogéneas|DBPROP_HETEROGENEOUSTABLES|  
|Minúsculas en identificadores|DBPROP_IDENTIFIERCASE|  
|Catálogo original|DBPROP_INIT_CATALOG|  
|Niveles de aislamiento|DBPROP_SUPPORTEDTXNISOLEVELS|  
|Retención de aislamiento|DBPROP_SUPPORTEDTXNISORETAIN|  
|Identificador de configuración regional|DBPROP_INIT_LCID|  
|Location|DBPROP_INIT_LOCATION|  
|Tamaño máximo de índice|DBPROP_MAXINDEXSIZE|  
|Tamaño máximo de fila|DBPROP_MAXROWSIZE|  
|Tamaño máximo de fila incluye BLOB|DBPROP_MAXROWSIZEINCLUDESBLOB|  
|Número máximo de tablas en SELECT|DBPROP_MAXTABLESINSELECT|  
|Modo|DBPROP_INIT_MODE|  
|Varios conjuntos de parámetros|DBPROP_MULTIPLEPARAMSETS|  
|Varios resultados|DBPROP_MULTIPLERESULTS|  
|Varios objetos de almacenamiento|DBPROP_MULTIPLESTORAGEOBJECTS|  
|Actualización de varias tablas|DBPROP_MULTITABLEUPDATE|  
|Orden de intercalación de NULL|DBPROP_NULLCOLLATION|  
|Comportamiento de concatenación de NULL|DBPROP_CONCATNULLBEHAVIOR|  
|Servicios OLE DB|DBPROP_INIT_OLEDBSERVICES|  
|Versión OLE DB|DBPROP_PROVIDEROLEDBVER|  
|Compatibilidad con objetos OLE|DBPROP_OLEOBJECTS|  
|Conjunto de filas abierto|DBPROP_OPENROWSETSUPPORT|  
|Columnas ORDER BY en la lista de selección|DBPROP_ORDERBYCOLUMNSINSELECT|  
|Disponibilidad de parámetro de salida|DBPROP_OUTPUTPARAMETERAVAILABILITY|  
|Pasar por Ref descriptores de acceso|DBPROP_BYREFACCESSORS|  
|Contraseña|DBPROP_AUTH_PASSWORD|  
|Persist Security Info|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|  
|Tipo de Id.|DBPROP_PERSISTENTIDTYPE|  
|Preparar el comportamiento de anulación|DBPROP_PREPAREABORTBEHAVIOR|  
|Preparar el comportamiento de confirmación|DBPROP_PREPARECOMMITBEHAVIOR|  
|Término de procedimiento|DBPROP_PROCEDURETERM|  
|Pedir datos|DBPROP_INIT_PROMPT|  
|Nombre descriptivo del proveedor|DBPROP_PROVIDERFRIENDLYNAME|  
|Provider Name|DBPROP_PROVIDERFILENAME|  
|Versión del proveedor|DBPROP_PROVIDERVER|  
|Origen de datos de solo lectura|DBPROP_DATASOURCEREADONLY|  
|Conversiones de conjunto de filas en el comando|DBPROP_ROWSETCONVERSIONSONCOMMAND|  
|Término de esquema|DBPROP_SCHEMATERM|  
|Uso del esquema|DBPROP_SCHEMAUSAGE|  
|Compatibilidad con SQL|DBPROP_SQLSUPPORT|  
|Almacenamiento estructurado|DBPROP_STRUCTUREDSTORAGE|  
|Compatibilidad para subconsultas|DBPROP_SUBQUERIES|  
|Término de tabla|DBPROP_TABLETERM|  
|Transacción de DDL|DBPROP_SUPPORTEDTXNDDL|  
|Id. de usuario|DBPROP_AUTH_USERID|  
|Nombre de usuario|DBPROP_USERNAME|  
|Identificador de ventana|DBPROP_INIT_HWND|  
  
## <a name="recordset-dynamic-properties"></a>Propiedades del conjunto de registros dinámicos  
 Tenga en cuenta que el **propiedades dinámicas** de la **Recordset** objeto vaya fuera del ámbito (no están disponible) cuando el **Recordset** está cerrado.  
  
|Nombre de la propiedad ADO|Nombre de propiedad OLE DB|  
|-----------------------|--------------------------|  
|IAccessor|DBPROP_IACCESSOR|  
|IChapteredRowset||  
|IColumnsInfo|DBPROP_ICOLUMNSINFO|  
|IColumnsRowset|DBPROP_ICOLUMNSROWSET|  
|IConnectionPointContainer|DBPROP_ICONNECTIONPOINTCONTAINER|  
|IConvertType||  
|ILockBytes|DBPROP_ILOCKBYTES|  
|IRowset|DBPROP_IROWSET|  
|IDBAsynchStatus|DBPROP_IDBASYNCHSTATUS|  
|IParentRowset||  
|IRowsetChange|DBPROP_IROWSETCHANGE|  
|IRowsetExactScroll||  
|IRowsetFind|DBPROP_IROWSETFIND|  
|IRowsetIdentity|DBPROP_IROWSETIDENTITY|  
|IRowsetInfo|DBPROP_IROWSETINFO|  
|IRowsetLocate|DBPROP_IROWSETLOCATE|  
|IRowsetRefresh|DBPROP_IROWSETREFRESH|  
|IRowsetResynch||  
|IRowsetScroll|DBPROP_IROWSETSCROLL|  
|IRowsetUpdate|DBPROP_IROWSETUPDATE|  
|IRowsetView|DBPROP_IROWSETVIEW|  
|IRowsetIndex|DBPROP_IROWSETINDEX|  
|ISequentialStream|DBPROP_ISEQUENTIALSTREAM|  
|IStorage|DBPROP_ISTORAGE|  
|IStream|DBPROP_ISTREAM|  
|ISupportErrorInfo|DBPROP_ISUPPORTERRORINFO|  
|Orden de acceso|DBPROP_ACCESSORDER|  
|Conjunto de filas de sólo anexar|DBPROP_APPENDONLY|  
|Procesamiento de conjunto de filas asincrónico|DBPROP_ROWSET_ASYNCH|  
|Recálculo automático|DBPROP_ADC_AUTORECALC|  
|Tamaño de captura en segundo plano|DBPROP_ASYNCHFETCHSIZE|  
|Prioridad de los subprocesos en segundo plano|DBPROP_ASYNCHTHREADPRIORITY|  
|Tamaño de lote|DBPROP_ADC_BATCHSIZE|  
|Bloquear objetos de almacenamiento|DBPROP_BLOCKINGSTORAGEOBJECTS|  
|Tipo de marcador|DBPROP_BOOKMARKTYPE|  
|Admite marcadores|DBPROP_IROWSETLOCATE|  
|Marcadores solicitados|DBPROP_ORDEREDBOOKMARKS|  
|Almacenar en caché las filas secundarias|DBPROP_ADC_CACHECHILDROWS|  
|Almacenar en caché columnas aplazadas|DBPROP_CACHEDEFERRED|  
|Cambiar filas insertadas|DBPROP_CHANGEINSERTEDROWS|  
|Privilegios de columna|DBPROP_COLUMNRESTRICT|  
|Notificación de conjunto de columnas|DBPROP_NOTIFYCOLUMNSET|  
|Escritura de la columna|DBPROP_MAYWRITECOLUMN|  
|Tiempo de espera de comando|DBPROP_COMMANDTIMEOUT|  
|Versión del motor de cursor|DBPROP_ADC_CEVER|  
|Aplazar la columna|DBPROP_DEFERRED|  
|Actualizaciones de objetos de almacenamiento de retraso|DBPROP_DELAYSTORAGEOBJECTS|  
|Buscar hacia atrás|DBPROP_CANFETCHBACKWARDS|  
|Operaciones de filtro|DBPROP_FILTERCOMPAREOPS|  
|Operaciones de búsqueda|DBPROP_FINDCOMPAREOPS|  
|Columnas ocultas (recuento)|DBPROP_HIDDENCOLUMNS|  
|Conservar filas|DBPROP_CANHOLDROWS|  
|Filas inmóviles|DBPROP_IMMOBILEROWS|  
|Tamaño de captura inicial|DBPROP_ASYNCHPREFETCHSIZE|  
|Marcadores literales|DBPROP_LITERALBOOKMARKS|  
|Identidad de fila literal|DBPROP_LITERALIDENTITY|  
|Mantener el estado de cambio|DBPROP_ADC_MAINTAINCHANGESTATUS|  
|Número máximo de filas abierto|DBPROP_MAXOPENROWS|  
|Máximo de filas pendientes|DBPROP_MAXPENDINGROWS|  
|Número máximo de filas|DBPROP_MAXROWS|  
|Utilización de la memoria|DBPROP_MEMORYUSAGE|  
|Granularidad de notificación|DBPROP_NOTIFICATIONGRANULARITY|  
|Fases de notificación|DBPROP_NOTIFICATIONPHASES|  
|Objetos de transacción|DBPROP_TRANSACTEDOBJECT|  
|Cambios visibles de otros usuarios|DBPROP_OTHERUPDATEDELETE|  
|Inserciones visibles de otros usuarios|DBPROP_OTHERINSERT|  
|Propios cambios visibles|DBPROP_OWNUPDATEDELETE|  
|Propias inserciones visibles|DBPROP_OWNINSERT|  
|Conservar al anular|DBPROP_ABORTPRESERVE|  
|Conservar al confirmar|DBPROP_COMMITPRESERVE|  
|Private1||  
|Reinicio rápido|DBPROP_QUICKRESTART|  
|Eventos reentrantes|DBPROP_REENTRANTEVENTS|  
|Quitar filas eliminadas|DBPROP_REMOVEDELETED|  
|Comunicar múltiples cambios|DBPROP_REPORTMULTIPLECHANGES|  
|Cambiar la forma de nombre|DBPROP_ADC_RESHAPENAME|  
|Resincronizar comando|DBPROP_ADC_CUSTOMRESYNCH|  
|Devolver inserciones pendientes|DBPROP_RETURNPENDINGINSERTS|  
|Notificación de eliminación de fila|DBPROP_NOTIFYROWDELETE|  
|Primera notificación de cambio de fila|DBPROP_NOTIFYROWFIRSTCHANGE|  
|Notificación de inserción de fila|DBPROP_NOTIFYROWINSERT|  
|Privilegios de fila|DBPROP_ROWRESTRICT|  
|Notificación de resincronización de fila|DBPROP_NOTIFYROWRESYNCH|  
|Modelo de subprocesos de fila|DBPROP_ROWTHREADMODEL|  
|Notificación de cambio de deshacer de fila|DBPROP_NOTIFYROWUNDOCHANGE|  
|Notificación de eliminación de deshacer de fila|DBPROP_NOTIFYROWUNDODELETE|  
|Notificación de inserción de deshacer de fila|DBPROP_NOTIFYROWUNDOINSERT|  
|Notificación de actualización de fila|DBPROP_NOTIFYROWUPDATE|  
|Notificación de cambio de posición de captura del conjunto de filas|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|  
|Notificación de liberación del conjunto de filas|DBPROP_NOTIFYROWSETRELEASE|  
|Desplazar hacia atrás|DBPROP_CANSCROLLBACKWARDS|  
|Cursor de servidor|DBPROP_SERVERCURSOR|  
|Omitir marcadores eliminados|DBPROP_BOOKMARKSKIPPED|  
|Identidad de fila segura|DBPROP_STRONGIDENTITY|  
|Catálogo único|DBPROP_ADC_UNIQUECATALOG|  
|Filas únicas|DBPROP_UNIQUEROWS|  
|Esquema único|DBPROP_ADC_UNIQUESCHEMA|  
|Tabla única|DBPROP_ADC_UNIQUETABLE|  
|Posibilidad de actualización|DBPROP_UPDATABILITY|  
|Criterios de actualización|DBPROP_ADC_UPDATECRITERIA|  
|Resincronización de la actualización|DBPROP_ADC_UPDATERESYNC|  
|Utilizar marcadores|DBPROP_BOOKMARKS|

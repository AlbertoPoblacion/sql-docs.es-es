---
title: Compatibilidad con transacciones locales | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- SQL Server Native Client OLE DB provider, transactions
- local transactions [OLE DB]
ms.assetid: 78f2e5fc-b6fb-4eda-9f71-991a4d6c4902
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8533747bbe5ccb79a06b10a754c4af45ab241843
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280335"
---
# <a name="supporting-local-transactions"></a>Compatibilidad con transacciones locales
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Una sesión delimita [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] el ámbito de transacción para una transacción local de proveedor OLE DB de Native Client. Cuando, en la dirección de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un consumidor, el proveedor OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de Native Client envía una solicitud [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a una instancia conectada de , la solicitud constituye una unidad de trabajo para el proveedor OLE DB de cliente nativo. Las transacciones locales siempre ajustan una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o varias unidades de trabajo en una única sesión de proveedor OLE DB de Native Client.  
  
 Mediante el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] modo de confirmación automática del proveedor OLE DB de Native Client predeterminado, una sola unidad de trabajo se trata como el ámbito de una transacción local. Solo una unidad participa en la transacción local. Cuando se crea una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sesión, el proveedor OLE DB de Native Client inicia una transacción para la sesión. Cuando se completa correctamente una unidad de trabajo, el trabajo se confirma. En caso de error, cualquier trabajo comenzado se revierte y el error se notifica al consumidor. En cualquier caso, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client comienza una nueva transacción local para la sesión para que todo el trabajo se lleve a cabo dentro de una transacción.  
  
 El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumidor del proveedor OLE DB de Native Client puede dirigir un control más preciso sobre el ámbito de transacción local mediante la interfaz **ITransactionLocal.** Cuando una sesión del consumidor inicia una transacción, todas las unidades de trabajo de la sesión entre el punto de inicio de la transacción y las posibles llamadas a los métodos **Commit** o **Abort** se tratan como una unidad atómica. El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client inicia implícitamente una transacción cuando el consumidor se lo indica. Si el consumidor no solicita la retención, la sesión vuelve al comportamiento de nivel de transacción primaria, la mayoría de las veces en modo de confirmación automática.  
  
 El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client admite **parámetros ITransactionLocal::StartTransaction** como se indica a continuación.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*isoLevel*[in]|Nivel de aislamiento que se va a utilizar con esta transacción. En las transacciones [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locales, el proveedor OLE DB de Native Client admite lo siguiente:<br /><br /> **ISOLATIONLEVEL_UNSPECIFIED**<br /><br /> **ISOLATIONLEVEL_CHAOS**<br /><br /> **ISOLATIONLEVEL_READUNCOMMITTED**<br /><br /> **ISOLATIONLEVEL_READCOMMITTED**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_CURSORSTABILITY**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_SERIALIZABLE**<br /><br /> **ISOLATIONLEVEL_ISOLATED**<br /><br /> **ISOLATIONLEVEL_SNAPSHOT**<br /><br /> <br /><br /> Nota: A partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], ISOLATIONLEVEL_SNAPSHOT es válido para el argumento *isoLevel*, independientemente de que la base de datos tenga habilitado el control de versiones. Sin embargo, se producirá un error si el usuario intenta ejecutar una instrucción y no está habilitado el control de versiones, o si la base de datos no es de solo lectura. Además, si se especifica ISOLATIONLEVEL_SNAPSHOT como el valor de *isoLevel* al conectarse a una versión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anterior a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], se producirá el error XACT_E_ISOLATIONLEVEL.|  
|*isoFlags*[in]|El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client devuelve un error para cualquier valor que no sea cero.|  
|*pOtherOptions*[in]|Si no es [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NULL, el proveedor OLE DB de Native Client solicita el objeto options de la interfaz. El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client devuelve XACT_E_NOTIMEOUT si el miembro *ulTimeout* del objeto options no es cero. El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client omite el valor del miembro *szDescription.*|  
|*pulTransactionLevel*[out]|Si no es [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NULL, el proveedor OLE DB de Native Client devuelve el nivel anidado de la transacción.|  
  
 Para las transacciones [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locales, el proveedor OLE DB de Native Client implementa **parámetros ITransaction::Abort** como se indica a continuación.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*pboidReason*[in]|Se omite si está establecido. Puede ser sin ningún riesgo NULL.|  
|*fRetaining*[in]|Si es TRUE, se inicia una nueva transacción de forma implícita para la sesión. La transacción debe ser confirmada o finalizada por el consumidor. Cuando FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] el proveedor OLE DB de Native Client vuelve al modo de confirmación automática para la sesión.|  
|*fAsync*[in]|El proveedor OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de Native Client no admite la anulación asincrónica. El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client devuelve XACT_E_NOTSUPPORTED si el valor no es FALSE.|  
  
 Para las transacciones [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locales, el proveedor OLE DB de Native Client implementa **parámetros ITransaction::Commit** como se indica a continuación.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*fRetaining*[in]|Si es TRUE, se inicia una nueva transacción de forma implícita para la sesión. La transacción debe ser confirmada o finalizada por el consumidor. Cuando FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] el proveedor OLE DB de Native Client vuelve al modo de confirmación automática para la sesión.|  
|*grfTC*[in]|El proveedor OLE DB de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client no admite las devoluciones asincrónicas y de fase uno. El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client devuelve XACT_E_NOTSUPPORTED para cualquier valor distinto de XACTTC_SYNC.|  
|*grfRM*[in]|Debe ser 0.|  
  
 Los [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conjuntos de filas de proveedor OLE DB de Native Client en la sesión se conservan en una operación de confirmación o anulación local basada en los valores de las propiedades del conjunto de filas DBPROP_ABORTPRESERVE y DBPROP_COMMITPRESERVE. De forma predeterminada, estas propiedades [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] son VARIANT_FALSE y todos los conjuntos de filas de proveedor OLE DB de Native Client en la sesión se pierden después de una operación de anulación o confirmación.  
  
 El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client no implementa la interfaz **ITransactionObject.** Si el consumidor intenta recuperar una referencia en la interfaz, obtiene E_NOINTERFACE.  
  
 En este ejemplo, se usa **ITransactionLocal**.  
  
```  
// Interfaces used in the example.  
IDBCreateSession*   pIDBCreateSession   = NULL;  
ITransaction*       pITransaction       = NULL;  
IDBCreateCommand*   pIDBCreateCommand   = NULL;  
IRowset*            pIRowset            = NULL;  
  
HRESULT             hr;  
  
// Get the command creation and local transaction interfaces for the  
// session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
if (FAILED(hr = pIDBCreateCommand->QueryInterface(IID_ITransactionLocal,  
    (void**) &pITransaction)))  
    {  
    // Process error. Release any references and return.  
    }  
  
// Start the local transaction.  
if (FAILED(hr = ((ITransactionLocal*) pITransaction)->StartTransaction(  
    ISOLATIONLEVEL_REPEATABLEREAD, 0, NULL, NULL)))  
    {  
    // Process error from StartTransaction. Release any references and  
    // return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then terminate.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, XACTTC_SYNC, 0)))  
        {  
        // Get error from failed commit.  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>Consulte también  
 [Transacciones](../../relational-databases/native-client-ole-db-transactions/transactions.md)   
 [Trabajar con aislamiento de instantánea](../../relational-databases/native-client/features/working-with-snapshot-isolation.md)  
  
  

---
title: IBCPSession::BCPColumns (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- IBCPSession::BCPColumns (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPColumns method
ms.assetid: c338abe8-9e30-4853-a7c6-b1a6c00095e1
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1b5385d32ef349284f261a457391581b6e28da03
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "73789704"
---
# <a name="ibcpsessionbcpcolumns-ole-db"></a>IBCPSession::BCPColumns (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Establece el número de campos que van a enlazarse a las columnas en una tabla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
HRESULT BCPColumns(   
      DBCOUNTITEM nColumns);  
```  
  
## <a name="remarks"></a>Remarks  
 Llama a [a IBCPSession::BCPColFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) internamente para establecer los valores predeterminados para los datos de campo. Estos valores predeterminados se obtienen de la información de columna de SQL Server que el proveedor recupera internamente cuando el nombre de tabla se especifica a través de [IBCPSession::BCPInit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md).  
  
> [!NOTE]  
>  Se puede llamar a este método solamente después de que se haya llamado a **a BCPInit** con un nombre de archivo válido.  
  
 Solo debe llamar a este método si piensa utilizar un formato de archivo de usuario que difiere del valor predeterminado. Para obtener más información sobre una descripción del formato predeterminado del archivo de usuario, vea el método **BCPInit** .  
  
 Después de llamar al método **BCPColumns** , debe llamar al método **BCPColFmt** para cada columna en el archivo de usuario para definir completamente un formato de archivo personalizado.  
  
## <a name="arguments"></a>Argumentos  
 *nColumns*[in]  
 El número total de campos en el archivo de usuario. Aun cuando está preparando para realizar copias masiva de datos del archivo de usuario a una tabla SQL Server y no piensa copiar todos los campos en el archivo de usuario, todavía debe establecer el argumento *nColumns* en el número total de campos de archivo de usuario. Los campos omitidos se pueden especificar a continuación a través de **BCPColFmt**.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 S_OK  
 El método se ha llevado a cabo de forma correcta.  
  
 E_FAIL  
 Se produjo un error específico del proveedor; para obtener información detallada, use la interfaz [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) .  
  
 E_UNEXPECTED  
 No se esperaba la llamada al método. Por ejemplo, no se llamó al método **BCPInit** antes de llamar a este método. También se produce cuando se llama a este método más de una vez para una operación de copia masiva.  
  
 E_OUTOFMEMORY  
 Error de memoria insuficiente.  
  
## <a name="see-also"></a>Vea también  
 [ &#40;OLE DB&#41; IBCPSession](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Realizar operaciones de copia masiva](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  

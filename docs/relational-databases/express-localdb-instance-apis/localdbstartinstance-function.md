---
description: Función LocalDBStartInstance
title: Función LocalDBStartInstance | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- LocalDBStartInstance
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: cb325f5d-10ee-4a56-ba28-db0074ab3926
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cf46ccf1e972dc34b4f0500fdf654a76aa32f086
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494231"
---
# <a name="localdbstartinstance-function"></a>Función LocalDBStartInstance
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Inicia la instancia de SQL Server Express LocalDB especificada.  
  
 **Archivo de encabezado:** sqlncli.h  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT LocalDBStartInstance(  
           PCWSTR pInstanceName,  
           DWORD dwFlags,   
           LPWSTR wszSqlConnection,   
           LPDWORD lpcchSqlConnection   
);  
```  
  
## <a name="parameters"></a>Parámetros  
 *pInstanceName*  
 [Input] Nombre de la instancia de LocalDB que se va a iniciar.  
  
 *dwFlags*  
 [Entrada] Reservado para uso futuro. En estos momentos, se debe establecer en 0.  
  
 *wszSqlConnection*  
 [Salida] Búfer donde se almacena la cadena de conexión para la instancia de LocalDB.  
  
 *lpcchSqlConnection*  
 [Entrada/Salida] En la entrada contiene el tamaño de búfer de *wszSqlConnection* en caracteres, incluidos los valores NULL finales. En la salida, si el tamaño de búfer proporcionado es demasiado pequeño, contiene el tamaño de búfer necesario en caracteres, lo cual incluye los valores NULL finales.  
  
## <a name="returns"></a>Devoluciones  
 S_OK  
 La función se ha realizado correctamente.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../../relational-databases/express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB no está instalado en el equipo.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Uno o más parámetros de entrada especificados no son válidos.  
  
 [LOCALDB_ERROR_INVALID_INSTANCE_NAME](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 El nombre de instancia de especificado no es válido.  
  
 [LOCALDB_ERROR_UNKNOWN_INSTANCE](../../relational-databases/express-localdb-error-messages/localdb-error-unknown-instance.md)  
 La instancia no existe.  
  
 [LOCALDB_ERROR_INSUFFICIENT_BUFFER](../../relational-databases/express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 El búfer *wszSqlConnection* especificado es demasiado pequeño.  
  
 [LOCALDB_ERROR_WAIT_TIMEOUT](../../relational-databases/express-localdb-error-messages/localdb-error-wait-timeout.md)  
 Se ha agotado el tiempo de espera mientras se intentaba adquirir bloqueos de sincronización.  
  
 [LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG](../../relational-databases/express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 La ruta de acceso donde la instancia debe almacenarse es mayor que MAX_PATH.  
  
 [LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 No se puede recuperar una carpeta de perfil de usuario.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 No se puede tener acceso a una carpeta de la instancia.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 No se puede tener acceso a un registro de la instancia.  
  
 [LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-modify-instance-registry.md)  
 No se puede modificar un registro de la instancia.  
  
 [LOCALDB_ERROR_CANNOT_CREATE_SQL_PROCESS](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-create-sql-process.md)  
 No se puede crear un proceso para SQL Server.  
  
 [LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED](../../relational-databases/express-localdb-error-messages/localdb-error-sql-server-startup-failed.md)  
 Se ha iniciado un proceso de SQL Server, pero se ha producido un error al iniciar SQL Server.  
  
 [LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT](../../relational-databases/express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 Una configuración de instancia estaba dañada.  
  
 [LOCALDB_ERROR_AUTO_INSTANCE_CREATE_FAILED](../../relational-databases/express-localdb-error-messages/localdb-error-auto-instance-create-failed.md)  
 No se puede crear una instancia automática. Vea el registro de eventos de aplicación de Windows para obtener los detalles del error.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 Se ha producido un error inesperado. Vea el registro de eventos para obtener detalles.  
  
## <a name="details"></a>Detalles  
 Ell argumento del búfer de conexión (*wszSqlConnection*) y el argumento del tamaño de búfer de conexión (*lpcchSqlConnection*) son opcionales. La tabla siguiente muestra las opciones de uso de estos argumentos y sus resultados.  
  
|Buffer|Tamaño de búfer|Análisis razonado|Acción|  
|------------|-----------------|---------------|------------|  
|NULL|NULL|El usuario desea iniciar la instancia y no necesita un nombre de canalización.|Inicia una instancia (sin devolución de canalización y no se requiere la devolución de tamaño de búfer).|  
|NULL|Presente|El usuario solicita el tamaño de búfer de salida. (En la llamada siguiente el usuario probablemente solicitará un inicio real).|Devuelve el tamaño de búfer necesario (sin inicio y sin devolución de canalización). El resultado es S_OK.|  
|Presente|NULL|No está permitido; entrada no correcta.|El resultado devuelto es LOCALDB_ERROR_INVALID_PARAMETER.|  
|Presente|Presente|El usuario desea iniciar la instancia y necesita el nombre de la canalización para conectarse una vez se haya iniciado.|Comprueba el tamaño de búfer, inicia la instancia y devuelve el nombre de la canalización en el búfer. <br />El argumento de tamaño de búfer devuelve la longitud de la cadena "Server =", sin incluir los valores NULL de terminación.|  
  
 Para obtener un ejemplo de código que utilice LocalDB API, vea [SQL Server Express LocalDB Reference](../../relational-databases/sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Consulte también  
 [Información de encabezado y versión de SQL Server Express LocalDB](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  

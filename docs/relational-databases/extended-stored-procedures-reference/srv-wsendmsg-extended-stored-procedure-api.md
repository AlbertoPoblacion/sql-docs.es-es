---
title: srv_wsendmsg (API de procedimiento almacenado extendido) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_wsendmsg
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_wsendmsg
ms.assetid: f2153076-32c9-4a52-8e1b-fc9618153543
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c49d9e3ac3ba60ded98c7bdba55465b914bf1b28
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62704482"
---
# <a name="srvwsendmsg-extended-stored-procedure-api"></a>srv_wsendmsg (API de procedimiento almacenado extendido)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Use la integración con CLR en su lugar.  
  
 Envía un mensaje Unicode al cliente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
int srv_wsendmsg(SRV_PROC *   
srvproc  
, int   
msgnum  
, int   
severity  
, WCHAR *   
message  
, int   
msglen  
);  
```  
  
## <a name="arguments"></a>Argumentos  
 *srvproc*  
 Es un puntero a la estructura SRV_PROC que es el identificador de una conexión cliente determinada. La estructura contiene información que la biblioteca de API de procedimiento almacenado extendido usa para administrar la comunicación y los datos entre la aplicación y el cliente.  
  
 *Msgnum*  
 Es un número de mensaje de 4 bytes.  
  
 *Severity*  
 Especifica la gravedad del error. Una gravedad menor o igual que 10 se considera un mensaje informativo; de lo contrario, se considera un error.  
  
 *message*  
 Es un puntero a una cadena Unicode que se va a enviar al cliente.  
  
 *msglen*  
 Especifica la longitud en caracteres de *message*.  
  
## <a name="returns"></a>Devuelve  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Notas  
 Utilice esta función para enviar mensajes en Unicode. Es similar a **srv_sendmsg**, pero el mensaje que envía es una cadena WCHAR en lugar de una cadena de tipo DBCHAR. Tenga en cuenta que la longitud del mensaje se indica en caracteres en lugar de en bytes y que *msglen* nunca será igual a SRV_NULLTERM.  
  
 La función devuelve FAIL cuando  
  
-   El argumento *msglen* proporcionado no está comprendido en el intervalo de 0 a 32242.  
  
-   El argumento *msglen* proporcionado es 0 pero el puntero del mensaje es NULL.  
  
-   Se produce un error al enviar el mensaje de error a través de la red.  
  
> [!IMPORTANT]  
>  Debe revisar minuciosamente el código fuente de los procedimientos almacenados extendidos y debe probar las DLL compiladas antes de instalarlas en el servidor de producción. Para obtener información acerca de la revisión y pruebas de seguridad, vea este [sitio web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409 https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Consulte también  
 [srv_sendmsg &#40;API de procedimiento almacenado extendido&#41;](../../relational-databases/extended-stored-procedures-reference/srv-sendmsg-extended-stored-procedure-api.md)  
  
  

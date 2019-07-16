---
title: Modelo de programación de RDS básica | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS programming model [ADO]
ms.assetid: 0bdd236b-edff-4aac-94c3-93e1465ca6c5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 84b90e2c1338c38538d0c33779fb8e3f5cf2af79
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67922953"
---
# <a name="basic-rds-programming-model"></a>Modelo básico de programación de RDS
> [!IMPORTANT]
>  A partir de Windows 8 y Windows Server 2012, componentes de servidor RDS ya no están incluidos en el sistema operativo de Windows (consulte Windows 8 y [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) para obtener más detalles). Componentes de cliente RDS se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan. Deben migrar las aplicaciones que usan RDS a [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 RDS orienta a las aplicaciones que existen en el siguiente entorno: Una aplicación cliente especifica un programa que se ejecutará en un servidor y los parámetros necesarios para devolver la información deseada. El programa invocado en el servidor obtiene acceso al origen de datos especificada, recupera la información, opcionalmente procesa los datos y, a continuación, devuelve la información resultante a la aplicación cliente en un formulario que puede utilizar fácilmente. RDS proporciona los medios para realizar la siguiente secuencia de acciones:  
  
-   Especifique el programa que se invocará en el servidor y obtenga un medio para hacer referencia a él desde el cliente. (Esta referencia se denomina a veces un *proxy*. Representa el programa de servidor remoto. La aplicación cliente "llamará" el servidor proxy como si fuese un sistema local, pero invoca realmente el programa de servidor remoto.)  
  
-   Invocar el programa de servidor. Pasar parámetros al programa de servidor que identifican el origen de datos y el comando para emitir. (El programa de servidor realmente utiliza ADO para tener acceso al origen de datos. ADO realiza una conexión con uno de los parámetros especificados y, a continuación, emite el comando especificado en el otro parámetro).  
  
-   El programa de servidor obtiene una [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objeto desde el origen de datos. Opcionalmente, el **Recordset** se procesa el objeto en el servidor.  
  
-   El programa de servidor devuelve el estado final **Recordset** objeto a la aplicación cliente.  
  
-   En el cliente, el **Recordset** objeto se coloca en un formulario que se puede usar fácilmente los controles visuales.  
  
-   Las modificaciones en el **Recordset** objeto se envían al programa de servidor, que se utiliza para actualizar el origen de datos.  
  
 Este modelo de programación contiene algunas características prácticas. Si no es necesario un programa de servidor complejo para acceder al origen de datos y proporcionar los parámetros de comando y conexión necesaria, RDS automáticamente recuperar los datos especificados con un simple, programa de servidor predeterminado.  
  
 Si necesita un procesamiento más complejo, puede especificar su propio programa de servidor personalizado. Por ejemplo, dado que un programa de servidor personalizado tiene toda la funcionalidad de ADO a su disposición, podría conectarse a varios orígenes de datos, combinar sus datos de alguna manera compleja y, a continuación, devolver un resultado simple, que se procesa a la aplicación cliente.  
  
 Por último, si sus necesidades son intermedias, ADO ahora permite personalizar el comportamiento del programa de servidor predeterminado.  
  
## <a name="see-also"></a>Vea también  
 [Modelo de programación de RDS en detalle](../../../ado/guide/remote-data-service/rds-programming-model-in-detail.md)   
 [Escenario RDS](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [Tutorial de RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Objeto de conjunto de registros (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Seguridad y uso de RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)



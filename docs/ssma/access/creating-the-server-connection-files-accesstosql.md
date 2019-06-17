---
title: Creación de los archivos de conexión de servidor (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 08/17/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 829153be-aa8e-4162-87e8-69882feecf19
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: fabc454fe6adc77ec3e9789925e099fb6b0de6b1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63138847"
---
# <a name="creating-the-server-connection-files-accesstosql"></a>Crear el servidor de archivos de conexión (AccessToSQL)
Información del servidor se puede especificar en la sección de servidores del archivo de script. También se puede especificar la información del servidor en un archivo de conexión de servidor independiente. El parámetro de línea de comandos para el archivo de conexión de servidor es `-c <serverconnectionfile>`. Si el mismo identificador de servidor está presente en el script y el servidor de archivos de conexión, se considera la definición del servidor en el archivo de script.  
  
```xml  
<!--Sample of server connection file commands -->  
<!--Connection to SQL Server-->  
  
<sql-server name="target_3">  
  
  <sql-server-authentication>  
  
    <server value="$TargetServerName$"/>  
  
    <database value="$TargetDB$"/>  
  
    <user-id value="$TargetUserName$"/>  
  
    <password value="$TargetPassword$"/>  
  
    <encrypt value="true"/>  
  
    <trust-server-certificate value="true"/>  
  
  </sql-server-authentication>  
  
</sql-server>  
```  
  
```xml  
<!--Connection to SQL Azure-->  
  
<sql-azure name="target_azure">  
  
  <server value="$TargetAzureServerName$"/>  
  
  <database value="$TargetAzureDB$"/>  
  
  <user-id value="$TargetAzureUserName$"/>  
  
  <password value="$TargetAzurePassword$"/>  
  
</sql-azure>  
```  
  
## <a name="server-connection-file-validation"></a>Validación del archivo de conexión de servidor  
El usuario puede validar fácilmente su archivo de conexión de servidor con el archivo de definición de esquema **'A2SSConsoleScriptServersSchema.xsd'** disponible en la carpeta "Esquemas".  
  
## <a name="next-step"></a>Paso siguiente  
El siguiente paso en el funcionamiento de la consola es [ejecutando la consola de SSMA &#40;AccessToSQL&#41;](../../ssma/access/executing-the-ssma-console-accesstosql.md)  
  
## <a name="see-also"></a>Vea también  
[Ejecución de la consola SSMA (acceso)](https://msdn.microsoft.com/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  

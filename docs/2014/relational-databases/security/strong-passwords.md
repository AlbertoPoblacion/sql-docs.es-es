---
title: Contraseñas seguras | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], passwords
- passwords [SQL Server], strong
- symbols [SQL Server]
- security [SQL Server], passwords
- passwords [SQL Server], symbols
- characters [SQL Server], password policies
- strong passwords [SQL Server]
ms.assetid: 338548f4-c4d8-47ca-b597-5c9c0f2fa205
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 97b13e8ccf7ef331320d15254dde3480331c4bb0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2020
ms.locfileid: "62470362"
---
# <a name="strong-passwords"></a>Contraseñas seguras
  Las contraseñas pueden constituir el vínculo más débil de una implementación de seguridad de servidor. Debe tener siempre mucho cuidado a la hora de elegir una contraseña. Una contraseña segura presenta las siguientes características:  
  
-   Tiene una longitud de 8 caracteres como mínimo.  
  
-   Contiene una combinación de letras, números y símbolos.  
  
-   No es una palabra que pueda encontrarse en el diccionario.  
  
-   No es el nombre de un comando.  
  
-   No es el nombre de una persona.  
  
-   No es el nombre de un usuario.  
  
-   No es el nombre de un equipo.  
  
-   Se cambia con frecuencia.  
  
-   Presenta diferencias notables con respecto a contraseñas anteriores.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pueden contener hasta 128 caracteres, entre los que se pueden incluir letras, símbolos y dígitos. Dado que los inicios de sesión, nombres de usuario, roles y contraseñas se utilizan con frecuencia en instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] , determinados símbolos deberán estar incluidos entre comillas dobles (") o corchetes ([ ]). Utilice estos delimitadores en las instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] cuando el inicio de sesión, usuario, rol o contraseña de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] presente las siguientes características:  
  
-   Contiene o comienza por un carácter de espacio.  
  
-   Comienza por el carácter $ o \@.  
  
 Si se usa en una cadena de conexión de OLE DB u ODBC, el inicio de sesión o la contraseña no deben contener ninguno de estos caracteres: [] {}() , ; ? * ! \@. Estos caracteres se usan para inicializar una conexión o para separar valores de conexión.  
  
## <a name="related-content"></a>Contenido relacionado  
 [Directiva de contraseñas](password-policy.md)  
  
  

---
title: Protección de cadenas de conexión | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 69ce8557-5260-4ea4-81b8-d0c5481f0868
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8f783db5fef7c0da10fb0ec856f3766388be49f5
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928429"
---
# <a name="securing-connection-strings"></a>Protección de cadenas de conexión

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

La protección del acceso al origen de datos es uno de los objetivos más importantes a la hora de proteger una aplicación. Para limitar el acceso al origen de datos, debe tomar precauciones y proteger la información de conexión como el Id. de usuario, la contraseña y el nombre del origen de datos. El almacenamiento del Id. de usuario en texto sin formato, como en el código fuente, supone un problema de seguridad grave. Incluso si proporciona una versión compilada del código que contiene la información de Id. de usuario y contraseña en una fuente externa, el código compilado se puede desensamblar y el Id. de usuario y la contraseña pueden quedar expuestos. Por consiguiente, es fundamental no incluir información clave como el Id. de usuario y la contraseña en el código.

Se recomienda no almacenar la contraseña junto con la URL de conexión en el código fuente de la aplicación. En su lugar, puede almacenar la contraseña en un archivo independiente con acceso restringido. Se puede conceder acceso a este archivo en el contexto en que se ejecuta la aplicación.

Otro enfoque consiste en almacenar la contraseña cifrada en un archivo. Asegúrese de usar una API de cifrado que no requiera el almacenamiento de la clave en cualquier parte y no se derive de la contraseña del usuario. Por ejemplo, puede usar pares de claves públicas o privada basadas en certificados o usar un método en que dos partes usen un protocolo de intercambio de claves (algoritmo Diffie-Hellman) para generar claves secretas idénticas para el cifrado sin tener que transmitir la clave secreta.

Si obtiene la información de cadena de conexión de una fuente externa (por ejemplo, si un usuario proporciona un Id. de usuario y una contraseña), debe validar las entradas desde el origen para asegurarse de que presentan el formato correcto y no contienen parámetros adicionales que afecten a la conexión.

## <a name="see-also"></a>Consulte también

[Protección de las aplicaciones del controlador JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)

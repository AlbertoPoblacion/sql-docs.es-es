---
title: Usar el cifrado SSL | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8e566243-2f93-4b21-8065-3c8336649309
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 34a486a2bcde43ccccc053aed9ebd9392ce34e8c
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2019
ms.locfileid: "69026033"
---
# <a name="using-ssl-encryption"></a>Empleo del cifrado SSL

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

El cifrado de capa de sockets seguros (SSL) habilita la transmisión de datos cifrados a través de la red entre una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y una aplicación cliente.  
  
Capa de sockets seguros (SSL) es un protocolo para establecer un canal de comunicaciones seguro para evitar la interceptación de información esencial o confidencial por la red y otras comunicaciones de Internet. SSL permite al cliente y al servidor autenticar la identidad de cada uno. Después de autenticar a los participantes, SSL proporciona conexiones cifradas entre ellos para proteger la transmisión de los mensajes.  
  
El [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] proporciona una infraestructura para habilitar y deshabilitar el cifrado en una conexión determinada según las propiedades de conexión especificadas por el usuario y la configuración del cliente y el servidor. El usuario puede especificar la ubicación del almacén de certificados y la contraseña, un nombre de host que se va a utilizar para validar el certificado y cuándo cifrar el canal de comunicaciones.  
  
Al habilitar el cifrado SSL se aumenta la seguridad de los datos que se transmiten a través de redes entre instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y las aplicaciones. No obstante, también reduce el rendimiento.  
  
En los temas de esta sección se describe cómo la versión del [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] admite el cifrado SSL, incluidas las nuevas propiedades de conexión, y cómo se puede configurar el almacén de confianza en el lado cliente.  
  
> [!NOTE]  
> Se recomienda la propiedad de conexión **hostNameInCertificate** para validar un certificado SSL.  

## <a name="in-this-section"></a>En esta sección  

| Tema                                                                                                        | Descripción                                                                                                                                           |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Descripción de la compatibilidad con SSL](../../connect/jdbc/understanding-ssl-support.md)                                 | Describe cómo el [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] admite el cifrado SSL.                                              |
| [Conexión con cifrado SSL](../../connect/jdbc/connecting-with-ssl-encryption.md)                       | Describe cómo conectarse a una base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con las nuevas propiedades de conexión específicas de SSL. |
| [Configuración del cliente para el cifrado SSL](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md) | Describe cómo configurar el almacén de confianza predeterminado del lado cliente y cómo importar un certificado privado al almacén de confianza del equipo cliente.   |
  
## <a name="see-also"></a>Vea también

[Protección de las aplicaciones del controlador JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  

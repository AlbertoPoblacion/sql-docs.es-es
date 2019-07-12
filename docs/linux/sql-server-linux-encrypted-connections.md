---
title: Cifrar conexiones a SQL Server en Linux
description: Este artículo describe cifrar conexiones a SQL Server en Linux.
ms.date: 01/30/2018
author: vin-yu
ms.author: vinsonyu
ms.reviewer: vanto
manager: jroth
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
helpviewer_keywords:
- Linux, encrypted connections
ms.openlocfilehash: 9ca1a6b7a3530041def66ec74be9de547c6d98ea
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67833769"
---
# <a name="encrypting-connections-to-sql-server-on-linux"></a>Cifrar conexiones a SQL Server en Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en Linux puede usar capa de transporte (TLS) para cifrar los datos transmitidos a través de una red entre una aplicación cliente y una instancia de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] admite los mismos protocolos TLS en Windows y Linux: TLS 1.0, 1.1 y 1.2. Sin embargo, son específicos del sistema operativo en el que los pasos para configurar TLS [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] se está ejecutando.  

## <a name="requirements-for-certificates"></a>Requisitos de certificados 
Antes de comenzar, deberá asegurarse de que los certificados cumplen estos requisitos:
- La hora actual del sistema debe ser posterior válido de propiedad del certificado y antes de la fecha válido para la propiedad del certificado.
- El certificado debe estar destinado a la autenticación del servidor. Esto requiere que la propiedad de uso mejorado de clave del certificado para especificar la autenticación de servidor (1.3.6.1.5.5.7.3.1).
- El certificado debe crearse con la opción KeySpec de AT_KEYEXCHANGE. Normalmente, la propiedad de uso de la clave del certificado (KEY_USAGE) también incluye cifrado de clave (CERT_KEY_ENCIPHERMENT_KEY_USAGE).
- La propiedad de asunto del certificado debe indicar que el nombre común (CN) es el mismo como el nombre de host o nombre de dominio completo (FQDN) del equipo del servidor. Nota: Se admiten certificados comodín.

## <a name="configuring-the-openssl-libraries-for-use-optional"></a>Configuración de las bibliotecas OpenSSL para su uso (opcional)
Puede crear vínculos simbólicos en el `/opt/mssql/lib/` directorio que hacen referencia a que `libcrypto.so` y `libssl.so` bibliotecas que se deben usar para el cifrado. Esto es útil si desea obligar a SQL Server para usar una versión específica de OpenSSL que no sea el valor predeterminado proporcionado por el sistema. Si no existen estos vínculos simbólicos, SQL Server se cargará las bibliotecas OpenSSL predeterminado configurado en el sistema.

Estos vínculos simbólicos deben denominarse `libcrypto.so` y `libssl.so` y se coloca en el `/opt/mssql/lib/` directory.

## <a name="overview"></a>Información general
TLS se utiliza para cifrar las conexiones desde una aplicación cliente [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Cuando se configura correctamente, TLS proporciona privacidad y la integridad de los datos para las comunicaciones entre el cliente y el servidor.  Las conexiones TLS pueden ser iniciado por el cliente o servidor iniciada. 

## <a name="client-initiated-encryption"></a>Cifrado por el cliente 
- **Generar certificado** (/ CN debe coincidir con el nombre de dominio completo del host de SQL Server)

> [!NOTE]
> En este ejemplo se usa un certificado autofirmado, esto no debe utilizarse para escenarios de producción. Debe usar certificados de CA. 

        openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql.contoso.com' -keyout mssql.key -out mssql.pem -days 365 
        sudo chown mssql:mssql mssql.pem mssql.key 
        sudo chmod 600 mssql.pem mssql.key   
        sudo mv mssql.pem /etc/ssl/certs/ 
        sudo mv mssql.key /etc/ssl/private/ 

- **Configurar SQL Server**

        systemctl stop mssql-server 
        cat /var/opt/mssql/mssql.conf 
        sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssql.pem 
        sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssql.key 
        sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2 
        sudo /opt/mssql/bin/mssql-conf set network.forceencryption 0 

- **Registrar el certificado en el equipo cliente (Windows, Linux o macOS)**

    -   Si utiliza un certificado firmado de CA, deberá copiar el certificado de entidad de certificación (CA) en lugar del certificado de usuario en el equipo cliente. 
    -   Si usas el certificado autofirmado, copie el archivo .pem a las carpetas siguientes correspondientes a la distribución y ejecutar los comandos para habilitarlas 
        - **Ubuntu**: Certificado de copia para ```/usr/share/ca-certificates/``` rename extensión .crt use certificados de ca de dpkg reconfigure para habilitarlo como certificado de entidad del sistema. 
        - **RHEL**: Certificado de copia para ```/etc/pki/ca-trust/source/anchors/``` usar ```update-ca-trust``` para habilitarlo como certificado de entidad del sistema.
        - **SUSE**: Certificado de copia para ```/usr/share/pki/trust/anchors/``` usar ```update-ca-certificates``` para habilitarlo como certificado de entidad del sistema.
        - **Windows**:  Importar el archivo .pem como un certificado en el usuario actual -> entidades de certificación raíz -> certificados de confianza
        - **macOS**: 
           - Copie el certificado para ```/usr/local/etc/openssl/certs```
           - Ejecute el siguiente comando para obtener el valor de hash: ```/usr/local/Cellar/openssql/1.0.2l/openssql x509 -hash -in mssql.pem -noout```
           - Cambie el nombre del certificado al valor. Por ejemplo: ```mv mssql.pem dc2dd900.0```. Asegúrese de que está dc2dd900.0 en ```/usr/local/etc/openssl/certs```
    
-   **Ejemplos de cadena de conexión** 

    - **[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)]**   
  ![Cuadro de diálogo de conexión de SSMS](media/sql-server-linux-encrypted-connections/ssms-encrypt-connection.png "cuadro de diálogo de conexión de SSMS")  
  
    - **SQLCMD** 

            sqlcmd  -S <sqlhostname> -N -U sa -P '<YourPassword>' 
    - **ADO.NET** 

            "Encrypt=True; TrustServerCertificate=False;" 
    - **ODBC** 

            "Encrypt=Yes; TrustServerCertificate=no;" 
    - **JDBC** 
    
            "encrypt=true; trustServerCertificate=false;" 

## <a name="server-initiated-encryption"></a>Cifrado iniciado por el servidor 

- **Generar certificado** (/ CN debe coincidir con el nombre de dominio completo del host de SQL Server)
        
        openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql.contoso.com' -keyout mssql.key -out mssql.pem -days 365 
        sudo chown mssql:mssql mssql.pem mssql.key 
        sudo chmod 600 mssql.pem mssql.key   
        sudo mv mssql.pem /etc/ssl/certs/ 
        sudo mv mssql.key /etc/ssl/private/ 

- **Configurar SQL Server**

        systemctl stop mssql-server 
        cat /var/opt/mssql/mssql.conf 
        sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssql.pem 
        sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssql.key 
        sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2 
        sudo /opt/mssql/bin/mssql-conf set network.forceencryption 1 
        
-   **Ejemplos de cadena de conexión** 

    - **SQLCMD**

            sqlcmd  -S <sqlhostname> -U sa -P '<YourPassword>' 
    - **ADO.NET** 

            "Encrypt=False; TrustServerCertificate=False;" 
    - **ODBC** 

            "Encrypt=no; TrustServerCertificate=no;"  
    - **JDBC** 
    
            "encrypt=false; trustServerCertificate=false;" 
            
> [!NOTE]
> Establecer **TrustServerCertificate** en True si el cliente no puede conectarse a la entidad emisora de certificados para validar la autenticidad del certificado

## <a name="common-connection-errors"></a>Errores de conexión comunes  

|Mensaje de error |Fix |
|--- |--- |
|La cadena de certificado fue emitida por una entidad que no sea de confianza.  |Este error se produce cuando los clientes no pueden comprobar la firma en el certificado presentado por SQL Server durante el protocolo de enlace TLS. Asegúrese de que el cliente confía ya sea el [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] directamente el certificado o la entidad de certificación que firmó el certificado de SQL Server. |
|El nombre principal de destino es incorrecto.  |Asegúrese de que el campo de nombre común en el certificado del servidor SQL coincide con el nombre del servidor especificado en la cadena de conexión del cliente. |  
|El host remoto cerró a la fuerza una conexión ya existente. |Este error puede producirse cuando el cliente no es compatible con la versión del protocolo TLS requerida SQL Server. Por ejemplo, si [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] está configurado para requerir TLS 1.2, asegúrese de que los clientes también admiten el protocolo TLS 1.2. |
| | |   

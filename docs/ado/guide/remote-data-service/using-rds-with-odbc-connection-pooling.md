---
title: Uso de RDS con conexión ODBC agrupación | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connection pooling in RDS [ADO]
ms.assetid: e8b912c1-da5b-4e85-a000-1e6648a94237
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a2ffcc64cb9d0e45d371e927cd1c15be51cd917c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67921936"
---
# <a name="using-rds-with-odbc-connection-pooling"></a>Uso de RDS con la agrupación de conexiones de ODBC
Si usa un origen de datos ODBC, puede usar la opción en Internet Information Services (IIS) de agrupación de conexiones para conseguir un procesamiento de alto rendimiento de carga del cliente. Agrupación de conexiones es un administrador de recursos para las conexiones, mantiene el estado abierto en conexiones que se utilizan con frecuencia.  
  
> [!IMPORTANT]
>  A partir de Windows 8 y Windows Server 2012, componentes de servidor RDS ya no están incluidos en el sistema operativo de Windows (consulte Windows 8 y [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) para obtener más detalles). Componentes de cliente RDS se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan. Deben migrar las aplicaciones que usan RDS a [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Para habilitar la agrupación de conexiones, consulte la documentación de Internet Information Services.  
  
 Tenga en cuenta que habilitar la agrupación de conexiones puede someter al servidor Web a otras restricciones, como se indica en la documentación de Microsoft Internet Information Services.  
  
 Para asegurarse de que la agrupación de conexiones es estable y proporciona mejoras de rendimiento adicionales, debe configurar Microsoft SQL Server para usar la biblioteca de red de Socket TCP/IP.  
  
 Para ello, deberá:  
  
-   Configure el equipo de SQL Server para utilizar Sockets TCP/IP.  
  
-   Configurar el servidor Web para utilizar Sockets TCP/IP.  
  
## <a name="configuring-the-sql-server-computer-to-use-tcpip-sockets"></a>Configurar el equipo con SQL Server para utilizar Sockets TCP/IP  
 En el equipo de SQL Server, ejecute el programa de instalación de SQL Server para que las interacciones con el origen de datos utilizan la biblioteca de red de Socket TCP/IP.  
  
### <a name="to-specify-the-tcpip-socket-network-library-on-the-sql-server-computer"></a>Para especificar la biblioteca de red de Socket TCP/IP en el equipo de SQL Server  
  
### <a name="in-microsoft-sql-server-65"></a>En Microsoft SQL Server 6.5:  
  
1.  En el menú Inicio, elija programas, elija Microsoft SQL Server 6.5 y, a continuación, haga clic en el programa de instalación de SQL.  
  
2.  Haga doble clic en continuar.  
  
3.  En Microsoft SQL Server-cuadro de diálogo Opciones, seleccione Cambiar soporte de red y, a continuación, haga clic en continuar.  
  
4.  Asegúrese de que la casilla de verificación Sockets TCP/IP está activada y haga clic en Aceptar.  
  
5.  Haga clic en Continuar para finalizar y salir de la instalación.  
  
### <a name="in-microsoft-sql-server-70"></a>En Microsoft SQL Server 7.0:  
  
1.  En el menú Inicio, elija programas, elija Microsoft SQL Server 7.0 y, a continuación, haga clic en herramienta de red de servidor.  
  
2.  En la ficha General del cuadro de diálogo, haga clic en Agregar.  
  
3.  En el cuadro de diálogo Agregar configuración de biblioteca de red, haga clic en TCP/IP.  
  
4.  En los cuadros de dirección de Proxy y número de puerto, escriba la dirección de proxy y el número de puerto proporcionada por el Administrador de red.  
  
5.  Haga clic en Aceptar para finalizar y salir de la instalación.  
  
## <a name="configuring-the-web-server-to-use-tcpip-sockets"></a>Configuración del servidor Web para utilizar Sockets TCP/IP  
 Hay dos opciones para configurar el servidor Web para utilizar Sockets TCP/IP. ¿Qué depende de si se tiene acceso a todos los servidores de SQL Server desde el servidor Web, o solo un servidor SQL específico se obtiene acceso desde el servidor Web.  
  
 Si se tiene acceso a todos los servidores de SQL Server desde el servidor Web, deberá ejecutar la herramienta de configuración de cliente de SQL Server en el equipo servidor Web. Los siguientes pasos cambian la biblioteca de red predeterminada para todas las conexiones de SQL Server que se realiza desde este servidor Web de IIS para usar la biblioteca de red Sockets TCP/IP.  
  
### <a name="to-configure-the-web-server-all-sql-servers"></a>Para configurar el servidor Web (todos los servidores de SQL)  
  
### <a name="for-microsoft-sql-server-65"></a>Para Microsoft SQL Server 6.5:  
  
1.  En el menú Inicio, elija programas, elija Microsoft SQL Server 6.5 y, a continuación, haga clic en utilidad de configuración de cliente de SQL.  
  
2.  Haga clic en la ficha Biblioteca de red.  
  
3.  En el cuadro de la red predeterminada, seleccione Sockets TCP/IP.  
  
4.  Haga clic en listo para guardar los cambios y salir de la utilidad.  
  
### <a name="for-microsoft-sql-server-70"></a>Para Microsoft SQL Server 7.0:  
  
1.  En el menú Inicio, elija programas, elija Microsoft SQL Server 7.0 y, a continuación, haga clic en herramienta de red de cliente.  
  
2.  Haga clic en la ficha General.  
  
3.  En el cuadro de biblioteca de red de forma predeterminada, haga clic en TCP/IP.  
  
4.  Haga clic en Aceptar para guardar los cambios y salir de la utilidad.  
  
 Si se tiene acceso a un servidor SQL específico desde un servidor Web, deberá ejecutar la herramienta de configuración de cliente de SQL Server en el equipo servidor Web. Para cambiar la biblioteca de red para una conexión específica de SQL Server, configure el software cliente de SQL Server en el equipo servidor Web.  
  
### <a name="to-configure-the-web-server-a-specific-sql-server"></a>Para configurar el servidor Web (un servidor SQL específico)  
  
### <a name="for-microsoft-sql-server-65"></a>Para Microsoft SQL Server 6.5:  
  
1.  En el menú Inicio, elija programas, elija Microsoft SQL Server 6.5 y, a continuación, haga clic en utilidad de configuración de cliente de SQL.  
  
2.  Haga clic en la ficha Opciones avanzadas.  
  
3.  En el cuadro servidor, escriba el nombre del servidor para conectarse a mediante Sockets TCP/IP.  
  
4.  En el cuadro Nombre del archivo DLL, seleccione Sockets TCP/IP.  
  
5.  Haga clic en Agregar o modificar. Todos los orígenes de datos que apunte a este servidor usará ahora Sockets TCP/IP.  
  
6.  Haga clic en listo.  
  
### <a name="for-microsoft-sql-server-70"></a>Para Microsoft SQL Server 7.0:  
  
1.  En el menú Inicio, elija programas, elija Microsoft SQL Server 7.0 y, a continuación, haga clic en utilidad de configuración del cliente.  
  
2.  Haga clic en la ficha General.  
  
3.  Haga clic en Agregar.  
  
4.  Escriba el alias del servidor en el cuadro de alias de servidor. En el cuadro de bibliotecas de red, haga clic en TCP/IP. En el cuadro Nombre de equipo, escriba el nombre del equipo del equipo que realiza escuchas para los clientes de Sockets TCP/IP. En el cuadro de número de puerto, escriba el puerto en el que escucha el servidor SQL Server.  
  
5.  Haga clic en Aceptar y, a continuación, de nuevo en Aceptar para salir de la utilidad.  
  
## <a name="see-also"></a>Vea también  
 [Aspectos básicos de RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)























---
title: Cargando la capacidad del servidor planificación - Analytics Platform System | Microsoft Docs
description: Esta hoja de cálculo de planeación de capacidad le ayuda a determinar los requisitos para un servidor de carga para cargar datos en almacenamiento de datos paralelos de Analytics Platform System."
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2f0efd7e0688496d5af7887431ca00ae683c874f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63213394"
---
# <a name="loading-server-capacity-planning-worksheet-for-analytics-platform-system"></a>Carga la hoja de planificación de capacidad de servidor para Analytics Platform System
Esta hoja de cálculo de planeación de capacidad le ayuda a determinar los requisitos de servidores de carga para cargar datos en PDW de SQL Server. Utilícelo para crear su plan de compra o el aprovisionamiento de servidores de carga existente.  
  
## <a name="worksheet-notes"></a>Notas de la hoja de cálculo
  
1.  Esta hoja de cálculo se aplica a los servidores que se carga datos con el **dwloader** herramienta de línea de comandos al cargar.  
  
2.  Para cargar datos con Integration Services o una tercera herramienta de carga de terceros, los requisitos pueden variar dependiendo de las diferencias en el proceso de carga.  
  
3.  La mayoría de los requisitos se aplica a la carga ya que los archivos comprimidos o sin comprimir datos; las diferencias en los requisitos se indican en negrita.  
  
## <a name="clipboardmediaclipboard-iconpng-clipboard-capacity-planning-worksheet"></a>![Portapapeles](media/clipboard-icon.png "Portapapeles") hoja de cálculo de planeamiento de capacidad  
  
Imprimir esta hoja de cálculo y rellenarlo con sus propios requisitos.  
  
|Componente|Requisito|Rellene esta columna con sus propios requisitos|Recomendaciones|  
|-------------|---------------|--------------------------------------------------|-------------------|  
|Storage|Número máximo de bytes que va a almacenar en el servidor de la carga en cualquier período de tiempo determinado.|![Icono de lápiz](media/pencil-icon.png "icono de lápiz")|Para determinar los requisitos de almacenamiento, averigüe cuántos datos que va a almacenar en el servidor de la carga en cualquier período de tiempo determinado.  Son los requisitos de capacidad para cargar archivos solamente; el sistema operativo y los archivos de carga deben estar en matrices de discos diferentes.<br /><br />Por ejemplo: Si tiene previsto cargar 100 GB de datos desde el disco 3 veces cada día, pero no eliminar los archivos de datos hasta el final de la semana, a continuación, se necesita un mínimo TB 2.1 para almacenar los archivos de datos. Se recomienda ser conservador y obtener sobre almacenamiento de más de 30% para tener en cuenta las variaciones y crecimiento.  En este ejemplo, sería mejor 2,73 TB de espacio de almacenamiento.|  
|Velocidad de carga|Número máximo de bytes por hora de datos que se va a cargar en PDW.|![Icono de lápiz](media/pencil-icon.png "icono de lápiz")|Esta es una estimación. Cuando se calcula este requisito, se supone que los archivos ya están en el servidor de carga y que otras condiciones de carga son tan eficaz como sea posibles.<br /><br />Por ejemplo: Sin necesidad de descomponer en factores de compresión de los datos, ya que siempre envía dwloader sin comprimir datos en PDW. No es necesario incluir en las conversiones de tipos de datos y el tamaño de la tabla de destino.|  
|red|Tipo de conexión de red.|![Icono de lápiz](media/pencil-icon.png "icono de lápiz")|Determinar el mejor tipo de conexión de red para sus requisitos de velocidad de carga.<br /><br />Por ejemplo: InfiniBand o 10 Gigabit Ethernet proporcionará las velocidades de carga óptimo. Ethernet de 1 Gbit limitará las tasas de carga a 360 GB por hora o menos.|  
|E/S|Bytes por hora para lecturas y escrituras.|![Icono de lápiz](media/pencil-icon.png "icono de lápiz")|Para cargar datos, dwloader debe leer todos los datos del disco antes de enviarlo a PDW.<br /><br />Cada servidor de carga no puede cargar datos más rápidamente que el dispositivo puede recibir datos de todos los orígenes de la carga. Para ahorrar dinero, planee la capacidad para la carga de modo que no supera la capacidad de carga del dispositivo de lectura de E/S.<br /><br />Por ejemplo:<br />PDW recibe y carga datos en un dispositivo de bastidor de 1 a una tasa máxima de 1,8 TB por hora. Para un dispositivo con 2 o más bastidores, la velocidad de carga máxima es de 3,6 TB por hora.<br /><br />Si va a cargar desde varios servidores de carga al mismo tiempo, los requisitos de E/S para cada servidor de carga será menor que cuando un servidor está realizando todas la carga.<br /><br />Por ejemplo: Un servidor de carga puede cargar un máximo de 1,8 TB por hora para un dispositivo de bastidor de 1. Dos servidores de carga podrían cada una al mismo tiempo cargar 900 GB por hora en un dispositivo de bastidor de 1. Niveles más altos de simultaneidad pueden reducir la eficacia y el rendimiento máximo.<br /><br />Para la capacidad de E/S, se tienen en cuenta todas las operaciones de E/S que se producen en el servidor de carga. Si el servidor de carga tiene otro tráfico de E/S, además de cargas de datos, como la recepción de archivos de datos de un servidor ETL, los requisitos de E/S aumentará.<br /><br />Los requisitos de E/S para los datos comprimidos, dependen de la tasa de compresión de datos. dwloader lee los datos comprimidos y, a continuación, descomprime antes de enviarlo a PDW. Cuanto mayor sea la razón de compresión, los datos menos el servidor de carga necesitará leer del disco.<br /><br />Por ejemplo: Si la velocidad de carga necesario es 1,8 TB por hora, y los datos se almacenan en el servidor de carga con la compresión de 2:1, a continuación, el servidor de carga sólo necesita leer 900 GB por hora desde el disco en lugar de 1,8 TB. Una razón de compresión de 3:1 significa que el servidor de carga necesita leer 600 GB por hora desde el disco.|  
|CPU|Número de sockets.|![Icono de lápiz](media/pencil-icon.png "icono de lápiz")|Para cargar los datos sin comprimir, una aplicación intensiva de CPU no es dwloader.  Como mínimo, se recomienda usar un servidor de socket de 2 de los equipos fabricados.<br /><br />Para cargar los datos comprimidos, necesita suficiente capacidad de CPU para descomprimir los datos antes de enviarlo a PDW. dwloader puede ejecutar 10 subprocesos activos al mismo tiempo. Si tiene previsto cargar simultáneamente los 10 archivos comprimidos, se recomienda que el servidor tiene al menos una CPU de 10 núcleos o dos de 6 núcleos CPU.|  
|RAM|GB de memoria que permite a Windows en caché los archivos durante la carga.|![Icono de lápiz](media/pencil-icon.png "icono de lápiz")|dwloader usa muy poca RAM en el servidor de carga. Rendimiento, Windows utiliza memoria para almacenar en caché los archivos de carga después de leerlos desde el disco.<br /><br />Para determinar los requisitos de RAM, consulte la instalación de Windows Server y los requisitos de aplicación parte 3ª. Se recomienda un mínimo de 32 GB, si no tiene requisitos de otros orígenes.<br /><br />Para los datos comprimidos, RAM, más rápida es útil porque se acelerará la descompresión.|  
  
## <a name="see-also"></a>Vea también  
[Adquisición y configuración de servidores de carga](acquire-and-configure-loading-server.md)  
[Cargador de la línea de comandos de dwloader](dwloader.md)  
  

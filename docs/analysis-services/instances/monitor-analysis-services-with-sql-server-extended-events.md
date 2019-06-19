---
title: Supervisar Analysis Services con SQL Server extendida Events | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dc51c444483dc9a89cf0b9edbd557c3dce11a054
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62709267"
---
# <a name="monitor-analysis-services-with-sql-server-extended-events"></a>Supervisar Analysis Services con SQL Server Extended Events
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas-all-aas.md)]
  Eventos extendidos (*xEvents*) es un sistema ligero de supervisión de seguimiento y rendimiento que usa muy pocos recursos del sistema, lo que lo convierte en una herramienta ideal para diagnosticar problemas tanto en los servidores de producción como en los de prueba. También es altamente escalable, configurable y, en SQL Server 2016, más fácil de usar gracias a la nueva compatibilidad de herramienta integrada. En SQL Server Management Studio, en las conexiones con instancias de Analysis Services, puede configurar, ejecutar y supervisar un seguimiento activo, algo parecido al uso de SQL Server Profiler. La adición de mejores herramientas debería convertir a xEvents en un reemplazo más razonable para SQL Server Profiler y crea más simetría en la forma de diagnosticar problemas en el motor de base de datos y las cargas de trabajo de Analysis Services.  
  
 Además de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], también puede configurar sesiones de Eventos extendidos para  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de la manera antigua, por medio de scripting XMLA, como se hacía en las versiones anteriores.  
  
 Todos los eventos de Analysis Services se pueden capturar y destinar a usuarios específicos, según se define en [Eventos extendidos](../../relational-databases/extended-events/extended-events.md).  
  
> [!NOTE]  
>  Vea esta [breve presentación de vídeo](https://www.youtube.com/watch?v=ja2mOHWRVC0&index=1&list=PLv2BtOtLblH1YvzQ5YnjfQFr_oKEvMk19) o lea la [entrada de blog complementaria](http://blogs.msdn.com/b/analysisservices/archive/2015/09/22/using-extended-events-with-sql-server-analysis-services-2016-cpt-2-3.aspx) para obtener más información sobre xEvents para Analysis Services en SQL Server 2016.  
  
  
##  <a name="bkmk_ssas_extended_events_ssms"></a> Usar Management Studio para configurar Analysis Services  
 En las instancias tabulares y multidimensionales, Management Studio proporciona una nueva carpeta de administración que contiene sesiones de xEvents iniciadas por el usuario. Puede ejecutar varias sesiones a la vez. Sin embargo, en la implementación actual, la interfaz de usuario de Eventos extendidos para [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] no admite la actualización ni la reproducción de una sesión existente.  
  
 ![ssas_extended_events_ssms_start](../../analysis-services/instances/media/ssas-extended-events-ssms-start.png "ssas_extended_events_ssms_start")  
  
 **Seleccionar eventos**  
  
 Si ya sabe qué eventos desea capturar, buscarlos es la manera más fácil de agregarlos al seguimiento. De lo contrario, los eventos siguientes se usan habitualmente para supervisar operaciones:  
  
-   **CommandBegin** y **CommandEnd**.  
  
-   **QueryBegin**, **QueryEnd**y **QuerySubcubeVerbose** (muestra la consulta MDX o DAX completa enviada al servidor), además de **ResourceUsage** para estadísticas sobre recursos usados por la consulta y el número de filas devueltas.  
  
-   **ProgressReportBegin** y **ProgressReportEnd** (para operaciones de procesamiento).  
  
-   **AuditLogin** y **AuditLogout** (captura la identidad del usuario con la que una aplicación cliente se conecta a Analysis Services).  
  
 **Seleccionar el almacenamiento de datos**  
  
 Una sesión se puede transmitir en directo a una ventana de Management Studio o guardarse en un archivo para su análisis posterior mediante Power Query o Excel.  
  
-   **event_file** almacena datos de sesión en un archivo .xel.  
  
-   **event_stream** habilita la opción **Observar datos en directo** de Management Studio.  
  
-   **ring_buffer** almacena datos de sesión en memoria mientras el servidor se esté ejecutando. Al reiniciar el servidor, los datos de sesión se descartan.  
  
 **Agregar campos de evento**  
  
 Asegúrese de configurar la sesión de modo que incluya campos de evento para poder ver fácilmente la información interesante.  
  
 **Configurar** es una opción del extremo del cuadro de diálogo.  
  
 ![ssas-xevents-configure](../../analysis-services/instances/media/ssas-xevents-configure.PNG "ssas-xevents-configure")  
  
 En Configuración, en la pestaña Campos de evento, seleccione **TextData** para que este campo aparezca junto al evento y muestre los valores devueltos, incluidas las consultas que se están ejecutando en el servidor.  
  
 Después de configurar una sesión para los eventos deseados y el almacenamiento de datos, puede hacer clic en el botón Script para enviar la configuración a uno de los destinos admitidos, que incluye un archivo, una nueva consulta en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]y el Portapapeles.  
  
 **Actualizar sesiones**  
  
 Una vez creada la sesión, asegúrese de actualizar la carpeta Sesiones de Management Studio para ver la sesión que acaba de crear. Si configuró un event_stream, puede hacer clic con el botón derecho en el nombre de la sesión y seleccionar **Observar datos en directo** para supervisar la actividad del servidor en tiempo real.  
  
##  <a name="bkmk_script_start"></a> Script XMLA para iniciar Extended Events en Analysis Services  
 El seguimiento de Eventos extendidos se habilita mediante un comando de script de objeto de creación XMLA similar como se muestra a continuación:  
  
```  
<Execute ...>  
   <Command>  
      <Batch ...>  
         <Create ...>  
            <ObjectDefinition>  
               <Trace>  
                  <ID>trace_id</ID>  
                  <Name>trace_name</Name>  
                  <ddl300_300:XEvent>  
                     <event_session ...>  
                        <event package="AS" name="AS_event">  
                           <action package="PACKAGE0" .../>  
                        </event>  
                        <target package="PACKAGE0" name="asynchronous_file_target">  
                           <parameter name="filename" value="data_filename.xel"/>  
                           <parameter name="metadatafile" value="metadata_filename.xem"/>  
                        </target>  
                     </event_session>  
                  </ddl300_300:XEvent>  
               </Trace>  
            </ObjectDefinition>  
         </Create>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 Donde el usuario definirá los siguientes elementos, según las necesidades del seguimiento:  
  
 *trace_id*  
 Define el identificador único de este seguimiento.  
  
 *trace_name*  
 El nombre proporcionado a este seguimiento; normalmente una definición legible del mismo. Es una práctica común usar el valor de *trace_id* como nombre.  
  
 *AS_event*  
 El evento de Analysis Services que se expondrá. Consulte [Eventos de seguimiento de Analysis Services](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events) para ver los nombres de los eventos.  
  
 *data_filename*  
 El nombre del archivo de datos que contiene los datos de los eventos. Este nombre se añade como sufijo con una marca de tiempo para evitar sobrescribir los datos si el seguimiento se envía repetidamente.  
  
 *metadata_filename*  
 El nombre del archivo de datos que contiene los metadatos de los eventos. Este nombre se añade como sufijo con una marca de tiempo para evitar sobrescribir los datos si el seguimiento se envía repetidamente.  
  
  
##  <a name="bkmk_script_stop"></a> Script XMLA para detener Extended Events en Analysis Services  
 Para detener el objeto de seguimiento de Eventos extendidos, debe eliminar el objeto utilizando un comando de script de objeto de eliminación XMLA como se muestra a continuación:  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Batch ...>  
         <Delete ...>  
            <Object>  
               <TraceID>trace_id</TraceID>  
            </Object>  
         </Delete>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 Donde el usuario definirá los siguientes elementos, según las necesidades del seguimiento:  
  
 *trace_id*  
 Define el identificador único para el seguimiento que se va a eliminar.  
  
  
## <a name="see-also"></a>Vea también  
 [Eventos extendidos](../../relational-databases/extended-events/extended-events.md)  
  
  

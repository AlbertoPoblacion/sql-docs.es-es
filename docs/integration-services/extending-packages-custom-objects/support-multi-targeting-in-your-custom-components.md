---
title: Admitir múltiples versiones de los componentes personalizados | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ec611374-16bf-4a56-8fd9-45d3ddd7befc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 91524408998df8be0df4ee5d4ede0b641dbaa2a4
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "71287226"
---
# <a name="support-multi-targeting-in-your-custom-components"></a>Admitir múltiples versiones de los componentes personalizados

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


 Ahora puede usar el Diseñador SSIS en SQL Server Data Tools (SSDT) para crear, mantener y ejecutar paquetes que se destinen a SQL Server 2016, SQL Server 2014 o SQL Server 2012. Para obtener SSDT para Visual Studio 2015, consulte [Descargar SQL Server Data Tools](../../ssdt/download-sql-server-data-tools-ssdt.md). 

 En el Explorador de soluciones, haga clic con el botón derecho en un proyecto de Integration Services y seleccione **Propiedades** para abrir las páginas de propiedades del proyecto. En la pestaña **General** de **Propiedades de configuración**, seleccione la propiedad **TargetServerVersion** y luego elija SQL Server 2016, SQL Server 2014 o SQL Server 2012.  
   
 ![Propiedad TargetServerVersion en el cuadro de diálogo Propiedades del proyecto](../../integration-services/media/targetserverversion2.png "Propiedad TargetServerVersion en el cuadro de diálogo Propiedades del proyecto")  
 
 ## <a name="multiple-version-support-and-multi-targeting-for-custom-components"></a>Compatibilidad con múltiples versiones para componentes personalizados
 
Los cinco tipos de extensiones personalizadas de SSIS admiten compatibilidad con múltiples versiones.
-   Administradores de conexión
-   Tareas
-   Enumerators
-   Proveedores de registro
-   Componentes de flujo de datos

Para las extensiones administradas, el Diseñador SSIS carga la versión de la extensión para la versión de destino especificada. Por ejemplo:
-   Cuando la versión de destino es SQL Server 2012, el diseñador carga la versión 2012 de la extensión.
-   Cuando la versión de destino es SQL Server 2016, el diseñador carga la versión 2016 de la extensión.

Las extensiones de COM no son compatibles con múltiples versiones. El Diseñador SSIS carga siempre la extensión de COM para la versión actual de SQL Server, independientemente de la versión de destino especificada.

## <a name="add-basic-support-for-multiple-versions-and-multi-targeting"></a>Agregar compatibilidad básica para múltiples versiones

Para obtener instrucciones básicas, consulte [Getting your SSIS custom extensions to be supported by the multi-version support of SSDT 2015 for SQL Server 2016](https://blogs.msdn.microsoft.com/ssis/2016/04/19/getting-your-ssis-custom-extensions-to-be-supported-by-the-multi-version-support-of-ssdt-2015-for-sql-server-2016/) (Obtener las extensiones personalizadas de SSIS que debe admitir la compatibilidad con múltiples versiones de SSDT 2015 para SQL Server 2016). Esta entrada de blog describe los siguientes pasos o requisitos.

-   Implemente los ensamblados en las carpetas adecuadas.

-   Cree un archivo de asignación de extensiones para SQL Server 2014 y versiones posteriores.

## <a name="add-code-to-switch-versions"></a>Agregar código para cambiar las versiones

### <a name="switch-versions-in-a-custom-connection-manager-task-enumerator-or-log-provider"></a>Cambiar versiones en un administrador de conexiones personalizado, tarea, enumerador o proveedor de registro

Para un administrador de conexiones personalizado, una tarea, un enumerador o un proveedor de registro, agregue lógica de cambio a una versión anterior en el método **SaveToXML**.

```csharp
public void SaveToXML(XmlDocument doc, IDTSInfoEvents events)
{
    if (TargetServerVersion == DTSTargetServerVersion.SQLServer2014)
    {
        // Add logic to downgrade from SQL Server 2016 to SQL Server 2014.
    }

    if (TargetServerVersion == DTSTargetServerVersion.SQLServer2012)
    {
         // Add logic to downgrade from SQL Server 2016 to SQL Server 2012.
    }
}
```

### <a name="switch-versions-in-a-custom-data-flow-component"></a>Cambiar versiones en un componente de flujo de datos personalizado

Para un administrador de conexiones personalizado, una tarea, un enumerador o un proveedor de registro, agregue lógica de cambio a una versión anterior en el nuevo método **PerformDowngrade**.

```csharp
public override void PerformDowngrade(int pipelineVersion, DTSTargetServerVersion targetServerVersion)
{
    if (targetServerVersion == DTSTargetServerVersion.DTSTSV_SQLSERVER2014)
    {
        // Add logic to downgrade from SQL Server 2016 to SQL Server 2014.
        ComponentMetaData.Version = 8;
    }

    if (targetServerVersion == DTSTargetServerVersion.DTSTSV_SQLSERVER2012)
    {
          // Add logic to downgrade from SQL Server 2016 to SQL Server 2012.
        ComponentMetaData.Version = 6;
    }
}
```

## <a name="common-errors"></a>Errores comunes

### <a name="invalidcastexception"></a>InvalidCastException

**Mensaje de error.** No se puede convertir el objeto COM del tipo "System.__ComObject" al tipo de interfaz "Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100". No se pudo realizar esta operación porque la llamada QueryInterface en el componente COM para la interfaz con IID "{BE8C48A3-155B-4810-BA5C-BDF68A659E9E}" generó el siguiente error: No se admite dicha interfaz (excepción de HRESULT: 0x80004002 (E_NOINTERFACE)). (Microsoft.SqlServer.DTSPipelineWrap).

**Solución.** Si la extensión personalizada hace referencia a ensamblados de interoperabilidad de SSIS, como Microsoft.SqlServer.DTSPipelineWrap o Microsoft.SqlServer.DTSRuntimeWrap, establezca el valor de la propiedad **Insertar tipos de interoperabilidad** en **False**.

![Insertar tipos de interoperabilidad](../../integration-services/extending-packages-custom-objects/media/embed-interop-types.png)

### <a name="unable-to-load-some-types-when-target-version-is-sql-server-2012"></a>No se pueden cargar algunos tipos cuando la versión de destino es SQL Server 2012

Este problema afecta a determinados tipos, como IErrorReportingService o IUserPromptService.

**Mensaje de error (ejemplo).** No se puede cargar el tipo "Microsoft.DataWarehouse.Design.IErrorReportingService" del ensamblado "Microsoft.DataWarehouse, Version=13.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91".

**Solución alternativa.** Use un Cuadro de mensajes en lugar de estas interfaces cuando la versión de destino sea SQL Server 2012.


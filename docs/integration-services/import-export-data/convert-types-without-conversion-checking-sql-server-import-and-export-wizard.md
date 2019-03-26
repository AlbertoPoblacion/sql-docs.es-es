---
title: Convertir tipos sin comprobar conversión (Asistente para importación y exportación de SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 01/11/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.impexpwizard.nomappingfile.f1
ms.assetid: 87d9d3e5-477f-4117-a37f-bff53ea3e14d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d5e0afe01fea1855dde6e174a12d6a9971e78b83
ms.sourcegitcommit: 5683044d87f16200888eda2c2c4dee38ff87793f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2019
ms.locfileid: "58222169"
---
# <a name="convert-types-without-conversion-checking-sql-server-import-and-export-wizard"></a>Convertir tipos sin comprobar conversión (Asistente para importación y exportación de SQL Server)
  Después de seleccionar las tablas y vistas existentes para copiar o revisar la consulta que ha proporcionado, el Asistente para importación y exportación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] puede mostrar **Convertir tipos sin comprobar conversión**. El asistente muestra esta página cuando no puede encontrar uno o varios de los archivos de asignación y de conversión de tipo de datos que necesita para asignar tipos de datos entre el origen y el destino. La página incluye información que le ayudará a comprender qué falta.
  
 Haga clic en **Siguiente** para continuar sin saber si las conversiones de tipos de datos se realizarán correctamente. De lo contrario, haga clic en **Atrás** para cambiar las selecciones o haga clic en **Cancelar** para salir del asistente.

## <a name="screen-shot-of-the-convert-types-page"></a>Captura de pantalla de la página Convertir tipos  
  
La siguiente captura de pantalla muestra un ejemplo de la página del asistente **Convertir tipos sin comprobar conversión** .

![Convertir tipos](../../integration-services/import-export-data/media/convert-types.png)

El problema es que el asistente no puede encontrar un archivo de asignación que asigne tipos de datos para el destino seleccionado.

La información de esta página no incluye el nombre del archivo de asignación que falta. Dado que el asistente no sabe si existe un archivo para el proveedor de datos especificado, no puede proporcionar un nombre para el archivo que falta.

## <a name="whats-next"></a>¿Qué sigue?  
 Después de hacer clic en **Siguiente** para continuar sin saber si las conversiones de tipos de datos se realizarán correctamente, la siguiente página es **Guardar y ejecutar paquete**. En esta página, especifique si quiere ejecutar la operación de copia inmediatamente. Según la configuración, también puede guardar el paquete de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creado por el asistente para personalizarlo y volver a usarlo más adelante. Para más información, vea [Guardar y ejecutar paquete](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).  

## <a name="see-also"></a>Vea también
[Asignación de tipos de datos en el Asistente para importación y exportación de SQL Server](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)

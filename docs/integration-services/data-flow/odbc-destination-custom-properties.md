---
title: Propiedades personalizadas de los destinos ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 07508c40-6c08-4359-96cd-8ff17671244d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9c1775b42624d755da4642d0c17c277c3b254eb4
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2019
ms.locfileid: "65726661"
---
# <a name="odbc-destination-custom-properties"></a>ODBC Destination Custom Properties

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  En la tabla siguiente se describen las propiedades personalizadas del destino ODBC. Todas las propiedades se pueden establecer a partir de expresiones SSIS.  
  
|Nombre de propiedad|Tipo de datos|Descripción|  
|-------------------|---------------|-----------------|  
|Conexión|Conexión ODBC|Conexión ODBC para acceder a la base de datos de destino.|  
|BatchSize|Integer|Tamaño de lote para la carga masiva. Es el número de filas cargadas como un lote. Esto solo es válido si se admite el enlace de parámetro de modo de fila. Si el enlace parámetro de modo de fila no se admite, el tamaño de lote es 1.|  
|BindCharColumnAs|Integer (enumeración)|Esta propiedad determina cómo el destino ODBC enlaza las columnas con tipos string de varios bytes como SQL_CHAR, SQL_VARCHAR o SQL_LONGVARCHAR.<br /><br /> Los valores posibles son Unicode (0), que enlaza las columnas como SQL_C_WCHAR, y ANSI (1), que enlaza las columnas como SQL_C_CHAR). El valor predeterminado es Unicode (0).<br /><br /> Unicode es la mejor opción para la mayoría de los proveedores ODBC 3.x y los proveedores ODBC 2.x que permiten el enlace de parámetros CHAR como cadenas anchas. Cuando selecciona Unicode y ExposeCharColumnsAsUnicode es True, el usuario no necesita especificar la página de códigos que usa la base de datos de origen.<br /><br /> **Nota:** Esta propiedad no está disponible en el **Editor de destino ODBC**, pero se puede definir con el **Editor avanzado**.|  
|BindNumericAs|Integer (enumeración)|Esta propiedad determina el modo en que el destino ODBC enlaza columnas con datos numéricos con los tipos de datos SQL_TYPE_NUMERIC y SQL_TYPE_DECIMAL.<br /><br /> Los valores posibles son Char (0), que enlaza las columnas como SQL_C_CHAR y Numeric (1), que enlaza las columnas como SQL_C_NUMERIC. El valor predeterminado es Char (0).<br /><br /> **Nota**: Esta propiedad no está disponible en el **Editor de destino ODBC**, pero se puede definir con el **Editor avanzado**.|  
|DefaultCodePage|Integer|Página de códigos que se usará para las columnas de cadena.<br /><br /> **Nota**: Esta propiedad no está disponible en el **Editor de destino ODBC**, pero se puede definir con el **Editor avanzado**.|  
|InsertMethod|Integer (enumeración)|Método usado para insertar los datos. Los valores posibles son fila por fila (0) y lote (1). El valor predeterminado es lote (1).<br /><br /> Para obtener más información sobre estas opciones, vea “Opciones de carga” en [Destino de ODBC](../../integration-services/data-flow/odbc-destination.md).|  
|StatementTimeout|Integer|Número de segundos que se esperará a que una instrucción SQL se ejecute antes de volver, con un error, a la aplicación. El valor predeterminado es 120.|  
|TableName|String|Nombre de la tabla de destino donde los datos se insertan.|  
|TransactionSize|Integer|Número de inserciones en una sola transacción. El valor predeterminado es 0, que significa que el destino ODBC funciona en modo de confirmación automática.<br /><br /> Dado que el administrador de conexiones ODBC no admite transacciones distribuidas, es posible establecer esta propiedad con un valor distinto de 0. Sin embargo, si la propiedad **RetainSameConnection** del administrador de conexiones se establece en **true** , esta propiedad se debe establecer en 0.<br /><br /> **Nota**: Esta propiedad no está disponible en el **Editor de destino ODBC**, pero se puede definir con el **Editor avanzado**.|  
|LobChunkSize|Integer|Asignación de tamaño del fragmento para las columnas LOB.|  
  
  

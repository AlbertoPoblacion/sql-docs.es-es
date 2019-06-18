---
title: Implementar una clase DataReader para una extensión de procesamiento de datos | Microsoft Docs
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], data readers
- data readers [Reporting Services]
- DataReader class
- read-only data
ms.assetid: 23e286e7-6074-4fbe-be29-203420d6c3d0
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 1367774e84dd10c2749f46a1ee6c38b8d5f6dd7b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63193902"
---
# <a name="implementing-a-datareader-class-for-a-data-processing-extension"></a>Implementar una clase DataReader para una extensión de procesamiento de datos
  El objeto **DataReader** permite a un cliente recuperar de un origen de datos una secuencia de datos de solo lectura y solo avance. Los resultados se devuelven a medida que se ejecuta la consulta y se almacenan en el búfer de red en el cliente hasta que se los solicita mediante el método **Read** de la clase **DataReader**. Para crear una clase **DataReader**, implemente <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> y, si quiere, <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension>. Al usar un objeto **DataReader**, aumenta el rendimiento de la aplicación tanto al recuperar datos en cuanto están disponibles en lugar de esperar a que se devuelvan los resultados completos de la consulta, como (de forma predeterminada) al almacenar solo una fila a la vez en la memoria, con lo que se reduce la sobrecarga del sistema.  
  
 Después de crear una instancia de la clase **Command**, cree un objeto **DataReader** al llamar a **Command.ExecuteReader** para recuperar filas del origen de datos. La implementación de **DataReader** debe proporcionar dos capacidades básicas: el acceso de solo avance a los conjuntos de resultados obtenidos al ejecutar un comando y el acceso a los tipos de columna, los nombres y los valores dentro de cada fila. Los clientes usan el método **Read** del objeto **DataReader** para obtener una fila de los resultados de la consulta.  
  
 En el Diseñador de informes, el objeto **DataReader** se usa para recuperar una lista de campos, así como información de esquema sobre el conjunto de resultados. Esto se logra al implementar los métodos **GetName**, **GetValue**, **GetFieldType** y **GetOrdinal** de la interfaz <xref:Microsoft.ReportingServices.DataProcessing.IDataReader>.  
  
 La interfaz <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension> le permite proporcionar información de agregaciones concretas acerca del conjunto de resultados. Para obtener un ejemplo de implementación de la clase **DataReader**, vea [Ejemplos del producto SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Consulte también  
 [Extensiones de Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implementar una extensión de procesamiento de datos](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Biblioteca de extensiones de Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

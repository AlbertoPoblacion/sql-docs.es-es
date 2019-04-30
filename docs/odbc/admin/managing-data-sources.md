---
title: Administrar orígenes de datos | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- deleting data sources [ODBC], ODBC data source administrator
- data sources [ODBC], ODBC data source administrator
- adding data sources [ODBC], ODBC data source administrator
- removing data sources [ODBC], ODBC data source administrator
- ODBC data source administrator [ODBC], data source management
ms.assetid: 67cc4945-4850-4eb4-8da6-b835ddaeca4c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6a1f8893351ceb68ebd7c42e3ac82c876c01c10b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63198759"
---
# <a name="managing-data-sources"></a>Administrar orígenes de datos
Después de haber instalado a un controlador ODBC desde el programa de instalación del controlador, puede definir uno o varios orígenes de datos para él. El nombre del origen de datos (DSN) debe proporcionar una descripción única de los datos; Por ejemplo, *nóminas* o *cuentas por pagar*. Se enumeran los orígenes de datos de usuario y del sistema que se definen para todos los controladores instalados actualmente en el **DSN de usuario** o **DSN de sistema** pestañas de la **Administrador de orígenes de datos ODBC**cuadro de diálogo. Los orígenes de datos de archivo en un directorio determinado se muestran en el **DSN de archivo** pestaña; se especifica el directorio que se mostrará en el **buscar en** cuadro el **DSN de archivo** ficha.  
  
> [!NOTE]  
>  Para administrar un origen de datos que se conecta a un controlador de 32 bits en plataformas de 64 bits, utilice c:\windows\sysWOW64\odbcad32.exe. Para administrar un origen de datos que se conecta a un controlador de 64 bits, utilice c:\windows\system32\odbcad32.exe. En **herramientas administrativas** en un sistema operativo de Windows 8 de 64 bits, hay iconos de 32 bits tanto 64-bit **Administrador de orígenes de datos ODBC** cuadro de diálogo.  
  
 Si usas el odbcad32.exe 64 bits para configurar o quitar un DSN que se conecta a un controlador de 32 bits, por ejemplo, **controlador es Microsoft Access (\*.mdb)**, recibirá el mensaje de error siguiente:  
  
```  
The specified DSN contains an architecture mismatch between the Driver and Application  
```  
  
 Para resolver este error, utilice el odbcad32.exe 32 bits para configurar o quitar el DSN.  
  
 Un origen de datos asocia un controlador ODBC específico con los datos que desea tener acceso a través de ese controlador. Por ejemplo, puede crear un origen de datos para usar el controlador ODBC dBASE para tener acceso a uno o varios archivos dBASE se encuentra en un directorio específico en el disco duro o una unidad de red. Mediante el Administrador de orígenes de datos ODBC, puede agregar, modificar y eliminar orígenes de datos, como se describe en la tabla siguiente.  
  
|Acción|Descripción|  
|------------|-----------------|  
|Agregar orígenes de datos|Es posible agregar varios orígenes de datos, cada una de ellas se asocia un controlador de algunos datos que desea tener acceso mediante el uso de ese controlador. Asigne un nombre que identifica ese origen de datos a cada origen de datos. Por ejemplo, si crea un origen de datos para un conjunto de archivos de dBASE que contienen información de cliente, podría denominar el origen de datos "Clientes". Las aplicaciones suelen mostrar los nombres de origen de datos para los usuarios elijan.<br /><br /> Agregar un origen de datos de archivo es ligeramente diferente de agregar orígenes de datos del sistema o de usuario. Para obtener más información, consulte el Administrador de orígenes de datos ODBC a archivo de ayuda.|  
|Modificar orígenes de datos|Según sus requisitos, le resultará necesario volver a configurar los orígenes de datos. Puede restablecer las opciones, haga clic en **configurar** en cualquier cuadro de diálogo del programa de instalación de controlador.|  
|Eliminar orígenes de datos|Haga clic en **quitar** después de seleccionar un origen de datos.|  
  
 Para obtener más información acerca de los orígenes de datos de archivo, consulte [conecta orígenes de datos de archivo utilizando](../../odbc/reference/develop-app/connecting-using-file-data-sources.md) o [SQLDriverConnect, función](../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="see-also"></a>Vea también  
 [Administrador de orígenes de datos ODBC](../../odbc/admin/odbc-data-source-administrator.md)

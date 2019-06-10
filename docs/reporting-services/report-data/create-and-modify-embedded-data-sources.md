---
title: Creación y modificación de orígenes de datos incrustados | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: 1c38c2e8-7a29-4f79-a4a3-85ed2b13723b
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0daca68faa97a59b9c98b13ab9ca8f867341917c
ms.sourcegitcommit: 1800fc15075bb17b50d0c18b089d8a64d87ae726
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2019
ms.locfileid: "66500467"
---
# <a name="create-and-modify-embedded-data-sources"></a>Creación y modificación de orígenes de datos incrustados
  Un origen de datos incrustado se define en una definición de informe y se usa solamente en ese informe.  
  
## <a name="to-create-an-embedded-data-source-in-report-designer"></a>Para crear un origen de datos incrustado en el Diseñador de informes  
  
1.  En la barra de herramientas del panel Datos de informe, haga clic en **Nuevo** y, a continuación, haga clic en **Origen de datos**. Se abre el cuadro de diálogo **Propiedades del origen de datos** .  
  
    > [!NOTE]  
    >  Si el panel Datos de informe no es visible, haga clic en **Datos de informe** en el menú **Ver** .  
  
2.  En el cuadro de texto **Nombre** , escriba un nombre para el origen de datos o acepte el valor predeterminado. El nombre del origen de datos se utiliza internamente en el informe. Para evitar confusiones, se recomienda que el nombre del origen de datos contenga el nombre de la base de datos especificada en la cadena de conexión.  
  
3.  Compruebe que está seleccionada la opción **Conexión incrustada** y haga lo siguiente.  
  
    1.  En la lista desplegable **Tipo** , seleccione un tipo de origen de datos (por ejemplo, **Microsoft SQL Server** u **OLE DB**).  
  
    2.  Especifique una cadena de conexión usando una de las alternativas siguientes:  
  
        -   Escriba la cadena de conexión directamente en el cuadro de texto **Cadena de conexión** . Para consultar una lista de cadenas de conexión de ejemplo, vea [Conexiones de datos, orígenes de datos y cadenas de conexión en el Generador de informes](data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md) o [Conexiones de datos, orígenes de datos y cadenas de conexión &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
        -   Haga clic en el botón de expresión (**fx** ) para crear una expresión que dé como resultado una cadena de conexión. En el cuadro de diálogo **Expresión** , escriba la expresión en el panel Expresión. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
        -   Haga clic en **Editar** para abrir el cuadro de diálogo **Propiedades de conexión** para el tipo de origen de datos que eligió en el paso 2.  
  
             Rellene los campos del cuadro de diálogo **Propiedades de conexión** según corresponda para el tipo de origen de datos. Las propiedades de conexión incluyen el tipo de origen de datos, el nombre del origen de datos, y las credenciales que se deben usar. Después de especificar los valores en este cuadro de diálogo, haga clic en **Probar conexión** para comprobar que el origen de datos está disponible y que las credenciales que especificó son correctas. Para más información sobre tipos de orígenes de datos específicos, vea los temas en [Agregar datos de orígenes de datos externos &#40;SSRS&#41;](../../reporting-services/report-data/add-data-from-external-data-sources-ssrs.md).  
  
    3.  Haga clic en **Credenciales**.  
  
         Especifique las credenciales que se deben usar para este origen de datos. El propietario del origen de datos elige el tipo de credenciales que se admiten.  
  
4.  El nuevo origen de datos incrustado aparece en el panel Datos de informe.  
  
## <a name="to-create-an-embedded-data-source-in-report-builder"></a>Para crear un origen de datos incrustado en el Generador de informes  
  
1.  En la barra de herramientas del panel Datos de informe, haga clic en **Nuevo**y, a continuación, haga clic en **Origen de datos**. Se abre el cuadro de diálogo **Propiedades del origen de datos** .  
  
2.  En el cuadro de texto **Nombre** , escriba un nombre para el origen de datos o acepte el valor predeterminado.  
  
3.  Compruebe que la casilla **Usar una conexión incrustada en el informe** está seleccionada.  
  
    1.  En la lista desplegable **Seleccionar el tipo de conexión** , seleccione un tipo de origen de datos (por ejemplo, **Microsoft SQL Server** o **OLE DB**).  
  
    2.  Especifique una cadena de conexión usando una de las alternativas siguientes:  
  
        -   Escriba la cadena de conexión directamente en el cuadro de texto **Cadena de conexión** . Para obtener ejemplos de cadenas de conexión, vea [Conexiones de datos, orígenes de datos y cadenas de conexión en el Generador de informes](data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
        -   Haga clic en el botón de expresión (**fx** ) para crear una expresión que dé como resultado una cadena de conexión. En el cuadro de diálogo **Expresión** , escriba la expresión en el panel Expresión. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
        -   Haga clic en **Generar** para abrir el cuadro de diálogo **Propiedades de conexión** correspondiente al tipo de origen de datos que eligió en el paso 2.  
  
             Rellene los campos del cuadro de diálogo **Propiedades de conexión** según corresponda para el tipo de origen de datos. Las propiedades de conexión incluyen el tipo de origen de datos, el nombre del origen de datos, y las credenciales que se deben usar. Después de especificar los valores en este cuadro de diálogo, haga clic en **Probar conexión** para comprobar que el origen de datos está disponible y que las credenciales que especificó son correctas.  
  
4.  Haga clic en **Credenciales**.  
  
     Especifique las credenciales que se deben usar para este origen de datos. El propietario del origen de datos elige el tipo de credenciales que se admiten. Para más información, consulte [Especificar información de credenciales y conexión para los orígenes de datos de informes](specify-credential-and-connection-information-for-report-data-sources.md).  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     El origen de datos aparece en el panel Datos de informe.  
  
## <a name="see-also"></a>Consulte también  
 [Conjuntos de datos incrustados y compartidos de informe &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Especificación de información de credenciales y conexión para los orígenes de datos de informes](specify-credential-and-connection-information-for-report-data-sources.md)  
  
  

---
title: Evaluar los objetos de base de datos SAP ASE para la conversión (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: eb996b7c-1eef-4f73-b5e6-2fa6faf7336c
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e7d1b0b68835fe8b909369a87814a3d1c41e07d1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63240246"
---
# <a name="assessing-sap-ase-database-objects-for-conversion-sybasetosql"></a>Evaluar los objetos de base de datos de SAP ASE para la conversión (SybaseToSQL)
Antes de cargar los objetos y migrar datos a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure, debe determinar cómo la complejidad de la migración y cuánto tiempo tardará. SSMA puede crear un informe de evaluación que muestra el porcentaje de objetos y los procedimientos que se convierten correctamente en [!INCLUDE[tsql](../../includes/tsql-md.md)]. SSMA también le permite ver los problemas específicos que pueden causar errores de conversión.  
  
## <a name="create-assessment-reports"></a>Crear informes de evaluación  
Al crear este informe de evaluación, SSMA convierte los objetos de base de datos de SAP Adaptive Server Enterprise (ASE) seleccionados a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o sintaxis SQL de Azure y, a continuación, muestra los resultados.  
  
**Para crear un informe de evaluación**  
  
1.  En el Explorador de metadatos de Sybase, seleccione las bases de datos que desea evaluar.  
  
2.  Para omitir los objetos individuales, desactive las casillas de verificación junto a los objetos que no desea evaluar.  
  
3.  Haga clic en **bases de datos**y, a continuación, seleccione **crear informe**.  
  
    También puede analizar los objetos individuales haciendo clic en un objeto y, a continuación, seleccione **crear informe**.  
  
    SSMA muestra el progreso en la barra de estado en la parte inferior de la ventana. Si está visible el panel de resultados, también verá los mensajes relacionados.  
  
    Una vez completada la evaluación, la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant para Sybase: Aparecerá la ventana de informe de evaluación.  
  
## <a name="use-assessment-reports"></a>Usar informes de evaluación  
La ventana de informe de evaluación contiene tres paneles:  
  
-   El panel izquierdo contiene la jerarquía de objetos que se incluyen en el informe de evaluación. Puede examinar la jerarquía y seleccionar objetos y categorías de objetos para ver el código y las estadísticas de la conversión.  
  
-   El contenido del panel derecho varía en función de qué elemento está seleccionado en el panel izquierdo.  
  
    Si se selecciona un grupo de objetos (por ejemplo, un esquema) o una tabla, el panel derecho muestra dos paneles. El **conversión estadísticas** panel muestra las estadísticas de conversión para los objetos seleccionados. El **objetos por categorías** panel muestra las estadísticas de conversión para el objeto o categorías de objetos.  
  
    Si se selecciona un procedimiento almacenado, vista o desencadenador, el panel derecho contiene las estadísticas, código fuente y código de destino.  
  
    -   El área superior muestra las estadísticas generales para el objeto. Es posible que deba expandir **estadísticas** para ver esta información. 
    -   El área de origen muestra el código fuente del objeto seleccionado en el panel izquierdo. Las áreas resaltadas muestran código fuente problemático.  
    -   El área de destino muestra el código convertido. Texto rojo muestra mensajes de error y el código problemáticos.  
  
-   El panel inferior muestra los mensajes de conversión, agrupados por número de mensaje. Seleccione **errores**, **advertencias**, o **información** para ver las categorías de mensajes y, a continuación, expanda un grupo de mensajes. Haga clic en un mensaje individual para seleccionar el objeto en el panel izquierdo y, después, mostrar los detalles en el panel derecho.  
  
## <a name="analyze-conversion-problems-by-using-the-assessment-report"></a>Análisis de problemas de conversión con el informe de evaluación  
El **paneles de estadísticas de conversión** muestran las estadísticas de la conversión. Si el porcentaje de cualquier categoría es inferior al 100%, debe determinar por qué la conversión no tuvo éxito.  
  
**Para ver los problemas de conversión**  
  
1.  Crear el informe de evaluación mediante el uso de las instrucciones que aparecen en el procedimiento anterior.  
  
2.  En el panel izquierdo, expanda los esquemas o las carpetas que tienen un icono rojo de error. Continúe expandiendo los elementos hasta que haya seleccionado un elemento individual que no se pudo conversión.  
  
3.  En la parte superior del panel de origen, seleccione **siguiente problema**.  
    Se resalta el código problemático, como es el código relacionado en el **navegación de destino** panel.  
  
4.  Revise los mensajes de error y, a continuación, determine qué desea hacer con el objeto que produjo el problema de conversión:  
  
    -   Actualice la sintaxis de ASE en SSMA. Puede actualizar la sintaxis solo para los procedimientos almacenados y desencadenadores. Para actualizar la sintaxis, seleccione el objeto en el panel Explorador de metadatos de Sybase, haga clic en el **SQL** ficha y, a continuación, edite el código SQL. Cuando se desplaza fuera del elemento, deberá guardar la sintaxis actualizada. Ver los errores notificados para el objeto en el **informe** ficha.  
  
    -   En el ASE, puede modificar el objeto de ASE para quitar o revisar el código problemático. Para cargar el código actualizado en SSMA, tendrá que actualizar los metadatos. Para obtener más información, consulte [conectarse a Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
    -   El objeto se puede excluir de la migración. En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o explorador de metadatos de SQL Azure y el Explorador de metadatos de Sybase, desactive la casilla de verificación situada junto al elemento antes de cargar los objetos en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure y migrar datos desde el ASE.
  
## <a name="next-steps"></a>Pasos siguientes  
[Convertir objetos de base de datos ASE de SAP &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)  
  
## <a name="see-also"></a>Vea también  
[Migrar bases de datos de ASE de SAP a SQL Server: base de datos SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  

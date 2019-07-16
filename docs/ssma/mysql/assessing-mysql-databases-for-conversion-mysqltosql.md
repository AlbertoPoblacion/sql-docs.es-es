---
title: Evaluación de las bases de datos de MySQL para la conversión (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Assessment reports
ms.assetid: 2a56a003-3b0f-453a-963c-00c9e40933ec
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: ae9210444311267569d5f240d40252d4fe024877
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68139206"
---
# <a name="assessing-mysql-databases-for-conversion-mysqltosql"></a>Evaluación de las bases de datos de MySQL para la conversión (MySQLToSQL)
Antes de cargar los objetos y migrar datos a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure, debe determinar cómo compleja será la migración y cuánto tiempo tardará la migración. SSMA puede crear un informe de evaluación que muestra el porcentaje de objetos que se convertirán correctamente. SSMA también le permite ver los problemas específicos que provocan errores de conversión.  
  
## <a name="creating-assessment-reports"></a>Creación de informes de evaluación  
Al crear este informe de evaluación, SSMA convierte los objetos seleccionados de base de datos de MySQL a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o sintaxis de SQL Azure y, a continuación, muestra los resultados.  
  
**Para crear un informe de evaluación**  
  
1.  En el Explorador de metadatos de MySQL, seleccione los esquemas que se va a evaluar.  
  
2.  Para omitir los objetos individuales, desactive las casillas situadas junto a los.  
  
3.  Haga clic en **esquemas**y, a continuación, seleccione **crear informe**.  
  
    Haga clic en un objeto para analizar objetos individuales. A continuación, seleccione **crear informe**.  
  
    SSMA mostrará el progreso en la barra de estado en la parte inferior de la ventana. Si está visible el panel de resultados, también verá los mensajes en el panel de salida.  
  
    Una vez completada la evaluación, la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant para MySQL, la ventana de informe de evaluación aparecerá.  
  
## <a name="using-assessment-reports"></a>Uso de informes de evaluación  
La ventana de informe de evaluación contiene tres paneles:  
  
-   El panel izquierdo contiene la jerarquía de objetos que se incluyen en el informe de evaluación. Puede examinar la jerarquía y seleccionar objetos y categorías de objetos para ver el código y las estadísticas de la conversión.  
  
-   El contenido del panel derecho depende del elemento que está seleccionado en el panel izquierdo.  
  
    Si se selecciona un grupo de objetos, como el esquema, el panel derecho contiene un panel de estadísticas de conversión y objetos mediante el panel de categorías. El panel de estadísticas de la conversión muestra las estadísticas de conversión para los objetos seleccionados. Los objetos mediante el panel de categorías se muestran las estadísticas de conversión para el objeto o categorías de objetos.  
  
    Si se selecciona una función, procedimiento, tabla o vista, el panel derecho contiene las estadísticas, código fuente y código de destino.  
  
    -   El área superior muestra las estadísticas generales para el objeto. Es posible que deba expandir **estadísticas** para ver esta información.  
  
    -   El área de origen muestra el código fuente del objeto seleccionado en el panel izquierdo. Las áreas resaltadas muestran código fuente problemático.  
  
    -   El área de destino muestra el código convertido. Texto rojo muestra mensajes de error y el código problemáticos.  
  
-   El panel inferior muestra los mensajes de conversión, agrupados por número de mensaje. Puede hacer clic en **errores**, **advertencias**, o **información** para ver las categorías de mensajes y, a continuación, expanda un grupo de mensajes. Haga clic en un mensaje individual para seleccionar el objeto en el panel izquierdo y mostrar los detalles en el panel derecho.  
  
## <a name="analyzing-conversion-problems-by-using-the-assessment-report"></a>Analizar problemas de conversión mediante el informe de evaluación  
El panel de estadísticas de la conversión muestra las estadísticas de la conversión. Si el porcentaje de cualquier categoría es inferior al 100%, debe determinar por qué la conversión no tuvo éxito.  
  
**Para ver los problemas de conversión**  
  
1.  Crear el informe de evaluación mediante el uso de las instrucciones que aparecen en el procedimiento anterior.  
  
2.  En el panel izquierdo, expanda los esquemas o las carpetas que tienen un icono rojo de error. Continúe expandiendo los elementos hasta que haya seleccionado un elemento individual que no se pudo conversión.  
  
3.  En la parte superior del panel de origen, haga clic en **siguiente problema**.  
  
    Se resalta el código problemático, como es el código relacionado en el panel de navegación de destino.  
  
4.  Revise los mensajes de error y, a continuación, determine qué desea hacer con el objeto que produjo el problema de conversión.  
  
-   Actualice la sintaxis de MySQL en SSMA. Puede actualizar la sintaxis solo para los procedimientos y funciones. Para actualizar la sintaxis, seleccione el objeto en el panel Explorador de metadatos de MySQL, haga clic en el **SQL** pestaña y, a continuación, modifique el código SQL. Cuando se desplaza fuera del elemento, se le indicará que guarde la sintaxis actualizada. Puede ver los errores notificados para el objeto en el **informe** ficha.  
  
-   De MySQL, puede modificar el objeto de MySQL para quitar o revisar el código problemático. Para cargar el código actualizado en SSMA, tendrá que actualizar los metadatos. Para obtener más información, consulte [conectar con MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md).  
  
-   El objeto se puede excluir de la migración. En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o explorador de metadatos de SQL Azure y el Explorador de metadatos de MySQL, desactive la casilla de verificación situada junto al elemento antes de cargar los objetos en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure y migrar datos de MySQL.  
  
## <a name="next-step"></a>Paso siguiente  
[Conversión de bases de datos MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>Vea también  
[Bases de datos de migración desde MySQL a SQL Server: base de datos SQL Azure &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  

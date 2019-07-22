---
title: 'Procedimientos: Crear un proyecto de prueba para las pruebas unitarias de base de datos de SQL Server | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 4b3e7ba8-b565-4689-af1a-34cc255b7c60
author: markingmyname
ms.author: maghan
ms.openlocfilehash: cff6d8342ea1fe4d40616bf07e1189e0ffba030e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67897140"
---
# <a name="how-to-create-a-test-project-for-sql-server-database-unit-testing"></a>Procedimientos: Creación de un proyecto de prueba para las pruebas unitarias de base de datos de SQL Server
Antes de empezar a escribir las pruebas unitarias que evalúan los objetos de base de datos, debe crear primero un proyecto de prueba. Este proyecto contiene pruebas unitarias de SQL Server, pero podría contener otros tipos de pruebas.  
  
Puede colocar todas las pruebas unitarias de SQL Server de un proyecto de base de datos determinado en un solo proyecto de prueba. Sin embargo, puede ser conveniente proyectos de prueba adicionales en función de sus respuestas a las preguntas siguientes:  
  
|||  
|-|-|  
|**Pregunta**|**Decisión**|  
|¿Las diferentes pruebas unitarias de SQL Server necesitan tener acceso a distintas conexiones de base de datos para la ejecución de prueba o la validación de prueba?|En caso afirmativo, necesita más de un proyecto de prueba. No puede especificar más de una conexión de base de datos para la ejecución de prueba. Sin embargo, puede especificar una conexión de base de datos diferente para la validación de prueba.|  
|¿Desea implementar distintos proyectos de base de datos para las diferentes pruebas unitarias?|En caso afirmativo, necesita más de un proyecto de prueba. Un proyecto de prueba solo puede implementar un proyecto de base de datos.|  
  
Para obtener más información sobre estas preguntas, vea [Cómo: Configurar una ejecución de prueba unitaria de SQL Server](../ssdt/how-to-configure-sql-server-unit-test-execution.md). Como alternativa a la creación de varios proyectos de prueba, también puede proporcionar su propia implementación de Microsoft.Data.Schema.UnitTesting.DatabaseTestService [DatabaseTestService](https://msdn.microsoft.com/library/microsoft.data.schema.unittesting.databasetestservice.aspx).  
  
Tiene tres opciones para agregar un proyecto de prueba a una solución que contenga un proyecto de base de datos:  
  
-   Agregar un proyecto de prueba a la solución. El proyecto de prueba contiene una prueba unitaria estándar, que se puede eliminar. Este proyecto no contiene una clase de prueba unitaria de SQL Server, que se debe agregar.  
  
-   Agregue una nueva prueba unitaria de SQL Server desde el menú **Prueba**. Al agregar la prueba unitaria, SQL Server Data Tools también crea un proyecto de prueba si lo solicita. Este proyecto contiene una clase de prueba unitaria de SQL Server. Las clases de prueba unitaria de SQL Server contienen una o más pruebas unitarias.  
  
-   Crear una prueba unitaria desde un procedimiento almacenado, una función o un desencadenador desde un proyecto abierto en el Explorador de objetos de SQL Server. Al crear la prueba unitaria, SQL Server Data Tools también crea un proyecto de prueba, si lo solicita. Este proyecto contiene una clase de prueba unitaria de SQL Server. Las clases de prueba unitaria de SQL Server contienen una o más pruebas unitarias.  
  
Cada enfoque se describe en los procedimientos siguientes.  
  
### <a name="to-add-a-test-project-to-an-existing-solution"></a>Para agregar un proyecto de prueba a una solución existente  
  
1.  En el menú **Archivo** , elija **Nuevo**y, a continuación, haga clic en **Proyecto**.  
  
    Aparecerá el cuadro de diálogo **Nuevo proyecto** .  
  
2.  En **Plantillas instaladas**, expanda el nodo **SQL Server** y, a continuación, seleccione **Proyecto de base de datos de SQL Server**.  
  
3.  En **Nombre**, escriba un nombre de proyecto.  
  
### <a name="to-create-a-test-project-with-a-sql-server-unit-test-class"></a>Para crear un proyecto de prueba con una clase de prueba unitaria de SQL Server  
  
-   Siga el procedimiento que se describe en [Cómo: Crear una prueba unitaria de SQL Server vacía](../ssdt/how-to-create-an-empty-sql-server-unit-test.md) o [Cómo: Crear pruebas unitarias de SQL Server para funciones, desencadenadores y procedimientos almacenados](../ssdt/how-to-create-unit-tests-for-functions-triggers-stored-procedures.md).  
  
## <a name="see-also"></a>Consulte también  
[Crear y definir pruebas unitarias de SQL Server](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
  

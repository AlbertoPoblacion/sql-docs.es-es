---
title: 'Procedimientos: Usar el Diseñador de tablas para administrar tablas y relaciones | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.design.table.columnspecification.index.dialog
- sql.data.tools.design.table.columnsgrid.view
- sql.data.tools.design.table.scriptpanel
ms.assetid: 322a2903-d7a6-4f52-9048-1bd413b4c799
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 1d70fe813437ff6204173dc20df90d029f6568fb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65096861"
---
# <a name="how-to-use-the-table-designer-to-manage-tables-and-relationships"></a>Procedimientos: Uso el Diseñador de tablas para administrar tablas y relaciones
El Diseñador de tablas proporciona una experiencia visual junto con el Editor de Transact\-SQL para crear y editar estructuras de tablas, incluidos objetos de programación específicos de tablas, para bases de datos de SQL Server.  Se inicia al crear una nueva tabla para una base de datos conectada o un proyecto, o al hacer doble clic para editar una tabla en el Explorador de objetos de SQL Server o en el Explorador de soluciones.  
  
El diseñador consta de la cuadrícula de columnas, el panel de scripts y el panel Contexto. La cuadrícula de columnas muestra todas las columnas de la tabla. En esta cuadrícula se pueden agregar, editar y eliminar columnas.  El panel de contexto le ofrece una vista lógica de la definición de tabla (claves, índices, restricciones, desencadenadores, etc.) y le permite seleccionar un objeto para resaltar sus relaciones con las columnas individuales. También puede agregar objetos nuevos a la tabla en este panel, así como editar las propiedades de un objeto seleccionado en la cuadrícula de propiedades. El panel de scripts muestra la definición de la estructura de tabla, y resalta el script del objeto seleccionado en el panel Contexto o en la cuadrícula de columnas. Es posible editar el script viendo en paralelo la cuadrícula de columnas y el panel Contexto. Los cambios realizados en cualquiera de los tres paneles se propagarán a los otros dos inmediatamente.  
  
> [!WARNING]  
> Los procedimientos siguientes usan entidades creadas en procedimientos de las secciones [Desarrollo de bases de datos conectadas](../ssdt/connected-database-development.md) y [Desarrollo de bases de datos sin conexión orientado a proyectos](../ssdt/project-oriented-offline-database-development.md).  
  
### <a name="to-create-a-new-table"></a>Para crear una tabla  
  
1.  Abra el proyecto TradeDev con el que ha trabajado en procedimientos anteriores.  
  
2.  En el **Explorador de soluciones**, expanda la carpeta **dbo**, haga clic con el botón secundario en la carpeta **Tablas**, seleccione **Agregar** y, a continuación, haga clic en **Tabla**.  
  
3.  Asigne a la nueva tabla el nombre **Shipper** y haga clic en **Agregar**.  
  
4.  Se abrirá el Diseñador de tablas. En la cuadrícula de columnas, agregue a la tabla una nueva columna denominada **ShipperName** y con el tipo de datos **int**.  
  
5.  Observe que también puede editar las propiedades de las columnas en la ventana **Propiedades**. Haga clic en la columna **ShipperName** y después, en la ventana **Propiedades**, cambie el valor **DataType** de esta columna a **nvarchar** y el valor **length** a **128**. Observe que en cuanto sale del campo, el panel de scripts y la cuadrícula de columnas del diseñador se actualizan automáticamente para reflejar el cambio.  
  
### <a name="to-create-a-new-foreign-key-constraint"></a>Para crear una nueva restricción de clave externa  
  
1.  Haga clic con el botón secundario en el nodo **Claves externas** en el panel Contexto del diseñador y seleccione **Agregar nueva clave externa**.  
  
2.  Observe que el número de nodo se incrementa automáticamente en 1. Presione ENTRAR para aceptar el nombre predeterminado de la restricción.  
  
3.  Reemplace la definición predeterminada de la restricción en el panel de scripts con lo siguiente.  
  
    ```  
    CONSTRAINT [FK_Shipper_Products] FOREIGN KEY ([Id]) REFERENCES [dbo].[Products]([Id])  
    ```  
  
    Observe que la experiencia de crear y editar entidades de base de datos para un proyecto sin conexión es idéntica a la realización de las tareas con una base de datos conectada.  
  
## <a name="see-also"></a>Consulte también  
[Cómo: Crear objetos de base de datos usando el Diseñador de tablas](../ssdt/how-to-create-database-objects-using-table-designer.md)  
  

---
title: 'Tarea 7: Crear un dominio compuesto | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ae778647-1df0-4952-9a69-0ef6177eea9c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: bbc00117e10e48adbde37b9f0561610feff8f87e
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65488964"
---
# <a name="task-7-creating-a-composite-domain"></a>Tarea 7: Creación de un dominio compuesto
  En esta tarea, creará un dominio compuesto, **validación de direcciones**, que consta de **Address Line**, **Ciudad**, **estado**y  **Código postal** dominios. Un dominio compuesto permite definir una regla entre dominios que afecta a varias dominios de una regla. Un dominio compuesto presenta otras ventajas como la posibilidad de analizar un valor de campo en varios dominios.  Por ejemplo, un valor de un campo Nombre completo se puede analizar en distintos dominios Nombre, Segundo nombre y Apellidos. En este tutorial, solo definirá una regla entre dominios. Consulte [administrar un dominio compuesto](https://msdn.microsoft.com/library/hh510399.aspx) para obtener más detalles.  
  
1.  En el panel izquierdo, haga clic en **crear un dominio compuesto** en la barra de herramientas.  
  
     ![Crear un botón de barra de herramientas del dominio compuesto](../../2014/tutorials/media/et-creatingacompositedomain-01.jpg "crear un botón de barra de herramientas del dominio compuesto")  
  
2.  Escriba **validación de direcciones** para el **nombre de dominio compuesto**.  
  
     ![Dominio compuesto validación de direcciones](../../2014/tutorials/media/et-creatingacompositedomain-02.jpg "dominio compuesto validación de direcciones")  
  
3.  En la lista de dominios seleccione **Address Line**, **Ciudad**, **estado**, y **Zip** y haga clic en **flecha derecha** para agregarlos a la **dominios del dominio compuesto** lista.  
  
4.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo.  
  
## <a name="next-step"></a>Paso siguiente  
 [Tarea 8: Crear una regla de dominio compuesto](../../2014/tutorials/task-8-creating-a-composite-domain-rule.md)  
  
  

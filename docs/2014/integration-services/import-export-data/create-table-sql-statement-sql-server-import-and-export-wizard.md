---
title: Instrucción Create Table de SQL (Asistente para importación y exportación de SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.createtablesql.f1
ms.assetid: 0d6f6b3b-d023-4770-a8a9-65b2977c8d05
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7f541ad24e87bf5bdea9ed8b8c2523a73c81daa9
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2019
ms.locfileid: "58376173"
---
# <a name="create-table-sql-statement-sql-server-import-and-export-wizard"></a>Instrucción Create Table de SQL (Asistente para importación y exportación de SQL Server)
  Use la **instrucción Create Table SQL** cuadro de diálogo para ver la instrucción que se generó automáticamente o modificarlo para sus fines. Si modifica esta instrucción, probablemente también deba realizar cambios asociados en la asignación de columnas y, en adelante, mantener la instrucción SQL modificada manualmente.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] genera una instrucción CREATE TABLE predeterminada basada en el origen de datos conectado. La instrucción predeterminada CREATE TABLE no incluirá el atributo FILESTREAM, aunque la tabla de origen tenga una columna con el atributo FILESTREAM declarado. Para ejecutar un componente [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] con el atributo FILESTREAM, implemente en primer lugar el almacenamiento de FILESTREAM en la base de datos de destino. A continuación, agregue el atributo FILESTREAM a la instrucción CREATE TABLE en el cuadro de diálogo **Crear tabla** . Para más información, vea [Datos de objeto binario grande &#40;Blob&#41; &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 Para obtener más información acerca de este asistente, vea [Asistente para importación y exportación de SQL Server](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Para obtener información acerca de las opciones para iniciar el asistente, así como los permisos necesarios para ejecutar el asistente correctamente, consulte [ejecutar la importación de SQL Server y el Asistente para exportación de](start-the-sql-server-import-and-export-wizard.md).  
  
 La finalidad del Asistente para importación y exportación de SQL Server es copiar datos desde un origen a un destino. El asistente también puede crear una base de datos y tablas de destino. Sin embargo, si tiene que copiar diversas bases de datos o tablas, u otros tipos de objetos de bases de datos, debe utilizar el Asistente para copiar bases de datos. Para más información, consulte [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Opciones  
 **Instrucción SQL**  
 Muestra la instrucción SQL generada automáticamente y permite que se edite.  
  
> [!NOTE]  
>  Si desea incluir un retorno de carro en la instrucción SQL, presione CTRL+ENTRAR. Si presiona solamente ENTRAR, se cierra el cuadro de diálogo.  
  
 **Autogenerar**  
 Restaura la instrucción SQL predeterminada (si se ha modificado) al hacer clic en **Autogenerar**.  
  
  

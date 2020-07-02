---
title: Ensamblados (Motor de base de datos) | Microsoft Docs
description: Una instancia de SQL Server puede hospedar ensamblados que implementan funciones, procedimientos, desencadenadores y agregados definidos por el usuario y tipos escritos en un lenguaje CLR.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration]
- assemblies [CLR integration], about assemblies
- managed code [SQL Server], assemblies
ms.assetid: 4b146437-3061-47f6-9e8c-26eeea10b54e
author: rothja
ms.author: jroth
ms.openlocfilehash: 399c1dca1657c95edd70dcec0ba26619f6001180
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727676"
---
# <a name="assemblies-database-engine"></a>Ensamblados (motor de base de datos)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  En los temas de esta sección se ofrece información que le ayudará a comprender, diseñar e implementar ensamblados.  
  
 Los ensamblados son archivos DLL que se utilizan en una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para implementar funciones, procedimientos almacenados, desencadenadores, agregados definidos por el usuario y tipos definidos por el usuario que se escriben en uno de los lenguajes de código administrado hospedados por el [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Common Language Runtime (CLR), en lugar de en [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 Un ensamblado en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] es un objeto que hace referencia a un módulo de aplicación administrada (archivo .dll) creado en [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Common Language Runtime. Un ensamblado contiene metadatos de clase y código administrado. El primer paso para crear los siguientes objetos de base de datos es cargar un ensamblado en una instancia de SQL Server:  
  
-   Funciones CLR. Para obtener más información, vea [Create CLR Functions](../../relational-databases/user-defined-functions/create-clr-functions.md).  
  
-   Procedimientos almacenados CLR. Para obtener más información, vea [procedimientos almacenados CLR](https://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33).  
  
-   Desencadenadores CLR. Para obtener más información, vea [crear desencadenadores CLR](../../relational-databases/triggers/create-clr-triggers.md).  
  
-   Funciones de agregado definidas por el usuario. Para obtener más información, consulte [crear agregados definidos por el usuario](../../relational-databases/user-defined-functions/create-user-defined-aggregates.md).  
  
-   Tipos definidos por el usuario. Para obtener más información, vea [Tipos definidos por el usuario de CLR](../../relational-databases/native-client/features/using-user-defined-types.md).  
  
 Los ensamblados realizan las funciones siguientes en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Contienen el código administrado que ejecuta la funcionalidad de uno o más de los objetos de base de datos CLR antes mencionados.  
  
-   Contienen metadatos que incluyen el número de versión y la referencia cultural del ensamblado, una clave pública opcional que identifica de manera única la lista de clases del ensamblado, los métodos definidos en el ensamblado y la arquitectura de procesador del ensamblado.  
  
-   Administran el grado en el que el código administrado puede tener acceso a los recursos externos mediante la regulación de los permisos de acceso a código.  
  
-   Contienen metadatos sobre las dependencias de otros ensamblados a los que el ensamblado hace referencia.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Diseñar ensamblados](../../relational-databases/clr-integration/assemblies-designing.md)|Explica las consideraciones previas a la creación de un ensamblado. Se incluyen el empaquetado de los ensamblados, los permisos de acceso a código y otras restricciones.|  
|[Implementar ensamblados](../../relational-databases/clr-integration/assemblies-implementing.md)|Se explica cómo crear y quitar ensamblados, cómo y cuándo se pueden modificar y cómo se recuperan los metadatos sobre los ensamblados.|  
|[Obtener información acerca de los ensamblados](../../relational-databases/clr-integration/assemblies-getting-information.md)|Enumera las vistas de catálogo y las funciones que se pueden utilizar para consultar metadatos sobre ensamblados.|  
  
## <a name="see-also"></a>Consulte también  
 [Conceptos de programación en el ámbito de la integración de Common Language Runtime &#40;CLR&#41;](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  

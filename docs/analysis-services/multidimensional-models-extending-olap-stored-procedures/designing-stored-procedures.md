---
title: "Diseñar procedimientos almacenados | Documentos de Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- stored procedures [Analysis Services], designing
- dependent assemblies [Analysis Services]
- assemblies [Analysis Services]
ms.assetid: af4e7bd5-041b-4a40-9942-0ef6a3af46c6
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4b8b145a22f7d309fbaf69c1da3f6f4bb068fad5
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="designing-stored-procedures"></a>Diseñar procedimientos almacenados
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
El modelo de objeto administrativo Objetos de administración de análisis (AMO) y el modelo de objeto orientado al cliente Objetos de datos [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® (Multidimensional) (ADO MD) se incluyen en los procedimientos almacenados.  
  
 Los procedimientos almacenados deben estar en el ámbito (el servidor o la base de datos) para ser visibles en el nivel de Expresiones multidimensionales (MDX) para ser llamados. Sin embargo, cuando se invoca un procedimiento almacenado, su ámbito no se limita a acciones bajo su elemento primario. Un procedimiento almacenado puede realizar cambios o modificaciones en cualquier lugar del servidor, sujeto únicamente a las limitaciones de seguridad del proceso de usuario que lo invoca o a las limitaciones de la transacción en la que opera.  
  
 Los procedimientos del ámbito del servidor están disponibles en todos los contextos del servidor. Los procedimientos almacenados del ámbito de la base de datos solamente están visibles en el contexto de la base de datos en la que se definen.  
  
 Al igual que con cualquier función MDX, para que pueda continuar una sesión MDX se debe resolver el procedimiento almacenado; los procedimientos almacenados bloquean las sesiones MDX mientras se ejecutan. A menos que exista una razón específica para detener una sesión MDX pendiente de interacción del usuario, se desaconsejan las interacciones del usuario (como los cuadros de diálogo).  
  
## <a name="dependent-assemblies"></a>Ensamblados dependientes  
 Todos los ensamblados dependientes se deben cargar en una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] para que los encuentre Common Language Runtime (CLR). [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] almacena los ensamblados dependientes en la misma carpeta que el ensamblado principal, de manera que CLR resuelve automáticamente todas las referencias de función a las funciones en esos ensamblados.  
  
## <a name="see-also"></a>Vea también  
 [Administración de ensamblados de modelos multidimensionales](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Definir procedimientos almacenados](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  

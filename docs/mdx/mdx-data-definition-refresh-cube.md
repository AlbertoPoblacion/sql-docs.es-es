---
title: "Instrucción REFRESH CUBE (MDX) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Cube
- REFRESH CUBE
- REFRESH_CUBE
- REFRESH
dev_langs: kbMDX
helpviewer_keywords:
- cubes [Analysis Services], cache
- refreshing cache
- REFRESH CUBE statement
- cache [Analysis Services]
ms.assetid: b8c087fb-5d17-4b13-b7cf-9929e9aab35c
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 37649d37d1cef67eb50caf8f3768beba19545988
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-data-definition---refresh-cube"></a>Definición de datos MDX - actualización de cubo
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Actualiza la caché de cliente para un cubo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
REFRESH CUBECube_Name   
```  
  
## <a name="arguments"></a>Argumentos  
 *Restricciones obligatorias Cube_Name*  
 Expresión de cadena válida que proporciona un nombre de cubo.  
  
## <a name="remarks"></a>Comentarios  
 Para las aplicaciones cliente conectadas a una instancia de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], esta instrucción hace que la memoria caché en la aplicación cliente se sincronicen con el servidor. Mientras que esto normalmente se detectará y actualizará automáticamente, el período de tiempo antes de que esto suceda depende de la configuración de la cadena de conexión del cliente. La instrucción REFRESH CUBE actualiza inmediatamente los datos.  
  
 En las aplicaciones cliente conectadas a un cubo local, la instrucción REFRESH CUBE hace que el archivo de cubo local se vuelva a generar.  
  
> [!IMPORTANT]  
>  Los conjuntos con nombre que se almacenan en el servidor no se actualizan.  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones de definición de datos MDX &#40; MDX &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  

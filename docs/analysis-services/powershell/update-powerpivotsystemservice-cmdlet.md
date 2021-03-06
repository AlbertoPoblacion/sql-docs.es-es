---
title: Update-PowerPivotSystemService cmdlet | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a90f1158-68d3-4330-98c1-fb0f81e13328
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 045979085e6d8e1622fef2a961f6c9fdb21d772a
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="update-powerpivotsystemservice-cmdlet"></a>Cmdlet Update-PowerPivotSystemService
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Actualiza el objeto primario del Servicio de sistema de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en la granja.  

>[!NOTE] 
>En este artículo puede contener información no actualizada y ejemplos. Use el cmdlet Get-Help para la versión más reciente.
  
 **Se aplica a:** SharePoint 2010 y SharePoint 2013.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Update-PowerPivotSystemService [-Confirm <switch>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 El cmdlet **Update-PowerPivotSystemService** ejecuta una serie de acciones de actualización en el objeto primario del Servicio de sistema de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , las instancias y las aplicaciones de servicio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en la granja. Todos los servicios y aplicaciones de nivel intermedio de una implementación de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint tienen que ejecutarse en el mismo nivel funcional. Este cmdlet ejecuta las acciones de actualización en todos estos objetos.  
  
 Ejecute este cmdlet después de ejecutar el programa de instalación de SQL Server para instalar una versión más reciente de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint o si ha aplicado una actualización acumulativa en el servidor. Para comprobar si la actualización se requiere, ejecute `Get-PowerPivotSystemService` para revisar la propiedad **NeedsUpgrade** . Si **NeedsUpgrade** es true, es necesario ejecutar los cmdlets para actualizar los objetos de nivel intermedio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en la granja.  
  
 Como en una implementación de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint se incluyen servicios de datos de nivel intermedio y back-end, es necesario ejecutar **Update-PowerPivotEngineService** siempre que se ejecute **Update-PowerPivotSystemService** para asegurarse de que ambos niveles tienen la misma versión en la granja.  
  
 La actualización no se puede revertir a la versión anterior. Si debe revertir a una versión anterior, quite [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de la granja de servidores de SharePoint y vuelva a instalar el software. Para comprobar que la operación de actualización se realiza correctamente, ejecute `Get-PowerPivotSystemService` para revisar las propiedades globales y obtener información de la versión y para comprobar que **NeedsUpgrade** ya no está establecido en true.  
  
## <a name="parameters"></a>Parámetros  
  
### <a name="-confirm-switch"></a>-Confirme \<cambiar >  
 Le solicita confirmación antes de ejecutar el comando. Este valor se habilita de forma predeterminada. Para omitir la respuesta de confirmación de un comando, especifique Confirm:$false en el comando.  
  
|||  
|-|-|  
|¿Requerido?|false|  
|¿Posición?|con nombre|  
|Valor predeterminado||  
|¿Aceptar la entrada de la canalización?|false|  
|¿Aceptar caracteres comodín?|false|  
  
### <a name="commonparameters"></a>\<CommonParameters >  
 Este cmdlet admite los siguientes parámetros:  
  
-   Verbose  
  
-   Depuración  
  
-   ErrorAction  
  
-   ErrorVariable  
  
-   WarningAction  
  
-   WarningVariable  
  
-   OutBuffer  
  
-   OutVariable  
  
 Para más información, vea [about_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Entradas y salidas  
 El tipo de entrada es el tipo de objetos que se pueden canalizar al cmdlet. El tipo de valor devuelto es el tipo de objeto que el cmdlet devuelve.  
  
|||  
|-|-|  
|Entradas|Ninguno.|  
|Resultados|Ninguno.|  
  
  

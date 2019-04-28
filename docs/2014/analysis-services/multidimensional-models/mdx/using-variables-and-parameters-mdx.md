---
title: Usar Variables y parámetros (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- parameters [MDX]
- queries [MDX], variables
- queries [MDX], parameters
- variables [MDX]
ms.assetid: a4754d16-d9c4-49f6-9be0-392180b912e4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fc4ca51b182ca528c6bab05804da4396fbde4dff
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62699492"
---
# <a name="using-variables-and-parameters-mdx"></a>Usar variables y parámetros (MDX)
   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]admite la parametrización de las instrucciones de expresiones multidimensionales (MDX). Las instrucciones con parámetros permiten crear instrucciones genéricas que pueden personalizarse en tiempo de ejecución.  
  
 Al crear una instrucción con parámetros se debe identificar el nombre del parámetro mediante un prefijo con el símbolo de arroba (@). Por ejemplo, @Year sería un nombre de parámetro válido  
  
 MDX solo admite parámetros para valores literales o escalares. Para crear un parámetro que haga referencia a un miembro, conjunto o tupla debería utilizar una función como [StrToMember](/sql/mdx/strtomember-mdx) o [StrToSet](/sql/mdx/strtoset-mdx).  
  
 En el siguiente código XML de ejemplo de análisis (XMLA), el @CountryName parámetro contendrá el cliente para el que se recuperan los datos de país:  
  
```  
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">  
  <Body>  
    <Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
      <Command>  
        <Statement>  
select [Measures].members on 0,   
       Filter(Customer.[Customer Geography].Country.members,   
              Customer.[Customer Geography].CurrentMember.Name =  
              @CountryName) on 1  
from [Adventure Works]  
</Statement>  
      </Command>  
      <Properties />  
      <Parameters>  
        <Parameter>  
          <Name>CountryName</Name>  
          <Value>'United Kingdom'</Value>  
        </Parameter>  
      </Parameters>  
    </Execute>  
  </Body>  
</Envelope>  
```  
  
 Para utilizar esta funcionalidad con OLE DB, debería usarse la interfaz `ICommandWithParameters`. Para utilizar esta funcionalidad con ADOMD.Net, debería usarse la colección **AdomdCommand.Parameters** .  
  
## <a name="see-also"></a>Vea también  
 [Aspectos básicos de scripting MDX &#40;Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md)  
  
  

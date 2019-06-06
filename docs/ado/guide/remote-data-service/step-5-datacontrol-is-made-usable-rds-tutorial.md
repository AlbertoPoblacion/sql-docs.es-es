---
title: 'Paso 5: Control de datos es realizado utilizable (Tutorial de RDS) | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], datacontrol made usable
ms.assetid: ed5c4a24-9804-4c85-817e-317652acb9b4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f654bc1ccd913c5fc31f81cae67ffdb84e80f952
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66704156"
---
# <a name="step-5-datacontrol-is-made-usable-rds-tutorial"></a>Paso 5: Habilitación del uso del control de datos (Tutorial de RDS)
El valor devuelto **Recordset** objeto está disponible para su uso. Puede examinar, desplácese o editarlo tal y como lo haría con cualquier otro **Recordset**. ¿Qué puede hacer con el **Recordset** depende del entorno. Visual Basic y Visual C++ tienen controles visuales que pueden usar un **Recordset** directa o indirectamente con la Ayuda de un control de datos.  
  
> [!IMPORTANT]
>  A partir de Windows 8 y Windows Server 2012, componentes de servidor RDS ya no están incluidos en el sistema operativo de Windows (consulte Windows 8 y [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) para obtener más detalles). Componentes de cliente RDS se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan. Deben migrar las aplicaciones que usan RDS a [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Por ejemplo, si va a mostrar una página Web en Microsoft Internet Explorer, es posible que desee mostrar el **Recordset** datos en un control visual del objeto. No pueden acceder los controles visuales de una página Web un **Recordset** objeto directamente. Sin embargo, puede tener acceso a la **Recordset** objeto a través de la [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md). El **RDS. DataControl** puede ser utilizado por un objeto visual controlar cuándo su [SourceRecordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) propiedad está establecida en el **Recordset** objeto.  
  
 El objeto visual del control debe tener su **DATASRC** parámetro establecido en el **RDS. DataControl**y su **DATAFLD** propiedad establecida en un **Recordset** campo (columna) del objeto.  
  
 En este tutorial, establezca la **SourceRecordset** propiedad:  
  
```vb
Sub RDSTutorial5()  
   Dim DS as New RDS.DataSpace  
   Dim RS as ADODB.Recordset  
   Dim DC as New RDS.DataControl  
   Dim DF as Object  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "https://yourServer")  
   Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors")  
   DC.SourceRecordset = RS         ' Visual controls can now bind to DC.  
...  
```  
  
## <a name="see-also"></a>Vea también  
 [Paso 6: Los cambios se envían al servidor (Tutorial de RDS)](../../../ado/guide/remote-data-service/step-6-changes-are-sent-to-the-server-rds-tutorial.md)   
 [Tutorial de RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   

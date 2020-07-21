---
title: Establecer permisos para elementos del servidor de informes en un sitio de SharePoint | Microsoft Docs
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], SharePoint integrated mode
- SharePoint integration [Reporting Services], permissions
ms.assetid: 2467c657-a3bf-4ec3-a88c-8877df19823d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 8bdd50291a009189bf894300cdea4633fdd952f0
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/29/2020
ms.locfileid: "65570614"
---
# <a name="set-permissions-for-report-server-items-on-a-sharepoint-site"></a>Establecer permisos para elementos del servidor de informes en un sitio de SharePoint
  Si la configuración de seguridad predeterminada no proporciona el nivel de acceso necesario, puede crear nuevos niveles de permisos para proporcionar acceso a elementos u operaciones específicos del servidor de informes. La configuración de seguridad personalizada puede ser útil si desea restringir el acceso a un informe determinado.  
  
 Debe ser el propietario del sitio para crear niveles de permiso y grupos. Los niveles de permiso se usan de forma global en el sitio. Si crea un nivel de permiso nuevo, estará disponible para otros propietarios de sitios.  
  
 La mayoría de los permisos se heredan de un sitio primario. Si asigna permisos en una biblioteca o elemento específicos, anula la herencia de permisos y genera una sobrecarga adicional en el modo de administrar los permisos para dicha rama de la jerarquía de sitios.  
  
 Puede establecer permisos en archivos de definición de informe (.rdl), modelos (.smdl) y orígenes de datos compartidos (.rsds). No se pueden combinar permisos heredados y administrados en el mismo elemento. Si elige administrar permisos directamente, los permisos heredados no tendrán ningún efecto sobre el elemento actual. Si desea reanudar la herencia de permisos más adelante, puede seleccionar **Heredar permisos** en el menú **Acciones** .  
  
 Para establecer permisos en las entidades y perspectivas de un modelo, debe tener el nivel de permiso Control total para el modelo. Control total incluye "Administrar permisos", que es un permiso de nivel de sitio que se concede a los propietarios del sitio y a otros grupos de SharePoint con el nivel de permiso Control total. Si desea conceder a usuarios específicos la capacidad de establecer la seguridad de elementos de modelo, debe anular la herencia de permisos y conceder permisos elevados (como Control total) al usuario o grupo del archivo del modelo. Cuando concede el control total sobre un elemento como un archivo de una biblioteca, los permisos se centran en ese elemento y no se extienden al elemento primario ni a otros elementos de la misma biblioteca. Una vez que el usuario posee el permiso Administrar permisos para el modelo, podrá usar la seguridad de los elementos del modelo establecida a través del sitio de SharePoint o el Diseñador de modelos.  
  
### <a name="to-set-permissions-on-an-individual-report-model-or-data-source"></a>Para establecer permisos en un informe, modelo u origen de datos individual  
  
1.  Si la biblioteca no está abierta todavía, haga clic en su nombre en Inicio rápido. Si no aparece el nombre de la biblioteca, haga clic en **Ver todo el contenido del sitio**y, a continuación, haga clic en el nombre de la biblioteca.  
  
2.  Seleccione el archivo de informe, modelo de informe u origen de datos compartido.  
  
3.  Haga clic en la flecha hacia abajo y, en el menú, haga clic en **Administrar permisos**.  
  
4.  En el menú **Acciones** , haga clic en **Editar permisos**y, a continuación, haga clic en **Aceptar** para confirmar la acción.  
  
5.  Para conceder permisos a un usuario o un grupo que aún no tenga permisos para usar el archivo, haga clic en **Nuevo**y, a continuación, haga clic en **Agregar usuarios**.  
  
6.  Para quitar o modificar permisos para un usuario o grupo existente, haga clic en la casilla junto al usuario o grupo, haga clic en **Acciones**y, a continuación, haga clic en **Quitar permisos de usuario** o **Editar permisos de usuario**.  
  
### <a name="to-set-permissions-that-enable-model-item-security"></a>Para establecer permisos que habiliten la seguridad de elementos de modelo  
  
1.  Inicie sesión en el sitio de SharePoint mediante una cuenta con el permiso Administrar permisos para el sitio.  
  
2.  Abra la biblioteca que contiene el modelo.  
  
3.  Elija el modelo.  
  
4.  Haga clic en la flecha hacia abajo situada junto al modelo y seleccione **Administrar permisos**.  
  
5.  Haga clic en **Acciones**.  
  
6.  Haga clic en **Editar permisos**. Haga clic en **OK**.  
  
7.  Haga clic en **Nueva**.  
  
8.  Haga clic en **Agregar usuarios**.  
  
9. En Usuarios/Grupos, especifique la cuenta de usuario.  
  
10. Seleccione **Conceder permisos a los usuarios directamente**.  
  
11. Haga clic en **Control total**.  
  
12. Haga clic en **OK**. Una vez que el usuario pueda administrar permisos para un modelo específico, dicho usuario podrá abrir el modelo para editar los permisos de dicho modelo.  
  
## <a name="see-also"></a>Consulte también  
 [Usar la seguridad integrada de Windows SharePoint Services para los elementos del servidor de informes](../../reporting-services/security/use-built-in-security-in-windows-sharepoint-services-for-report-server-items.md)   
 [Establecimiento de permisos para las operaciones del servidor de informes en una aplicación web de SharePoint](../../reporting-services/security/set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md)   
 [Comparar roles y tareas de Reporting Services con grupos y permisos de SharePoint](../../reporting-services/security/reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)   
 [Referencia de permisos de sitio y lista de SharePoint para los elementos del servidor de informes](../../reporting-services/security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)   
 [Concesión de permisos sobre elementos del servidor de informes en un sitio de SharePoint](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
  
  

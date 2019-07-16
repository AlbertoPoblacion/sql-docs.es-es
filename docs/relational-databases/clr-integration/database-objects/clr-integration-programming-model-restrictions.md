---
title: Restricciones del modelo de programación de integración CLR | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
author: rothja
ms.author: jroth
ms.openlocfilehash: ecdc3192e0b6de26d7b829883d26cc7bbaa7e04a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68216397"
---
# <a name="clr-integration-programming-model-restrictions"></a>Restricciones del modelo de programación de la integración CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cuando se está generando un procedimiento almacenado administrado u otro objeto de base de datos administrado, hay realiza ciertas comprobaciones de código [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que deben tenerse en cuenta. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] realiza comprobaciones en el ensamblado de código administrado cuando se registra primero en la base de datos mediante el **CREATE ASSEMBLY** instrucción y también en tiempo de ejecución. El código administrado también se comprueba en tiempo de ejecución porque en un ensamblado puede haber rutas de acceso al código que nunca se hayan alcanzado realmente en tiempo de ejecución.  Esto proporciona flexibilidad para registrar ensamblados de terceros, de manera especial, de forma que no se debe bloquear un ensamblado donde haya un código 'no seguro' diseñado para que se ejecute en un entorno cliente pero nunca se ejecutaría en el CLR hospedado. Los requisitos que el código administrado debe cumplir dependen de si el ensamblado se registra como **seguro**, **EXTERNAL_ACCESS**, o **UNSAFE**, **SAFE** que se va las más estrictas y, a continuación se enumeran.  
  
 Además de las restricciones que se ubican en los ensamblados de código administrado, también hay permisos de seguridad de código que se conceden. Common Language Runtime (CLR) admite un modelo de seguridad denominado seguridad de acceso del código (CAS) para el código administrado. En este modelo, se conceden permisos a los ensamblados basados en la identidad del código. **SEGURO**, **EXTERNAL_ACCESS**, y **UNSAFE** ensamblados tienen permisos de CAS diferentes. Para obtener más información, consulte [CLR Integration Code Access Security](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md).  
  
## <a name="create-assembly-checks"></a>Comprobaciones de CREATE ASSEMBLY  
 Cuando el **CREATE ASSEMBLY** se ejecuta la instrucción, se realizan las comprobaciones siguientes para cada nivel de seguridad.  Si falla, cualquier comprobación **CREATE ASSEMBLY** se producirá un error con un mensaje de error.  
  
### <a name="global-any-security-level"></a>Global (cualquier nivel de seguridad)  
 Todos los ensamblados a los que se hace referencia deben cumplir uno o más de los criterios siguientes:  
  
-   El ensamblado ya está registrado en la base de datos.  
  
-   El ensamblado es uno de los ensamblados compatibles. Para obtener más información, consulte [admite bibliotecas de .NET Framework](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
-   Usa **crear ENSAMBLADOS de** _\<ubicación >,_ y están disponibles en todos los ensamblados que se hace referencia y sus dependencias *\<ubicación >* .  
  
-   Usa **crear ENSAMBLADOS de** _\<bytes... >,_ y todas las referencias se especifican a través de espacio separados por bytes.  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 Todos los **EXTERNAL_ACCESS** ensamblados deben cumplir los siguientes criterios:  
  
-   Los campos estáticos no se usan para almacenar información. Se permiten los campos estáticos de solo lectura.  
  
-   Se pasa la prueba PEVerify. La herramienta PEVerify (peverify.exe), que comprueba que el código MSIL y los metadatos asociados cumplen los requisitos de seguridad de tipos, se proporciona con .NET Framework SDK.  
  
-   Sincronización, por ejemplo con el **SynchronizationAttribute** de clases, no se utiliza.  
  
-   No se usan métodos de finalizador.  
  
 Los siguientes atributos personalizados no están permitidos en **EXTERNAL_ACCESS** ensamblados:  
  
-   System.ContextStaticAttribute  
  
-   System.MTAThreadAttribute  
  
-   System.Runtime.CompilerServices.MethodImplAttribute  
  
-   System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
  
-   System.Runtime.Remoting.Contexts.ContextAttribute  
  
-   System.Runtime.Remoting.Contexts.SynchronizationAttribute  
  
-   System.Runtime.InteropServices.DllImportAttribute  
  
-   System.Security.Permissions.CodeAccessSecurityAttribute  
  
-   System.Security.SuppressUnmanagedCodeSecurityAttribute  
  
-   System.Security.UnverifiableCodeAttribute  
  
-   System.STAThreadAttribute  
  
-   System.ThreadStaticAttribute  
  
### <a name="safe"></a>SAFE  
  
-   Todos los **EXTERNAL_ACCESS** se comprueban las condiciones del ensamblado.  
  
## <a name="runtime-checks"></a>Comprobaciones en tiempo de ejecución  
 En tiempo de ejecución, el ensamblado de código se comprueba para las condiciones siguientes. Si se encuentra cualquiera de estas condiciones, el código administrado no se puede ejecutar y se iniciará una excepción.  
  
### <a name="unsafe"></a>UNSAFE  
 Cargar un ensamblado, ya sea explícitamente mediante una llamada a la **System.Reflection.Assembly.Load()** método desde una matriz de bytes o implícitamente mediante el uso de **Reflection.Emit** espacio de nombres: no se permite.  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 Todos los **UNSAFE** se comprueban las condiciones.  
  
 Todos los tipos y métodos anotados con los siguientes valores de atributo de protección de host (HPA) en la lista compatible de ensamblados no están admitidos.  
  
-   SelfAffectingProcessMgmt  
  
-   SelfAffectingThreading  
  
-   Sincronización  
  
-   SharedState  
  
-   ExternalProcessMgmt  
  
-   ExternalThreading  
  
-   SecurityInfrastructure  
  
-   MayLeakOnAbort  
  
-   UI  
  
 Para obtener más información acerca de los HPA y una lista de tipos no permitidos y los miembros de los ensamblados compatibles, consulte [atributos de protección de Host y programación de integración de CLR](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md).  
  
### <a name="safe"></a>SAFE  
 Todos los **EXTERNAL_ACCESS** se comprueban las condiciones.  
  
## <a name="see-also"></a>Vea también  
 [Bibliotecas compatibles de .NET Framework](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)   
 [Seguridad de acceso del código de integración de CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Atributos de protección de host y programación de la integración CLR](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Crear un ensamblado](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  

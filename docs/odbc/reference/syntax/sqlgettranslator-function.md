---
title: Función SQLGetTranslator | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetTranslator
helpviewer_keywords:
- SQLGetTranslator function [ODBC]
ms.assetid: 33879db3-5ef9-4585-9be5-69376157e017
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 948fc36da520777812c02e6e5d52a423eb9cc288
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65536547"
---
# <a name="sqlgettranslator-function"></a>Función SQLGetTranslator
**Conformidad**  
 Versión de introducción: ODBC 2.0  
  
 **Resumen**  
 **SQLGetTranslator** muestra un cuadro de diálogo desde el que un usuario puede seleccionar un traductor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
  
BOOL SQLGetTranslator(  
     HWND      hwndParent,  
     LPSTR     lpszName,  
     WORD      cbNameMax,  
     WORD *    pcbNameOut,  
     LPSTR     lpszPath,  
     WORD      cbPathMax,  
     WORD *    pcbPathOut,  
     DWORD *   pvOption);  
```  
  
## <a name="arguments"></a>Argumentos  
 *hwndParent*  
 [Entrada] Identificador de la ventana primaria.  
  
 *lpszName*  
 [Entrada/salida] Nombre del traductor de la información del sistema.  
  
 *cbNameMax*  
 [Entrada] Longitud máxima de la *lpszName* búfer.  
  
 *pcbNameOut*  
 [Entrada/salida] Número total de bytes (sin incluir los bytes de terminación null) pasa o se devuelve en *lpszName*. Si el número de bytes disponible para devolver es mayor o igual a *cbNameMax*, el nombre del traductor en *lpszName* se trunca a *cbNameMax* menos el carácter de terminación NULL. El *pcbNameOut* argumento puede ser un puntero nulo.  
  
 *lpszPath*  
 [Salida] Ruta de acceso completa de la DLL de traducción.  
  
 *cbPathMax*  
 [Entrada] Longitud máxima de la *lpszPath* búfer.  
  
 *pcbPathOut*  
 [Salida] Número total de bytes (sin incluir los bytes de terminación null) devuelven en *lpszPath*. Si el número de bytes disponible para devolver es mayor o igual a *cbPathMax*, la ruta de acceso del archivo DLL de traducción en *lpszPath* se trunca a *cbPathMax* menos el carácter de terminación NULL. El *pcbPathOut* argumento puede ser un puntero nulo.  
  
 *pvOption*  
 Opción de traducción de 32 bits de [salida].  
  
## <a name="returns"></a>Devuelve  
 La función devuelve TRUE si es correcta y FALSE si se produce un error o si el usuario cancela el cuadro de diálogo.  
  
## <a name="diagnostics"></a>Diagnósticos  
 Cuando **SQLGetTranslator** devuelve FALSE, un asociado  *\*pfErrorCode* valor puede obtenerse mediante una llamada a **SQLInstallerError**. La siguiente tabla se enumeran los  *\*pfErrorCode* valores que pueden devolver **SQLInstallerError** y se explica cada uno de ellos en el contexto de esta función.  
  
|*\*pfErrorCode*|Error|Descripción|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Error del instalador general|Se produjo un error para que se ha producido ningún error de instalación concreto.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Longitud de búfer no válido|El *cbNameMax* o *cbPathMax* argumento era menor o igual que 0.|  
|ODBC_ERROR_INVALID_HWND|Identificador de ventana no válida|El *hwndParent* argumento era NULL o no válido.|  
|ODBC_ERROR_INVALID_NAME|Nombre de controlador o traductor no válido|El *lpszName* argumento no era válido. No se encontró en el registro.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|No se pudo cargar la biblioteca de instalación de traductor o controlador|No se pudo cargar la biblioteca de traductor.|  
|ODBC_ERROR_INVALID_OPTION|Opción de transacción no válido|El *pvOption* argumento contiene un valor no válido.|  
|ODBC_ERROR_OUT_OF_MEM|No hay memoria suficiente|El programa de instalación no pudo realizar la función debido a la falta de memoria.|  
  
## <a name="comments"></a>Comentarios  
 Si *hwndParent* es null o si *lpszName*, *lpszPath*, o *pvOption* es un puntero nulo, **SQLGetTranslator** devuelve FALSE. En caso contrario, muestra la lista de traductores instalados en el cuadro de diálogo siguiente.  
  
 ![Cuadro de diálogo Seleccionar traductor](../../../odbc/reference/syntax/media/ch23j.gif "CH23J")  
  
 Si *lpszName* contiene un nombre válido de traductor, está seleccionada. En caso contrario, \<ningún convertidor > está seleccionado.  
  
 Si el usuario elige \<ningún convertidor >, el contenido de *lpszName*, *lpszPath*, y *pvOption* no se han tocado. **SQLGetTranslator** establece *pcbNameOut* y *pcbPathOut* a 0 y devuelve TRUE.  
  
 Si el usuario elige un traductor, **SQLGetTranslator** llamadas **ConfigTranslator** en el archivo DLL de configuración del traductor. Si **ConfigTranslator** devuelve FALSE, **SQLGetTranslator** vuelve a su cuadro de diálogo. Si **ConfigTranslator** devuelve TRUE, **SQLGetTranslator** devuelve TRUE, junto con la opción de nombre, la ruta de acceso y la traducción de traductor seleccionado.  
  
## <a name="related-functions"></a>Funciones relacionadas  
  
|Para obtener información acerca de|Vea|  
|---------------------------|---------|  
|Configuración de un traductor|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|  
|Obtención de un atributo de traducción|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Establecer un atributo de traducción|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|

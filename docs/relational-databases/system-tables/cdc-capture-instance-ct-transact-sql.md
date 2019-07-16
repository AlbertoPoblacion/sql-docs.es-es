---
title: CDC. &lt;capture_instance&gt;_CT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc
- cdc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.<capture_instance>_CT
ms.assetid: 979c8110-3c54-4e76-953c-777194bc9751
author: stevestein
ms.author: sstein
ms.openlocfilehash: e4ad2d32c313919ed4446a5506f22e9048e09288
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119310"
---
# <a name="cdcltcaptureinstancegtct-transact-sql"></a>CDC. &lt;capture_instance&gt;_CT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Es la tabla de cambio creada cuando la captura de datos de cambio se habilita en una tabla de origen. La tabla devuelve una fila para cada inserción y elimina la operación realizada contra la tabla de origen y dos filas para cada operación de actualización realizada contra la tabla de origen. Cuando el nombre de la tabla de cambio no se especifica en el momento que se habilita la tabla de origen, el nombre se deriva. El formato del nombre es cdc. *capture_instance*_CT donde *capture_instance* es el nombre del esquema de la tabla de origen y el nombre de tabla de origen en el formato *tabla_esquema*. Por ejemplo, si la tabla **Person.Address** en el **AdventureWorks** base de datos de ejemplo está habilitada para la captura de datos modificados, el nombre de tabla del cambio derivado sería **cdc. Person_Address_CT**.  
  
 Se recomienda **no consultar directamente las tablas del sistema**. En su lugar, ejecute el [cdc.fn_cdc_get_all_changes_ < capture_instance >](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md) y [cdc.fn_cdc_get_net_changes_ < capture_instance >](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md) funciones.  
  

  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**__$start_lsn**|**binary(10)**|Número de flujo de registro (LSN) asociado con la transacción de confirmación para el cambio.<br /><br /> Todos los cambios confirmados en la misma transacción comparten el mismo LSN de confirmación. Por ejemplo, si una operación de eliminación en la tabla de origen quita dos filas, la tabla de cambios contendrá dos filas, cada una con el mismo **__ $start_lsn** valor.|  
|**__$end_lsn**|**binary(10)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> En [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], esta columna siempre es NULL.|  
|**__$seqval**|**binary(10)**|Valor de secuencia utilizado para ordenar los cambios de fila dentro de una transacción.|  
|**__$operation**|**int**|Identifica la operación del lenguaje de manipulación de datos (DML) asociada con el cambio. Puede ser uno de los valores siguientes:<br /><br /> 1 = eliminar<br /><br /> 2 = insertar<br /><br /> 3 = actualizar (valores anteriores)<br /><br /> Los datos de columna tienen valores de fila antes de ejecutar la instrucción de actualización.<br /><br /> 4 = actualizar (valores nuevos)<br /><br /> Los datos de columna tienen valores de fila después de ejecutar la instrucción de actualización.|  
|**__$update_mask**|**varbinary(128)**|Máscara de bits basada en los índices de columna de la tabla de cambios que identifica las columnas que cambiaron.|  
|*\<columnas de la tabla de origen capturadas>*|varía|Las columnas restantes de la tabla de cambios son las columnas de la tabla de origen que se identificaron como columnas capturadas cuando se creó la instancia de captura. Si no se especificó ninguna columna en la lista de columnas capturadas, todas las columnas en la tabla de origen se incluyen en esta tabla.|  
|**__$command_id** |**int** |Realiza un seguimiento del orden de las operaciones dentro de una transacción. |  
  
## <a name="remarks"></a>Comentarios  

La `__$command_id` columna era la columna se introdujo en una actualización acumulativa en las versiones 2012 y 2016. Para obtener información de versión y descarga, consulte el artículo KB 3030352 en [corregir: La tabla de cambios está ordenada incorrectamente para actualizar filas después de habilitar el cambio de datos de captura para una base de datos de Microsoft SQL Server](https://support.microsoft.com/help/3030352/fix-the-change-table-is-ordered-incorrectly-for-updated-rows-after-you).  Para obtener más información, consulte [puede romper la funcionalidad de CDC después de actualizar a la CU más reciente para SQL Server 2012, 2014 y 2016](https://blogs.msdn.microsoft.com/sql_server_team/cdc-functionality-may-break-after-upgrading-to-the-latest-cu-for-sql-server-2012-2014-and-2016/).

## <a name="captured-column-data-types"></a>Tipos de datos de columna capturados  
 Las columnas capturadas incluidas en esta tabla tienen el mismo valor y tipo de datos que sus columnas de origen correspondientes con las excepciones siguientes:  
  
-   **Marca de tiempo** columnas se definen como **binary (8)** .  
  
-   **Identidad** columnas se definen como **int** o **bigint**.  
  
 Sin embargo, los valores de estas columnas son iguales que los valores de las columnas de origen.  
  
### <a name="large-object-data-types"></a>Tipos de datos de objetos grandes  
 Las columnas de tipo de datos **imagen**, **texto**, y **ntext** siempre se les asigna un **NULL** valor cuando __ $operation = 1 o \_ \_$operation = 3. Las columnas de tipo de datos **varbinary (max)** , **varchar (max)** , o **nvarchar (max)** se asignan una **NULL** valor cuando \_ \_$operation = 3, a menos que la columna cambie durante la actualización. Cuando \_ \_$operation = 1, estas columnas se les asigna su valor en el momento de la eliminación. Las columnas calculadas que están incluidas en una instancia de captura siempre tienen un valor de **NULL**.  
  
 De forma predeterminada, el tamaño máximo que se pueden agregar a una columna capturada en una sola instrucción INSERT, UPDATE, WRITETEXT o UPDATETEXT es 65.536 bytes o 64 KB. Para aumentar este tamaño para admitir datos LOB más grandes, use el [establecer el tamaño de replicación de texto máximo Server Configuration Option](../../database-engine/configure-windows/configure-the-max-text-repl-size-server-configuration-option.md) para especificar un tamaño máximo mayor. Para más información, consulte [Establecer la opción de configuración del servidor Tamaño de replicación de texto máximo](../../database-engine/configure-windows/configure-the-max-text-repl-size-server-configuration-option.md).  
  
## <a name="data-definition-language-modifications"></a>Modificaciones del lenguaje de definición de datos  
 Las modificaciones de DDL en la tabla de origen, como agregar o quitar columnas, se registran en el [cdc.ddl_history](../../relational-databases/system-tables/cdc-ddl-history-transact-sql.md) tabla. Estos cambios no se aplican a la tabla de cambio. Es decir, la definición de la tabla de cambio se mantiene constante. Al insertar las filas en la tabla de cambio, el proceso de captura omite esas columnas que no aparecen en la lista de columnas capturadas asociadas con la tabla de origen. Si en la lista de columnas capturadas aparece una columna que ya no se encuentra en la tabla de origen, se asignará un valor nulo a la columna.  
  
 Cambiar el tipo de datos de una columna en la tabla de origen también se registra en el [cdc.ddl_history](../../relational-databases/system-tables/cdc-ddl-history-transact-sql.md) tabla. Sin embargo, este cambio altera la definición de la tabla de cambio. El tipo de datos de la columna capturada en la tabla de cambio se modifica cuando el proceso de captura detecta la entrada de registro para el cambio DDL realizado en la tabla de origen.  
  
 Si debe modificar el tipo de datos de una columna capturada en la tabla de origen de tal modo que disminuye el tamaño del tipo de datos, utilice el procedimiento siguiente para asegurarse de que puede modificar correctamente la columna equivalente en la tabla de cambio.  
  
1.  En la tabla de origen, actualice los valores en la columna que se va a modificar para ajustar al tamaño del tipo de datos planeado. Por ejemplo, si cambia el tipo de datos de **int** a **smallint**, actualice los valores con un tamaño que se ajuste en el **smallint** oscilar entre-32.768 y 32.767.  
  
2.  En la tabla de cambio, realice la misma operación de actualización en la columna equivalente.  
  
3.  Altere la tabla de origen especificando el nuevo tipo de datos. El cambio del tipo de datos se propaga correctamente a la tabla de cambio.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="data-manipulation-language-modifications"></a>Modificaciones del lenguaje de manipulación de datos  
 Cuando las operaciones de inserción, actualización y eliminación se realizan en una tabla de origen habilitada para la captura de datos modificados, un registro de esas operaciones DML aparece en el registro de transacciones de la base de datos. El proceso de captura de datos modificados recupera información sobre los cambios del registro de transacciones y agrega una o dos filas en la tabla de cambios para registrar el cambio. Las entradas se agregan a la tabla de cambios en el mismo orden en que se confirmaron en la tabla de origen, aunque la confirmación de las entradas de la tabla de cambios se debe realizar normalmente en un grupo de cambios en lugar de para una sola entrada.  
  
 Dentro de la entrada de tabla de cambio, el **__ $start_lsn** columna se usa para registrar el LSN de confirmación que está asociado con el cambio en la tabla de origen y el **columna de __ $seqval** se usa para ordenar el cambio dentro de su transacción. Juntas, estas columnas de metadatos se pueden utilizar para asegurarse de que el orden de confirmación de los cambios de origen se conserva. Dado que el proceso de captura obtiene la información de los cambios en el registro de transacciones, es importante tener en cuenta que las entradas de la tabla de cambios no aparecen sincrónicamente con los cambios correspondientes de la tabla de origen. Por el contrario, los cambios correspondientes aparecen de forma asincrónica, después de que el proceso de captura haya procesado las entradas de cambios pertinentes del registro de transacciones.  
  
 Para operaciones de inserción y eliminación, todos los bits de la máscara de actualización están activados. Para las operaciones de actualización, la máscara de actualización tanto en las filas de actualización antiguas como nuevas se modificará para reflejar las columnas que cambiaron durante la actualización.  
  
## <a name="see-also"></a>Vea también  
 [sys.sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [sys.sp_cdc_get_ddl_history &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql.md)  
  
  

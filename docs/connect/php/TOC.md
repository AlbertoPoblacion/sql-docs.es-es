
# [Controladores de Microsoft para PHP para SQL Server](microsoft-php-driver-for-sql-server.md)

# [Introducción](getting-started-with-the-php-sql-driver.md)
## [Paso 1: configurar el entorno de desarrollo para el desarrollo de PHP](step-1-configure-development-environment-for-php-development.md)
## [Paso 2: crear una instancia de SQL Database para el desarrollo de PHP](step-2-create-a-sql-database-for-php-development.md)
## [Paso 3: prueba de concepto de la conexión a SQL con PHP](step-3-proof-of-concept-connecting-to-sql-using-php.md)
## [Paso 4: conectarse con resistencia a SQL con PHP](step-4-connect-resiliently-to-sql-with-php.md)

# [Información general](overview-of-the-php-sql-driver.md)
## [Requisitos del sistema](system-requirements-for-the-php-sql-driver.md)
## [Carga del controlador](loading-the-php-sql-driver.md)
## [Configuración de IIS](configuring-iis-for-php-sql-driver.md)
## [Tutorial de instalación de controladores de PHP en Linux y Mac](installation-tutorial-linux-mac.md)
## [Notas de la versión](release-notes-for-the-php-sql-driver.md)
## [Recursos de soporte técnico](support-resources-for-the-php-sql-driver.md)
## [Sobre los ejemplos de código](about-code-examples-in-the-documentation.md)

# [Guía de programación](programming-guide-for-php-sql-driver.md)
## [Conexión al servidor](connecting-to-the-server.md)
### [Conexión mediante la autenticación de Windows](how-to-connect-using-windows-authentication.md)
### [Conexión mediante la autenticación de SQL Server](how-to-connect-using-sql-server-authentication.md)
### [Conexión con la autenticación de Azure Active Directory](azure-active-directory.md)
### [Conexión a un puerto específico](how-to-connect-on-a-specified-port.md)
### [Agrupación de conexiones](connection-pooling-microsoft-drivers-for-php-for-sql-server.md)
### [Deshabilitar los conjuntos de resultados activos múltiples (MARS)](how-to-disable-multiple-active-resultsets-mars.md)
### [Opciones de conexión](connection-options.md)
### [Controlador PHP para el soporte de SQL Server para LocalDB](php-driver-for-sql-server-support-for-localdb.md)
### [Controlador PHP para el soporte de SQL Server para la alta disponibilidad con recuperación ante desastres](php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)
### [Conexión a Microsoft Azure SQL Database](connecting-to-microsoft-azure-sql-database.md)
### [Resistencia de conexión](connection-resiliency.md)
## [Comparación de las funciones de ejecución](comparing-execution-functions.md)
## [Ejecución de la instrucción preparada y directa en el controlador PDO_SQLSRV](direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md)
## [Recuperación de datos](retrieving-data.md)
### [Recuperación de datos como una secuencia con el controlador SQLSRV](retrieving-data-as-a-stream-using-the-sqlsrv-driver.md)
#### [Tipos de datos con compatibilidad con secuencias con el controlador SQLSRV](data-types-with-stream-support-using-the-sqlsrv-driver.md)
#### [Recuperación de datos de caracteres como una secuencia utilizando el controlador SQLSRV](how-to-retrieve-character-data-as-a-stream-using-the-sqlsrv-driver.md)
#### [Recuperación de datos binarios como una secuencia mediante el controlador SQLSRV](how-to-retrieve-binary-data-as-a-stream-using-the-sqlsrv-driver.md)
### [Uso de parámetros direccionales](using-directional-parameters.md)
#### [Especificación de la dirección del parámetro con el controlador SQLSRV](how-to-specify-parameter-direction-using-the-sqlsrv-driver.md)
#### [Recuperación de parámetros de salida con el controlador SQLSRV](how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)
#### [Recuperación de parámetros de entrada y salida con el controlador SQLSRV](how-to-retrieve-input-and-output-parameters-using-the-sqlsrv-driver.md)
### [Especificación de un tipo de cursor y selección de filas](specifying-a-cursor-type-and-selecting-rows.md)
#### [Tipos de cursor (controlador SQLSRV)](cursor-types-sqlsrv-driver.md)
#### [Tipos de cursor (controlador PDO_SQLSRV)](cursor-types-pdo-sqlsrv-driver.md)
### [Recuperación del tipo de fecha y hora como cadenas con el controlador SQLSRV](how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md)
## [Actualización de datos](updating-data-microsoft-drivers-for-php-for-sql-server.md)
### [Realización de consultas con parámetros](how-to-perform-parameterized-queries.md)
### [Envío de datos como una secuencia](how-to-send-data-as-a-stream.md)
### [Realización de transacciones](how-to-perform-transactions.md)
## [Conversión de tipos de datos](converting-data-types.md)
### [Tipos de datos de SQL Server predeterminados](default-sql-server-data-types.md)
### [Tipos de datos PHP predeterminados](default-php-data-types.md)
### [Especificación de tipos de datos de SQL Server cuando se utiliza el controlador SQLSRV](how-to-specify-sql-server-data-types-when-using-the-sqlsrv-driver.md)
### [Especificación de tipos de datos PHP](how-to-specify-php-data-types.md)
### [Envío y recuperación de datos UTF-8 gracias a la compatibilidad integrada con UTF-8](how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md)
### [Envío y recuperación de datos ASCII en Linux y Mac OS](how-to-send-and-retrieve-ascii-data-in-linux-mac.md)
## [Control de errores y advertencias](handling-errors-and-warnings.md)
### [Configuración del control de errores y advertencias con el controlador SQLSRV](how-to-configure-error-and-warning-handling-using-the-sqlsrv-driver.md)
### [Control de errores y advertencias con el controlador SQLSRV](how-to-handle-errors-and-warnings-using-the-sqlsrv-driver.md)
## [Actividad de registro](logging-activity.md)
## [Constantes (controladores de Microsoft para PHP para SQL Server)](constants-microsoft-drivers-for-php-for-sql-server.md)
## [Referencia de API del controlador SQLSRV](sqlsrv-driver-api-reference.md)
### [sqlsrv_begin_transaction](sqlsrv-begin-transaction.md)
### [sqlsrv_cancel](sqlsrv-cancel.md)
### [sqlsrv_client_info](sqlsrv-client-info.md)
### [sqlsrv_close](sqlsrv-close.md)
### [sqlsrv_commit](sqlsrv-commit.md)
### [sqlsrv_configure](sqlsrv-configure.md)
### [sqlsrv_connect](sqlsrv-connect.md)
### [sqlsrv_errors](sqlsrv-errors.md)
### [sqlsrv_execute](sqlsrv-execute.md)
### [sqlsrv_fetch](sqlsrv-fetch.md)
### [sqlsrv_fetch_array](sqlsrv-fetch-array.md)
### [sqlsrv_fetch_object](sqlsrv-fetch-object.md)
### [sqlsrv_field_metadata](sqlsrv-field-metadata.md)
### [sqlsrv_free_stmt](sqlsrv-free-stmt.md)
### [sqlsrv_get_config](sqlsrv-get-config.md)
### [sqlsrv_get_field](sqlsrv-get-field.md)
### [sqlsrv_has_rows](sqlsrv-has-rows.md)
### [sqlsrv_next_result](sqlsrv-next-result.md)
### [sqlsrv_num_fields](sqlsrv-num-fields.md)
### [sqlsrv_num_rows](sqlsrv-num-rows.md)
### [sqlsrv_prepare](sqlsrv-prepare.md)
### [sqlsrv_query](sqlsrv-query.md)
### [sqlsrv_rollback](sqlsrv-rollback.md)
### [sqlsrv_rows_affected](sqlsrv-rows-affected.md)
### [sqlsrv_send_stream_data](sqlsrv-send-stream-data.md)
### [sqlsrv_server_info](sqlsrv-server-info.md)
## [Referencia del controlador PDO_SQLSRV](pdo-sqlsrv-driver-reference.md)
### [Clase PDO](pdo-class.md)
#### [PDO::__construct](pdo-construct.md)
#### [PDO::beginTransaction](pdo-begintransaction.md)
#### [PDO::commit](pdo-commit.md)
#### [PDO::errorCode](pdo-errorcode.md)
#### [PDO::errorInfo](pdo-errorinfo.md)
#### [PDO::exec](pdo-exec.md)
#### [PDO::getAttribute](pdo-getattribute.md)
#### [PDO::getAvailableDrivers](pdo-getavailabledrivers.md)
#### [PDO::lastInsertId](pdo-lastinsertid.md)
#### [PDO::prepare](pdo-prepare.md)
#### [PDO::query](pdo-query.md)
#### [PDO::quote](pdo-quote.md)
#### [PDO::rollback](pdo-rollback.md)
#### [PDO::setAttribute](pdo-setattribute.md)
### [Clase PDOStatement](pdostatement-class.md)
#### [PDOStatement::bindColumn](pdostatement-bindcolumn.md)
#### [PDOStatement::bindParam](pdostatement-bindparam.md)
#### [PDOStatement::bindValue](pdostatement-bindvalue.md)
#### [PDOStatement::closeCursor](pdostatement-closecursor.md)
#### [PDOStatement::columnCount](pdostatement-columncount.md)
#### [PDOStatement::debugDumpParams](pdostatement-debugdumpparams.md)
#### [PDOStatement::errorCode](pdostatement-errorcode.md)
#### [PDOStatement::errorInfo](pdostatement-errorinfo.md)
#### [PDOStatement::execute](pdostatement-execute.md)
#### [PDOStatement::fetch](pdostatement-fetch.md)
#### [PDOStatement::fetchAll](pdostatement-fetchall.md)
#### [PDOStatement::fetchColumn](pdostatement-fetchcolumn.md)
#### [PDOStatement::fetchObject](pdostatement-fetchobject.md)
#### [PDOStatement::getAttribute](pdostatement-getattribute.md)
#### [PDOStatement::getColumnMeta](pdostatement-getcolumnmeta.md)
#### [PDOStatement::nextRowset](pdostatement-nextrowset.md)
#### [PDOStatement::rowCount](pdostatement-rowcount.md)
#### [PDOStatement::setAttribute](pdostatement-setattribute.md)
#### [PDOStatement::setFetchMode](pdostatement-setfetchmode.md)

# [Consideraciones de seguridad](security-considerations-for-php-sql-driver.md)

# [Ejemplos de código](code-samples-for-php-sql-driver.md)
## [Aplicación de ejemplo (controlador PDO_SQLSRV)](example-application-pdo-sqlsrv-driver.md)
## [Aplicación de ejemplo (controlador SQLSRV)](example-application-sqlsrv-driver.md)

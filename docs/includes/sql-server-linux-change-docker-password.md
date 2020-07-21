La cuenta **SA** es un administrador del sistema en la instancia de SQL Server que se crea durante la instalación. Después de crear el contenedor de SQL Server, la variable de entorno `MSSQL_SA_PASSWORD` especificada se reconoce mediante la ejecución de `echo $MSSQL_SA_PASSWORD` en el contenedor. Por motivos de seguridad, cambie la contraseña de administrador del sistema:

1. Elija una contraseña segura que se usará para el usuario SA.

1. Use `docker exec` para ejecutar la utilidad **sqlcmd** a fin de cambiar la contraseña a través de una instrucción Transact-SQL. Reemplace `<YourStrong!Passw0rd>` y `<YourNewStrong!Passw0rd>` con valores de contraseña propios:

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourStrong!Passw0rd>' \
      -Q 'ALTER LOGIN SA WITH PASSWORD="<YourNewStrong!Passw0rd>"'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourStrong!Passw0rd>" `
      -Q "ALTER LOGIN SA WITH PASSWORD='<YourNewStrong!Passw0rd>'"
   ```

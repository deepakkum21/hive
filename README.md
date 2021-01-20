# HIVE

## HIVE COMMANDS:-

1. `hive --service cli/beeline --database dbname`
   - starts hive with beeline or cli service default is cli, also if --database mentioned uses that db
2. `hive -e "SET;" > hive.properties`
   - to copy all the property which are present for the hive
3. `SET propertyName`
   - to see the value of the property
4. `SET propertyName = value`
   - to set the new value for the property
5. `ls -al | grep history`
   - to see the histrory cmds. go to home using `cd`
6. `dfs -ls filelocation`
   - to the files using dfs in hive cli
7. `hdfs -ls /app/hive/warehouse`
   - /app/hive/warehouse is the the loaction where all the databases are created.
   - hive.metastore.warehouse.dir is the property where the location value is stored.
8. `CREATE DATABASE IF NOT EXISTS dbName`
   - to create a db with dbName
9. `USE dbName`
   - to switch to the particular db
10. `SHOW CREATE TABLE tableName`
    - it shows the create table cmd used to create the table
11. `DESCRIBE FORMATTED tableName`
    - gives metadata about the table
    - **metadata are stored etastore whcih are RDBMS db like mysql, oracle**
12. `

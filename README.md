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
12. `LOAD DATA LOCAL INPATH 'pathof the file' INTO TABLE tableName;`
    - loads the local file data into the table
    - by default it will append if already data is present- it will throw error if the file format of table and file is different
    - eg, if source file is in txt,csv etc and table is having `store format` as orc then it will throw error to avoid this use stage table technique.
    - loading table from hdfs moves the file so it is much faster as compared to loading from local
13. `LOAD DATA LOCAL INPATH 'pathof the file' OVERWRITE INTO TABLE tableName;`
    - overwrite the data into the table
14. `CREATE EXTERNAL TABLE tableName(col....)`
    - creates a external table
    - `external vs managed table` if external table is droped the metadata from metastore is deleted not the the data in the hdfs location is deleted but in managed table it is deleted from the hdfs location also.
15. `TRUNCATE TABLE tableName`
    - deletes the data from the table
    - only applicable in managed table not in external table
16. `DROP TABLE tableName`
    - deletes the table but in case of external table only metadata from metastore is deleted and not the dtat from hdfs location
17. `PARTITION BY (colName dataType)`
    - the colName should be different from the col defined as regular one at create table
    - will give error if tried to load directly into the table as their will be missmatch of col (partition col might not there)
    - `static partition`
      - in this manually have to create partition usig `alter`
      - `ALTER TABLE tableName ADD PARTITION(partitionColName=value) PARTITION(partitionColName=value2);`
      - the above cmd will create 2 partition dir in the dfs location that can be seen using dfs -ls location.

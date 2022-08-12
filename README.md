# SQOOP

SQOOP runs MAPRED JOB under the hood

SQOOP IMPORT doesnt happen via CLI but its a server to server copy

You can use --options to specify a particular config file.txt

Max No. of parallel mappers are 4. Use 2 or 3 mappers optimally so that it does not affect the performance of the relational db as a overhead.

When primary key is present SQQOP will automatically detect and maps the part of data to the no of mappers tasks defined.

If primary key is unevenly spread, then use a column that u identify as a split by column.

SQOOP can copy data into a HIVE TABLE using --hive import. SQQOP needs Hive to be configured.

SQOOP runs a local HIVE client in its own server in order to invoke the commands CREATE TABLE for the structure in HIVE METASTORE and LOAD DATA INPATH to move the data into HIVE WAREHOUSE.

If you dont explicitly specify the -HIVE TABLE name then the source table name is assigned to the HIVE TABLE

Use --hive-home to speicfy the HIVE binary in case of multiple HIVE instances.

SQOOP incremental LOAD parameters: --check-column --incremental (-append (Prim key or any column in which the max value for the last import i checked) / 
-lastmodified (a column in the source table should be a datetime. even if an exisiting record is updated this column can be checked with column name and check value params) ) --checkvalue

--hive-overwrite will overwrite the existing table. used in ELT activity.

ETL, ELT, Data transformation processing, HDFS as Data Lake, Data Analysis, Reporting, Business Insights

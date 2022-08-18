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

SQOOP incremental LOAD parameters: --check-column --incremental (append / lastmodified) --last-value

-append (Prim key or any column in which the max value for the last import i checked) 

-lastmodified (a column in the source table should be a datetime. even if an exisiting record is updated this column can be checked with column name and check value params) ) 

sqoop --create job job1 -- import jdbc -u -p  -table tbl1 --check-column 'id' --incremental (append / lastmodified) --last-value 5 will create the job

You need to execute --sqoop -exec (job_name) to run the job. Everytime job runs , the last_value is updated automatically by SQOOP, unless you want to particularly specify the --last-value param.

SQOOP internally stores the -last value updated value in the local metastore of the server where it runs. This can be checked by issuing -grep command with --incremental param

--hive-overwrite will overwrite the existing table. used in ELT activity.

SQQOP export will have export-dir as the HDFS path

SQOOP export will not guarantee ATOMICITY. 100 INSERT or UPDATE statements will do a commit. So while in the 100 inserts u may see partial data.

SQOOP export will export with multiple threads.

SQQOP export with and --update key parameter will generate  UPDATE SET with WHERE clause filter and update the record in the destination relational table.

ETL, ELT, Data transformation processing, HDFS as Data Lake, Data Analysis, Reporting, Business Insights

Diff b/w SQOOP and SQOOP2 is that SQOOP was just a client and SQOOP2 has a middle layer SQOOP Server to interact with EDW, Doc based sys and RDBMS

You can have the connector string and credentials in a separate --options-file ".txt"
sqoop import --options-file="~/creds.txt" --connect jdbc:mysql//dbserver.com/live --table orders

sqoop import --options-file="~/creds-and-connec.txt" --table orders --check-column=id --incremental append --last-value 17092

sqoop import --options-file="~/creds-and-connec.txt" --table orders --query 'select EMP_NO, NAME from employees where SAL > 100000'

sqoop export --options-file="~/creds-and-connec.txt" --EXPORT-DIR /USER/HIVE/WAREHOUSE/RECOM-UPDATES --table recom

sqoop import list tables --options-file="~/creds.txt" --connect jdbc:mysql//dbserver.com/live

EVAL before running(prints op to console for previewing queries)
sqoop eval --options-file="~/creds-and-connec.txt -e "SELECT * FROM emp lIMIT 50"





# SQOOP

SQOOP runs MAPRED JOB under the hood

SQOOP IMPORT doesnt happen via CLI but its a server to server copy

You can use --options to specify a particular config file.txt

Max No. of parallel mappers are 4. Use 2 or 3 mappers optimally so that it does not affect the performance of the relational db as a overhead.

When primary key is present SQQOP will automatically detect and maps the part of data to the no of mappers tasks defined.

If primary key is unevenly spread, then use a column that u identify as a split by column.

SQOOP can copy data into a HIVE TABLE using --hive import. SQQOP needs Hive to be configured.

SQOOP runs a local HIVE client in its own server in order to invoke the commands CREATE TABLE for the structure and LOAD DATA INPATH to move the data into HIVE WAREHOUSE.

Use --hive-home to speicfy the HIVE binary in case of multiple HIVE instances.

--hive-overwrite will overwrite the existing table. used in ELT activity.

ETL, ELT, Data transformation processing, HDFS as Data Lake, Data Analysis, Reporting, Business Insights

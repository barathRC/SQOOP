# SQOOP

SQOOP runs MAPRED JOB under the hood

SQOOP IMPORT doesnt happen via CLI but its a server to server copy

You can use --options to specify a particular config file.txt

Max No. of parallel mappers are 4. Use 2 or 3 mappers optimally so that it does not affect the performance of the relational db as a overhead.

When primary key is present SQQOP will automatically detect and maps the part of data to the no of mappers tasks defined.

If primary key is unevenly spread, then use a column that u identify as a split by column.

ETL, ELT, Data transformation processing, HDFS as Data Lake, Data Analysis, Reporting, Business Insights

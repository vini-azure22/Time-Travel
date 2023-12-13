# Time Travel using PySpark
Time Travel in rollback means reverting a computer system to a prior state, ensuring data integrity. Unlike direct edits, it undoes changes by returning to a consistent earlier point, valuable for handling failed operations in databases.

# Code:
#TIMETRAVEL
from delta.tables import *
deltaTable = DeltaTable.forPath(spark, "abfss://transformado@dlsconexaodigitaldev.dfs.core.windows.net/exemplo/de/path/tabela)
latestHistory = deltaTable.history(); 
display(latestHistory)   



df_read = spark.read.format("delta").option("timestampAsOf", "2022-12-23 21:08:24.659").load("abfss://transformado@dlsconexaodigitaldev.dfs.core.windows.net/exemplo/de/path/tabela)

# Information:

*from delta.tables import * *: Imports the necessary classes and methods from the delta.tables library.

deltaTable = DeltaTable.forPath(spark, "abfss://transformed@dlsconexaodigitaldev.dfs.core.windows.net/example/of/path/table"): Creates a reference to a specified Delta Table located at the provided path. The variable deltaTable now represents the Delta Table located at the specified path.

latestHistory = deltaTable.history(): Retrieves the history of operations performed on the Delta Table. This includes information about the versions of the table, the operations performed in each version, and the dates associated with these operations. The result is stored in the variable latestHistory.

display(latestHistory): Displays the obtained history. display is a function used to visualize results in environments like Databricks, for example.

df_read = spark.read.format("delta").option("timestampAsOf", "2022-12-23 21:08:24.659").load("abfss://transformed@dlsconexaodigitaldev.dfs.core.windows.net/example/of/path/table"): Reads data from the Delta Table into a Spark DataFrame. The "timestampAsOf" option specifies a specific version of the data to read, in this case, the version corresponding to the provided date and time ("2022-12-23 21:08:24.659").

In summary, this code works with Delta Tables in the context of Apache Spark, allowing access to the table's history and reading data from a specific version based on timestamp information.

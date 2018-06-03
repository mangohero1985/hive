## hive的重要特性：
* databases和tables首先被创建，然后再加载数据到tables中。
* hive是SQL-like的。
* hive可以自动的创建map-reduce的jobs。
* hive支持partition和buckets操作。
* hive支持UDF
## hive和关系数据库的主要不同：
* 关系型数据库是基于“Schema on READ and Schema on WRITE", Hive是基于“Schema on READ only”。
## hive主要三个核心：
* hive clients
	- 针对应用的不同提供多种驱动, 例如JDBC或者ODBC
* hive services
	- 为client的操作提供接口。
* hive storage and computing
	- 数据存储和定义

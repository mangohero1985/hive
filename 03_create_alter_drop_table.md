## sytax
* 创建table
		
		CREATE TABLE <TableName> (field1 type1, field2 type2);
* 查看table
		
		SHOW TABLE
* table改名
		
		ALTER TABLE <old tablename> TO <new tablename>;
* 删除table
		
		DROP TABLE <tablename>;
## table的种类和使用
* hive中包括两种table类型，一种是是Internal， 另一种是External。
* Internal类型：
	- 紧耦合特性，先创建table然后导入数据。data on schema。
	- 当删除table的时候， 数据和schema都会被删除
	- 这种table的存储位置将会是/user/hive/warehouse。
	- 什么时候选择Internal:
		- 处理的数据在local file system
		- 想要hive去管理数据的整个lifecycle，包括删除。
		- example：
			- 创建inernal表格
					
					CREATE TABLE <tablename> (field1 type1, field2 type2);
					Row format delimited
					Fields terminated by '\t'
			- 加载数据到table
					
					LOAD DATA INPATH '/data/path/data.txt' INTO <tablename>；
			- 查看表格
					
					SELECT * FROM <tablename>
			- 删除表格
					
					注：这里schema和data都将会被删除
					DROP TABLE <tablename>
* External类型：
	- 松耦合类型， 这种类型的表格将会去创建HDFS数据， schema on data。
	- 删除表格只会删除schema，不会删除HDFS上的数据。
	- 通过为HDFS上的数据穿件多种schema来代替每次都先delete再update的操作。
	- 什么时候选择External：
		- 在HDFS上处理数据
		- 数据在hive之外也会被使用。
		- example
			- 创建External类型表格：
					
					CREATE EXTERNAL TABLE <tablename> (field1 type1, field2 type2);
					Row format delimited
					Fields terminated by '\t'
					LOCATION '*****';
			- 也可以另外加载数据到表格：
					
					LOAD DATA INPATH '***' INTO <tablename>;
			- 删除表格：
					
					DROP TABLE <tablename>；

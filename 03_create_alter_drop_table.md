## sytax
* 创建table
		
		CREATE table <TableName> (field1 type1, field2 type2);
* 查看table
		
		SHOW table
* table改名
		
		ALTER table <old tablename> to <new tablename>;
* 删除table
		
		DROP table <tablename>;
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
					
					CREATE table <tablename> (field1 type1, field2 type2);
				Row format delimited
				Fields terminated by '\t'
		- 加载数据到table
		
		LOAD data inpath '/data/path/data.txt' into <tablename>；


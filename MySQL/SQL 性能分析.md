
## explain 执行计划
`EXPLAIN` 或者 `DESC` 命令获取 MySQL 如何执行 SELECT 语句的信息，包括在 SELECT 语句执行过程中如何
![|800](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250302202255218.png)

- Id
	- select 查询的序列号，表示查询中执行 select 子句或者是操作表的顺序 (id 相同，执行顺序从上到下；id 不同，值越大，越先执行)
- 
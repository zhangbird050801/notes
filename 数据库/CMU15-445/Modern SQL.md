# 聚合函数


找出所有以 @cs 为结尾的学生的数量。
```sql
SELECT COUNT(login) AS cnt
	FROM student WHERE login LIKE '%@cs'
```

也可以是
```sql
SELECT COUNT(*) AS cnt
	FROM student WHERE login LIKE '%@cs'
```

```sql
SELECT COUNT(1) AS cnt
	FROM student WHERE login LIKE '%@cs'
```

因为实际上就是在数元组数量。

`%` 匹配一个或者多个字符，包括空字符。` _ ` 匹配单个字符。

获取这些学生的数量和平均绩点:
```sql
SELECT AVG(gpa), COUNT(sid) 
	FROM student WHERE login LIKE '%@cs'
```


Get the average GPA of students enrolled in each course:
```ad-error
以下写法是错误的
```

```sql
SELECT AVG(s.gpa), e.cid
	FROM enrolled AS e JOIN student AS s
		ON e.sid = s.sid
```

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250418200035927.png)

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250418200132854.png)
虽然加上 `ANY_VALUE` 之后获取的值也是没有意义的。
正确的解决方法是我们需要用到 `GROUP_BY`，因为我们要获得基于课程 ID 的每门课的平均 GPA。

## GROUP BY
![|900](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250418202130179.png)


```sql
SELECT AVG(s.gpa), e.cid
	FROM enrolled AS e JOIN student AS s
		ON e.sid = s.sid
GROUP BY e.cid
```

## HAVING
不能这样做，因为 avg_gpa 是在聚合之后才获得到的值，所以 group by 之前它并不知道是多少。
![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250418203322140.png)
要使用 HAVING 语句：
```sql
SELECT AVG(s.gpa) AS avg_gpa, e.cid
	FROM enrolled AS e, student AS s
WHERE e.sid = s.sid
GROUP BY e.cid
HAVING avg_gpa > 3.9;
```

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250418203511646.png)

但是有些系统不允许在 HAVING 语句使用别名。
正确的做法：
```sql
SELECT AVG(s.gpa) AS avg_gpa, e.cid
	FROM enrolled AS e, student AS s
WHERE e.sid = s.sid
GROUP BY e.cid
HAVING AVG(s.gpa) > 3.9;
```
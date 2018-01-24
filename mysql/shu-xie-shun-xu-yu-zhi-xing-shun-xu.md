# 语法

SELECT selection\_list /\*要查询的列名称\*/

 FROM table\_list /\*要查询的表名称\*/

 WHERE condition /\*行条件\*/

 GROUP BY grouping\_columns /\*对结果分组\*/

 HAVING condition /\*分组后的行条件\*/

 ORDER BY sorting\_columns /\*对结果分组\*/

 LIMIT offset\_start, row\_count /\*结果限定\*/

 

# 书写顺序与执行顺序

查询语句书写顺序：select - from - where - group by - having - order by - limit

查询语句执行顺序：from - where - group by - having - select - order by（不能写函数，使用别名）- limit

### 出现null

```Mysql
SELECT *,sal+IFNULL(comm,0) FROM emp;
```




# 书写顺序与执行顺序

查询语句书写顺序：select – from- where- group by- having- order by-limit

查询语句执行顺序：from - where -group by - having - select - order by（不能写函数，使用别名）-limit

出现null

```Mysql
SELECT *,sal+IFNULL(comm,0) FROM emp;
```



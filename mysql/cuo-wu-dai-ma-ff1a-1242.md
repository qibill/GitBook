# 错误代码： 1242 
Subquery returns more than 1 row
子查询返回超过1行

## 错误语句

```
select * 
from integralexchange 
where type_num = 
    (select ie_id 
    from integralexchange 
    where need_money >500) 
and groupnum=2 ;
```
## 错误原因

查询出ie_id是多条数据，而外层查询结果是要求 type_num为一条数据

## 解决办法

```
select * 
from integralexchange 
where type_num in 
    (select ie_id 
    from integralexchange 
    where need_money >500) 
and groupnum=2 ;
```
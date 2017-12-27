# 错误代码： 1248

Every derived table must have its own alias 每个表必须有自己的别名

## 错误语句

```Mysql
update integralexchange
set surplus_num =0
where ie_id in
    (select ie_id
    from
        (select ie_id
        from integralexchange 
        where type_num in
            (select ie_id 
            from integralexchange 
            where need_money >500 
            and groupnum=2)));
```

## 错误原因

子查询已被具体化为临时表,缺少别名。

## 解决办法

```Mysql
update integralexchange
set surplus_num =0
where ie_id in
    (select ie_id
    from
        (select ie_id
        from integralexchange 
        where type_num in
            (select ie_id 
            from integralexchange 
            where need_money >500 
            and groupnum=2)) a);
```




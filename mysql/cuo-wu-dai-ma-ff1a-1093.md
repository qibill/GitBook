# 错误代码： 1093 {#错误代码-1093}

You can't specify target table 'TEST\_NOIDX' for update in FROM clause

update的表不能出现在from语句中

## 错误语句

```Mysql
update integralexchange
set surplus_num =0
where ie_id in
    (select ie_id
    from integralexchange 
    where type_num in
        (select ie_id 
        from integralexchange 
        where need_money >500
        and groupnum=2));
```

## 错误原因

mysql对子查询的支持是比较薄弱的,update的表不能出现在from语句中。

## 解决办法

1. 多加一个嵌套。
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
2. 改成inner join,手册上的方法\(未验证\)。
   ```Mysql
   update integralexchange a
   inner join
    (select ie_id
    from integralexchange 
    where type_num in
        (select ie_id 
        from integralexchange 
        where need_money >500 
        and groupnum=2)) b
   on a.ie_id=b.ie_id
   set surplus_num =0;
   ```




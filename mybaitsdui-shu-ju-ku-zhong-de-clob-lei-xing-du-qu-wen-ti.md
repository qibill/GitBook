# Mybaits对数据库中的clob类型读取问题

### 在sqlmap里定义一下clob类型Mybaits就能直接变成string



```xml
<resultMap id="tempblob" class="java.util.HashMap">  
      <result property="CONTENT" column="CONTENT" jdbcType="BLOB" javaType = "java.lang.String" />  
</resultMap> 
```




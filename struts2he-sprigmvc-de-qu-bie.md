# struts2和sprigmvc的区别

### 1. 实现机制：

Struts2是基于过滤器实现的。

Springmvc基于servlet实现。Servlet比过滤器快。

### 2.运行速度：

Struts2是多例

Springmvc是单例。

### 3.参数封装来分析：

Struts基于属性进行封装。

Springmvc基于方法封装。颗粒更细

```java
Public class UserAction extends ActionSupport implements ModelDriven{
    Private User = new User();
    Private List<User> list;
}
```

请求来了以后，struts2创建多少个对象：

ActionContext，valuestack，UserAction，ActionSuport，ModelDriven

userAction里面属性：User对象，userlist集合等

```java
Public class UserController(){

}
```

访问一次，只需创建方法里面的几个对象。对象是局部变量。使用完毕后就销毁。


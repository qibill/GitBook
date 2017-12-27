# spring拦截器



```
Public class HandlerInterceptor1 implements HandlerInterceptor{

	/**
	 * controller执行前调用此方法
	 * 返回true表示继续执行，返回false中止执行
	 * 这里可以加入登录校验、权限拦截等
	 */
	@Override
	Public boolean preHandle(HttpServletRequest request,
			HttpServletResponse response, Object handler) throws Exception {
		// TODO Auto-generated method stub
		Return false;
	}
	
	/**
	 * controller执行后但未返回视图前调用此方法
	 * 这里可在返回用户前对模型数据进行加工处理，比如这里加入公用信息以便页面显示
	 */
	@Override
	Public void postHandle(HttpServletRequest request,
			HttpServletResponse response, Object handler,
			ModelAndView modelAndView) throws Exception {
		// TODO Auto-generated method stub}
	
	/**
	 * controller执行后且视图返回后调用此方法
	 * 这里可得到执行controller时的异常信息
	 * 这里可记录操作日志，资源清理等
	 */
	@Override
	Public void afterCompletion(HttpServletRequest request,
			HttpServletResponse response, Object handler, Exception ex)
			throws Exception {
		// TODO Auto-generated method stub		
	}
}

```



```
    <mvc:interceptors>
        <mvc:interceptor>
            <mvc:mapping path="/**"/>
            <!-- <mvc:mapping path="/item/**"/> -->
            <bean class="com.taotao.portal.interceptor.Interceptor1"></bean>
        </mvc:interceptor>
                <mvc:interceptor>
            <mvc:mapping path="/**"/>
            <!-- <mvc:mapping path="/item/**"/> -->
            <bean class="com.taotao.portal.interceptor.Interceptor2"></bean>
        </mvc:interceptor>
    </mvc:interceptors>
```

### 第一个拦截器放行，第二个拦截器也放行：

这是第一个拦截器Interceptor1。。。preHandle  
这是第二个拦截器Interceptor2。。。preHandle

这是第二个拦截器Interceptor2。。。postHandle  
这是第一个拦截器Interceptor1。。。postHandle

这是第二个拦截器Interceptor2。。。afterCompletion  
这是第一个拦截器Interceptor1。。。afterCompletion

### 第一个拦截器放行，第二个不放行：

==Springmvc规定：凡是preHandle返回true，afterCompletion必须执行。==

这是第一个拦截器Interceptor1。。。preHandle  
这是第二个拦截器Interceptor2。。。preHandle  
这是第一个拦截器Interceptor1。。。afterCompletion

### 拦截器1阻止，拦截器2阻止：

HandlerInterceptor1.........preHandle


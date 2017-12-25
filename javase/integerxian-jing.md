# Integer陷阱（0~127和其他 数值相等对象比较）

```java
public class Main {
    public static void main(String[] args) {
        Integer a = 200;
        Integer b = 200;
        System.out.println(a == b);// false
        System.out.println(a.equals(b));// true

        // 数据在byte范围内，JVM不会从新new对象
        Integer aa = 127;
        Integer bb = 127;
        System.out.println(aa == bb);// true
        System.out.println(aa.equals(bb));// true

        Integer aaa = 128;
        Integer bbb = 128;
        System.out.println(aaa == bbb);// false
        System.out.println(aaa.equals(bbb));// true
    }
}
```

       原因在于，在进行自动拆装箱时，编译器会使用Integer.valueof\(\)来创建Integer实例。

       以下是Integer.valueof\(\)的源代码：

```java
public static Integer valueOf(int i) {  
    assert IntegerCache.high >= 127;  
    if (i >= IntegerCache.low && i <= IntegerCache.high)  
        return IntegerCache.cache[i + (-IntegerCache.low)];  
    return new Integer(i);  
}
```

       简单地解释这段代码，就是如果传入的int在IntegerCache.low和IntegerCache.high之间，那就尝试看前面的缓存中有没有打过包的相同的值，如果有就直接返回，否则就创建一个Integer实例。IntegerCache.low 默认是-128；IntegerCache.high默认是127.

       注：如果要比较两个对象的内容是否相同，尽量不使用== 或者!= 来比较，可以使用equal\(\)来实现。


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




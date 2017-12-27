# String的地址

```java
public class Main {

    public static void main(String[] args) {
        String str1 = "1";
        String str2 = "2";
        String str3 = "12";
        String str4 = str1 + str2;
        System.out.println(str4 == str3);
    }
}
```

> false

str4=str1+str2 编译后的结果是

```java
str4 = new Stringbuilder·(str1).append(str2).tostring();
```

Stringbuiler中的tostring方法为：

```java
    public String toString() {
        // Create a copy, don't share the array
        return new String(value, 0, count);
    }
```

最后的编译结果为：

```
str4 = new String("12");
```

str4栈空间为堆空间new String的地址，堆空间指向常量池中的"12"。而str3栈空间直接指向常量池中的"12"。

故str3 !=str4.


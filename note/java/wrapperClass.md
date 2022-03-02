## 包装类型自动装箱与拆箱

基本类型都有对应的包装类型，基本类型与其对应的包装类型之间的赋值使用自动装箱与拆箱完成。 

**自动装箱**是 Java 编译器在基本类型与包装类型之间的自动转换，例如 int 转换为 Integer，将 double 转换为 Double 等等。如果是包装类型转换为基本类型，称为**拆箱**。

```java
Character ch = 'a';
Integer x = 2;     // 装箱 调用了 Integer.valueOf(2)
int y = x;         // 拆箱 调用了 X.intValue()
```

在下面的代码中，li 是 Integer 类型的链表，而这里添加的 int 类型，但是编译器在运行时会自动装箱，将 `li.add(i)` 自动转换为 `li.add(Integer.valueOf(i))`。

```java
List<Integer> li = new ArrayList<>(); 
for (int i = 1; i < 50; i += 2) 
    li.add(i);	// li.add(Integer.valueOf(i))
```

将基本类型（例如`int`）转换为相应包装类（`Integer`）的对象称为**自动装箱**。Java 编译器在原始值是以下情况时应用自动装箱： 

-   作为参数传递给需要相应包装类对象的方法。
-   分配给相应包装类的变量。

下面代码中，运算符不适用于 `Integer` 类，因此 Java 编译器调用 ` intValue ` 方法在运行时将 `Integer`  转换为 `int`。

```java
public static int sumEven(List<Integer> li) {
    int sum = 0;
    for (Integer i: li)
        if (i % 2 == 0)
            sum += i;	// sum += i.intValue();
        return sum;
}
```

将包装类型 ( `Integer` ) 的对象转换为其对应的基本类型 ( `int` ) 称为**拆箱**。Java 编译器在包装类的对象是以下情况时应用拆箱：

-   作为参数传递给需要相应基本类型值的方法。
-   分配给相应基本类型的变量。

```java
import java.util.ArrayList;
import java.util.List;

public class Unboxing {

    public static void main(String[] args) {
        Integer i = new Integer(-8);

        // 1. Unboxing through method invocation
        int absVal = absoluteValue(i);
        System.out.println("absolute value of " + i + " = " + absVal);

        List<Double> ld = new ArrayList<>();
        ld.add(3.1416);    // Π is autoboxed through method invocation.

        // 2. Unboxing through assignment
        double pi = ld.get(0);
        System.out.println("pi = " + pi);
    }

    public static int absoluteValue(int i) {
        return (i < 0) ? -i : i;
    }
}
```


## java的基本概念
### 1. java语言的优点
- 简单高效

java语言相对于c++语言，没有有文件，指针等复杂的特性
- 面向对象

java是一门面向对象的语言，以类的形式进行组织，用类来定义对象的各种的行为。并且支持类的继承，减少了程序的复杂性
- 平台无关性

任何的平台都可以进行运行，可以达到一处编译，处处运行。java代码，经过编译后生成为字节码(bytecode)。字节码是不依赖任何硬件和操作系统。这样的优点是因为java虚拟机的功劳。生成的字节码通过一条条的解释执行，或者通过编译器的编译为本地代码(native code)，直接执行。
- 交互式特性

java面向对象的网络编程语言，支持TCP/IP协议。
- 多线程机制

java语言支持多线程机制。多线程机制可以使java程序能够并行处理多项任务。
- 动态的内存管理机制

java语言采用自动垃圾回收机制进行内存的管理。在C++语言中，程序员需要在编写程序的时候仔细的处理内存的使用，例如在某块内存使用完成之后，及时的释放，以便供其他的程序使用。一旦内存管理出现一些问题，就可能会出现内存空间的浪费或程序运行的故障。在java中包含了一个内存管理机制，java虚拟机会自动、安全的回收不再使用的内存，这样的程序员就无需担心内存的管理问题，从而是java程序的编写变得简单。
- 安全性


- 效率高

java虚拟机的JIT即时编译器，编译的速度快

### 什么是自动拆装箱？
java语言支持8中基本的数据类型
`byte, char, short, int, long, float, double, boolean `

自动装箱是java编译器在基础数据类型和对应的对象包装类型直接做的一个转换。
int--->Integer 装箱
Integer--->int 拆箱

#### int 和 Integer 有什么区别?
Java 是一个近乎纯洁的面向对象编程语言，但是为了编程的方便还是引入不是对象的基本数据类型，但是为了能够将这些基本数据类型当成对象操作，Java 为每一个基本数据类型都引入了对应的包装类型（wrapper class），int 的包装类就是 Integer，从 JDK 1.5 开始引入了自动装箱/拆箱机制，使得二者可以相互转换。

Java 为每个原始类型提供了包装类型：

原始类型: boolean，char，byte，short，int，long，float，double

包装类型：Boolean，Character，Byte，Short，Integer，Long，Float，Double
```java
public class AutoUnboxingTest {  

    public static void main(String[] args) {  
        Integer a = new Integer(3);  
        Integer b = 3;              // 将3自动装箱成Integer类型  
        int c = 3;  
        System.out.println(a == b); // false 两个引用没有引用同一对象  
        System.out.println(a == c); // true a自动拆箱成int类型再和c比较  
    }  
}  
```


### 一个.java文件中是否可以包括多个类(不是内部类)？有什么限制？
可以有多个类，但是只能有一个public类，并且public的类名和文件名要一致

### 静态变量(static)和实例变量的区别？Java 中是否可以覆盖(override) 一个 private 或者是 static 的方法？

语法上，静态变量前加static；实例变量前没有。

区别主要是在程序运行时。
实例变量就是对象的熟悉，只有在创建了实例对象的时候，实例变量才会被分配空间，才能够使用这个实例变量。
静态变量不属于某一个实例对象，也是说静态变量是属于类，可称为类变量。

程序的加载了类的字节码，不会创建任何实例变量，但会为静态变量分配空间，静态变量就可以使用。

无论对象创建了多少，静态变量在内存中只会一个拷贝，也就是说，静态变量可以实现让多个对象共享内存。
静态变量依存于实例对象，只有创建实例对象才能访问它。

static关键字修饰变量或者成员方法可以在没有所属类的实例变量的情况下进行访问。
java的static方法不能被不覆盖，方法的覆盖是在运行的时候动态绑定的，而static方法是在编译的时候动态绑定的。
static方法跟类的实例都不想关，所以不可以被覆盖。


### 是否可以在 static 环境中访问非 static 变量？

static变量在java中是属于类的，它在所有的实例中的值都是一样的。当类被java虚拟机载入的时候，会对java的static变量进行初始化。如果在没有实例化的情况下，来访问非static变量，编译会报错，因为变量还没有创建，没有和任何的实例对象关联上。

### Java 中方法覆盖(overriding)和方法重载(overloading)
重载是在同一个类中，方法名相同但是参数不同；
方法的覆盖是子类重新定义父类的方法。方法覆盖，必须和父类的方法名和参数以及返回类型都是一致的。

### 构造器Constructor是否可以被override？
构造器Constructor不可以被继承，因此不能重写override，但可以被重载。

### 接口和抽象类的区别

不同点：
- 接口中的所有方法隐含都是抽象的。抽象类则可以包含抽象和非抽象的方法。
- 类可以有多个接口，但只能继承一个抽象类
- 类如果要实现一个接口，必须实现所有接口声明的所有方法。但类不用实现抽象类的所有方法。

抽象类可以在不提供接口方法实现的情况下实现接口。
Java 接口中声明的变量默认都是 final 的。抽象类可以包含非 final 的变量。
Java 接口中的成员函数默认是 public 的。抽象类的成员函数可以是 private，protected 或者是 public 。
接口是绝对抽象的，不可以被实例化。抽象类也不可以被实例化，但是，如果它包含 main 方法的话是可以被调用的。

### 下面的说法正确的是：
A. class 中的 constructor 不可省略
B. constructor 必须与 class 同名，但方法不能与class同名
C. **constructor在一个对象被 new 时执行**
D. 一个 class 只能定义一个 constructor
> 这里可能会有误区，其实普通的类方法是可以和类名同名的，和构造方法唯一的区分就是，构造方法没有返回值。

### java接口的修饰符可以为？
A. private
B. protected 
**C. final**
**D. abstract**

- 接口用于描述系统对外提供的所有服务,因此接口中的成员常量和方法都必须是公开(public)类型的,确保外部使用者能访问它们
- 接口仅仅描述系统能做什么,但不指明如何去做,所以接口中的方法都是抽象(abstract)方法
- 接口不涉及和任何具体实例相关的细节,因此接口没有构造方法,不能被实例化,没有实例变量，只有静态（static）变量

### 下面是 People 和 Child 类的定义和构造方法，每个构造方法都输出编号。在执行 new Child("mike") 的时候都有哪些构造方法被顺序调用？请选择输出结果
```java
class People {
    String name;

    public People() {
        System.out.print(1);
    }

    public People(String name) {
        System.out.print(2);
        this.name = name;
    }
}

class Child extends People {
    People father;

    public Child(String name) {
        System.out.print(3);
        this.name = name;
        father = new People(name + ":F");
    }

    public Child() {
        System.out.print(4);
    }

}
```
A. 312
B. 32
C. 432
**D. 132**
> 考察的又是父类与子类的构造函数调用次序。在 Java 中，子类的构造过程中必须调用其父类的构造函数，是因为有继承关系存在时，子类要把父类的内容继承下来。但如果父类有多个构造函数时，该如何选择调用呢？
第一个规则：子类的构造过程中，必须调用其父类的构造方法。一个类，如果我们不写构造方法，那么编译器会帮我们加上一个默认的构造方法（就是没有参数的构造方法），但是如果你自己写了构造方法，那么编译器就不会给你添加了，所以有时候当你 new 一个子类对象的时候，肯定调用了子类的构造方法，但是如果在子类构造方法中我们并没有显示的调用基类的构造方法，如：super(); 这样就会调用父类没有参数的构造方法。
第二个规则：如果子类的构造方法中既没有显示的调用基类构造方法，而基类中又没有无参的构造方法，则编译出错，所以，通常我们需要显示的：super(参数列表)，来调用父类有参数的构造函数，此时无参的构造函数就不会被调用。
总之，一句话：**子类没有显示调用父类构造函数，不管子类构造函数是否带参数都默认调用父类无参的构造函数，若父类没有则编译出错。**

### 下面程序的运行结果
```java
class A{  

    static{  
        System.out.print("1");  
    }  

    public A(){  
        System.out.print("2");  
    }  
}  

class B extends A{  

    static{  
        System.out.print("a");  
    }  

    public B(){  
        System.out.print("b");  
    }  
}  

public class Hello{  

    public static void main(String[] args){  
        A ab = new B();  
        ab = new B();  
    }  

}  
```
答案是：**1a2b2b**
创建对象构造器的调用顺序是
> 初始静态成员 --> 调用父类构造器 --> 初始化非静态成员 --> 调用自身的构造器

### 判断下列语句是否正确，如果有错误，请指出错误所在？
```java
interface A{
    int add(final A a);
}

class B implements A{
    long add(final A a){
    return this.hashCode() + a.hashCode();
    }
}
```
返回值不是 long 类型

###  == equals instanceof

- 使用 == 操作符检查“参数是否为这个对象的引用”；
- 使用 instanceof 操作符检查“参数是否为正确的类型”；
- 对于类中的关键属性，检查参数传入对象的属性是否与之相匹配；
- 编写完 equals 方法后，问自己它是否满足对称性、传递性、一致性；
- 重写 equals 时总是要重写 hashCode；
- 不要将 equals 方法参数中的 Object 对象替换为其他的类型，在重写时不要忘掉 @Override 注解。
#### `==`
- `==`:关系操作符生成的是一个boolean的结果，计算的是操作数的值之间的关系。说的简单一点就是比较的是两个值是否相等。
```java
public class Equals{
    public static void main(String[] args){
        int m = 3;
        int n = 3;
        System.out.println(m == n);

        String str = new String("hello");
        String str1 = new String("hello");
        String str2 = new String("hello");

        System.out.println(str1 == str2);

        str1 = str;
        str2 = str;
        System.out.println(str1 == str2);
    }
}
```
```
true
false
true
```
m和n存储都是数值，肯定是相同的。
这里要提一下，基本数据类型和非基本数据类型的区别。
java的基本数据类型
`byte, char, short, int, long, float, double, boolean `
对于上面的基本数据类型，关系操作符比较的就是值本身，所以`m=n`。
对于非基础数据类型(引用类型的变量)，存储的并不是值本身，而是与其相关联的对象在内存中的地址。
上面代码中str,str1,str2都是创建的不同的对象，分别指向不同的内存地址，所以使用关系运算符`==`，返回的就是false。
```java
str1 = str;
str2 = str;
System.out.println(str1 == str2);
```
上面的str1和str2指向的是同一个对象，也就是说同一个内存地址，所以返回的就是true。
#### `equals`

equals方法是基于Object中方法的，所有继承Object类的类都有该方法。
默认比较的是类型变量所指向的对象的地址。

### 访问修饰符 public, private, protected, 以及不写（默认）时的区别？
|修饰符|当前类|同包|子类|其他包|
|-----|-----|-----|-----|-----|
|public|Y|Y|Y|Y|
|protected|Y|Y|Y|N|
|private|Y|N|N|N|
|default|Y|Y|N|N|

> 类的成员不写访问修饰时默认为 default 。默认对于同一个包中的其他类相当于公开（public），对于不是同一个包中的其他类相当于私有（private）。受保护（protected）对子类相当于公开，对不是同一包中的没有父子关系的类相当于私有。Java 中，外部类的修饰符只能是 public 或默认，类的成员（包括内部类）的修饰符可以是以上四种。

### java的final关键字
- 修饰类：该类不能够被继承
- 修饰方法：表示方法不能被重写
- 修饰变量：修饰变量只能赋值一次，赋值后不能被修改

### final, finally, finalize
final 见上
finally：通常放在 try…catch 的后面构造总是执行代码块，这就意味着程序无论正常执行还是发生异常，这里的代码只要 JVM 不关闭都能执行，可以将释放外部资源的代码写在 finally 块中。

finalize：Object 类中定义的方法，Java 中允许使用 finalize() 方法在垃圾收集器将对象从内存中清除出去之前做必要的清理工作。这个方法是由垃圾收集器在销毁对象时调用的，通过重写finalize() 方法可以整理系统资源或者执行其他清理工作。

### `&` `&&` `|` `||`

#### `&` `&&`
两者可以用作逻辑与的运算符，表示的逻辑与操作(and)，当运算符两边的表达式的结果都为 true 时，整个运算结果才为 true，否则，只要有一方为 false，则结果为 false。

但两者存在一定的差异：
- `&&` 具有短路的功能，也就是第一个表达式的为false，不再计算第二个表达式。对于 `if(str != null&& !str.equals(“”))` 表达式，当 str 为 null 时，后面的表达式不会执行，所以不会出现 `NullPointerException `如果将 `&&` 改为` &` ，则会抛出`NullPointerException` 异常。`If(x==33 & ++y>0)` y 会增长， `If(x==33 && ++y>0)` 不会增长。
- `&` 还可以用作位运算符，当 `&` 操作符两边的表达式不是 `boolean` 类型时，`&` 表示按位与操作，我们通常使用 0x0f 来与一个整数进行 & 运算，来获取该整数的最低 4 个 bit 位，例如，0x31 & 0x0f 的结果为 0x01。

### 存在使 i + 1 < i的数吗?
答案：存在

解析：如果 i 为 int 型，那么当 i 为 int 能表示的最大整数时，i+1 就溢出变成负数了，此时不就 <i 了吗。

扩展：存在使 i > j || i <= j 不成立的数吗?

答案：存在

解析：比如 Double.NaN 或 Float.NaN 。

###  char 型变量中能不能存贮一个中文汉字?为什么?
答：char 类型可以存储一个中文汉字，因为 Java 中使用的编码是 Unicode（不选择任何特定的编码，直接使用字符在字符集中的编号，这是统一的唯一方法），一个 char 类型占 2 个字节（16bit），所以放一个中文是没问题的。

补充：使用 Unicode 意味着字符在 JVM 内部和外部有不同的表现形式，在 JVM 内部都是 Unicode，当这个字符被从 JVM 内部转移到外部时（例如存入文件系统中），需要进行编码转换。所以 Java 中有字节流和字符流，以及在字符流和字节流之间进行转换的转换流，如 InputStreamReader 和 OutputStreamReader，这两个类是字节流和字符流之间的适配器类，承担了编码转换的任务；对于 C 程序员来说，要完成这样的编码转换恐怕要依赖于union（联合体/共用体）共享内存的特征来实现了。

### 字符串初始化，代码是没有办法编译成功的
```java
import java.io.*;
import java.util.*;

public class foo{

    public static void main (String[] args){

        String s;

        System.out.println("s=" + s);

    }

}
```
上面的代码就是一个很好的例子，String s没有初始化，代码不能够编译通过。

### length，length()使用的时候经常的混淆
数组-----> length, 数组用length属性
String----->length()，string的长度，通过length()方法获得。

### String是final类，没有 办法继承

### String s=new String(“xyz”);创建了几个字符串对象？
- 两个对象，一个是静态存储区的"xyz",一个是用new创建在堆上的对象。

### 字符串转化为数字
```java
String s=”12345″;

long num=Long.valueOf(s).longValue();
```

### 为了显示 myStr = 23 这样的结果，写出在控制台输入的命令
```java
public class MyClass {

public static void main(String args[]) {

    String s1 = args[0];

    String s2 = args[1];

    String myStr = args[2];

    System.out.printin(“myStr =” + s2 + myStr);

    }

}
```
答：java MyClass 1 2 3 4

### String,StringBuilder,StringBuffer
- String是只读字符串，也就意味着String引用的字符串内容是不能被改变的。
- StringBuilder是JDK 1.5中引入的，它和 StringBuffer 的方法完全相同，区别在于它是在单线程环境下使用的，因为它的所有方面都没有被 synchronized 修饰，因此它的效率也比 StringBuffer 略高。

有一个面试题问：有没有哪种情况用 + 做字符串连接比调用 StringBuffer / StringBuilder 对象的 append 方法性能更好？如果连接后得到的字符串在静态存储区中是早已存在的，那么用+做字符串连接是优于 StringBuffer / StringBuilder 的 append 方法的。

### 输入输出流

### 什么是序列化？如何实现序列化？

序列化就是一种用来处理对象流的机制


# Java语言特点



java编译器不将对变量和方法的引用编译为数值引用，也不确定程序执行过程中的内部布局，而是将这些符号引用信息保留在一种扩展名为.class的字节码文件中，.class文件的最大特点就是不包含硬件的信息。如果需要执行，还要再由java的解释器在解释执行字节码的过程中创立内存布局，然后再通过查表来确定每一条指令所在的具体位置。

## 简单

*    lava语言学习起来很简单。它的设计思想是通过提供最基本的方法来完成指定的任务,只需理解一些基本的概念,就可以用它编写出适合于各种情况的应用程序。
*    Java省略了运算符重载、多重继承等模糊的概念,并且通过实现自动垃圾收集,大大简化了程序设计者的内存管理工作。
*     Java也适合于在低档机器上运行。它的基本解释器及类的支持只有40KB左右,加上标准类库和线程的支持也只有215KB左右。
*    Java适合用于各种嵌入式设备。

## 面向对象

*    Java是一种完全面向对象的程序设计语言。
*    它除了数值、布尔和字符3种基本类型之外,其他类型都是对象,完全摒弃了非面向对象的特性。
*    Java语言的设计集中于对象及其接口,它提供了简单的类机制以及动态的接口模型。
*    对象中封装了它的状态变量以及相应的方法,实现了模块化和信息隐藏。
*    而类则提供了一类对象的原型,并且通过继承机制,子类可以使用父类所提供的方法,实现了代码的复用。因此,大大提高了程序开发的效率。

## 分布式

*    分布式包括数据分布和操作分布。
*    数据分布是指数据可以分散在网络的不同主机上,操作分布是指把一个计算分散在不同主机上处理。
*    Java支持www客户机服务器计算模式,因此,它支持这两种分布性。
*    对于数据分布, Java提供了一个叫作URL的对象,利用这个对象,可以打开并访问具有相同URL地址上的对象,访问方式与访问本地文件系统相同
*    对于操作分布, Java的Applet小程序可以从服务器下载到客户端,即部分计算在客户端进行,提高系统执行效率。
*    Java提供了一整套网络类库,封装了Internet上的各种协议,开发人员可以利用类库进行网络程序设计,方便地实现Java的分布式特性。

## 结构中立

## 可移植

*    平台无关性是指用Java写的应用程序不用修改就可在不同的软硬件平台上运行。平台无关有两种:源代码级和目标代码级。
*    C和C++具有一定程度的源代码级平台无关,用C或C++写的应用程序不用修改,只需重新编译就可以在不同的平台上运行。
*    Java的跨平台性是目标代码级的,它通过JVM实现了“一次编译,处处运行”。

## 解释执行

## 健壮

*    Java最初设计的目的是应用于电子类消费产品,因此要求其具有较高的可靠性。
*    Java虽然源于C++,但它消除了许多C++的不可靠因素,可以避免许多编程错误。
*    Java是强类型的语言,要求用显式的方法声明,这保证了编译器可以发现方法调用错误,使程序更加可靠。
*    Java不支持指针,这杜绝了内存的非法访问。
*    Java解释器在运行时实施检查,可以发现数组和字符串访问的越界,解决了令C\C++程序员极为头痛的越界问题。
*    Java提供自动垃圾收集来进行内存管理,避免程序员在管理内存时容易产生的错误。
*    Java提供集成的面向对象的异常处理机制。
*    在编译时, Java提示可能出现但未被处理的异常,帮助程序员正确地进行选择以防止系统的崩溃。

## 安全

*    由于Java主要用于网络应用程序开发,因此对安全性有较高的要求。
*    如果没有安全保证,用户从网络下载程序并执行就非常危险。Java通过自己的安全机制防止了病毒程序的产生和下载程序对本地系统的威胁破坏。
*    当Java字节码进入解释器时,首先必须经过字节码校验器的检查。然后, Java解释器将决定程序中类的内存布局。随后,类装载器负责把来自网络的类装载到单独的内存区域,避免应用程序之间的相互干扰破坏。最后,客户端用户还可以限制从网络上装载的类只能访问某些文件系统。上述几种机制结合起来,使得Java成为安全的编程语言。

## 高性能

*    和其他解释执行的语言(如BASIC, VBScript, JavaScript和PERL等)不同, Java,字节码的设计使之能很容易地直接转换成对应于特定CPU的机器码,从而得到较高的性能。

## 多线程

*    多线程机制使应用程序能够并行执行,而且同步机制保证了对共享数据的正确操作。
*    通过使用多线程,程序设计者可以分别用不同的线程完成特定的行为,而不需要采用全局的事件循环机制。因此,很容易地实现网络上的实时交互行为。
*    Java在两方面支持多线程:一方面, Java环境本身就是多线程的。若干个系统线程运行负责必要的无用单元的回收、系统维护等系统级操作;另一方面, Java语言内置了多线程控制,可以大大简化多线程应用程序的开发。
*    Java提供了一个Thread类,由它负责启动运行和终止线程,并可检查线程状态。Java的线程还包括一组同步原语。这些原语负责对线程实行并发控制。
*    利用Java的多线程编程接口,开发人员可以方便地写出支持多线程的应用程序,提高程序的执行效率。

## 动态

*    Java的设计使它适合于一个不断发展的环境。在类库中可以自由地加入新的方法和实,例变量,而不会影响用户程序的执行。
*    Java通过接口来支持多重继承,使之比严格的类继承具有更灵活的方式和扩展性。
*    Java在运行时采用动态装载技术,类装入器的灵活性甚至允许动态地重新装入已修改的代码,同时应用程序继续执行。

# Java虚拟机

## JVM

*    JVM的运用，真正让Java实现了“一次编译，处处运行”，它是整个运行系统的核心。

### JVM解释器

*    JVM解释器负责将字节码转换成CPU能执行的机器指令

### 指令系统

*    指令系统同硬件计算机相似。一条指令分成操作码和操作数两部分。操作码为8位二进制数，操作数可以根据需要而定。操作码是为了说明一条指令的功能，所以JVM可以有多达256种不同的操作指令

### 寄存器

*    JVM有自己的虚拟寄存器，这样就可以快速地和JVM的解释器进行数据交换。为了实现必须的功能，JVM设置了4个常用的32位寄存器：pc、optop、frame和vars

### 栈

*    JVM栈是指令执行时数据和信息存储的场所和控制中心，提供给JVM解释器运算时所需要的信息

### 存储区

*    JVM存储区用于存储编译后的字节码等信息

### 碎片回收区

*    JVM碎片回收,是指将那些使用后的Java类的具体实例从内存中进行回收。因此,可以避免开发人员自己编程控制内存的麻烦。随着JVM的不断升级,其碎片回收技术和算法也更加合理。比较经典的算法有引用计数、复制、标记-清除和标记-整理。在JVM 1.4.1版以后,产生了一种代收集技术。简单地说,就是利用对象在程序中生存的时间划分成代,以这个代为标准进行碎片回收。

## 安装运行环境

1.   下载Sun Java Development Kit运行环境
2.   配置环境变量
3.   项目打包成".jar"文件
4.   生成".bat"文件,输入以下代码

```
java -jar %1
```

5.   .jar文件设置打开方式，以bat方式打开
6.   Windows上就可以运行.jar文件

### 环境变量

*    环境变量是包含关于系统及当前登录用户的环境信息的字符串,一些程序使用此信息确定在何处放置和搜索文件。和JDK相关的环境变量有3个: Java home、path和classpath.
*    Java home是JDK安装的目录路径,用来定义path和classpath的相关位置
*    path环境变量告诉操作系统到哪里去查找JDK工具
*    classpath环境变量则告诉JDK工具到哪里去查找类文件(.class文件)。

# 文件

*    bin文件夹:存放编程所要用到的开发工具，包括编译器、解释执行程序、小应用程序浏览器、调试器、文档生成工具和反编译器等。
*    db文件夹:存放JDK自带的小型数据库文件。
*    include文件夹:存放本地文件（Native means）。
*    jre文件夹:Java运行时环境的根目录，存放JVM所需的各种文件。
*    lib文件夹:存放库文件。
*    src.zip文件:是JDK的源文件压缩包，在实际开发过程中，可以将系统诸多类库与源代码进行关联，对于理解程序内部原理，尤其是代码深度调试非常有用。

## JAR文件的创建和使用

在一个包中,通常会有很多个.class文件。为了便于对这些文件的管理,以及减少传输这些文件所需的时间, Java允许把所有的类文件打包成一个文件,这就是JAR文件。 

JAR文件是压缩的,其压缩格式就是ZIP, JAR文件中除了可以包含.class文件之外,还可以像. ZIP文件一样包含其他类型的文件。

如果用Main-Class属性指定了程序的主类,那么可以用java命令来执行一个JAR文件

```java
java -jar "[程序名称]"
```

如果读者使用Windows,还可以通过关联JAR文件与java -jar命令来双击执行JAR文件。

# 命令

## javac命令编译选项

| 选项                  | 含义                               |
| --------------------- | ---------------------------------- |
| -g                    | 生成所有调试信息                   |
| -g:none               | 不生成任何调试信息                 |
| -g:{line,vars,source} | 只生成某些调试信息                 |
| -nowarn               | 不生成任何警告                     |
| -verbose              | 输出有关编译器正在执行的操作的信息 |
| -deprecation          | 输出使用已过时的API的源位置        |
| -classpath            | 指定查找用户类文件的位置           |
| -cp                   | 指定查找用户类文件的位置           |
| -sourcepath           | 指定查找输入源文件的位置           |
| -bootclasspath        | 覆盖引导类文件的位置               |
| -extdirs              | 覆盖安装的扩展目录的位置           |
| endorseddirs          | 覆盖签名的标准路径的位置           |
| -d                    | 指定存放生成的类文件的位置         |
| -encoding             | 指定源文件使用的字符编码           |
| -source               | 提供与指定版本的源兼容性           |
| -target               | 生成指定VM版本的类文件             |
| -version              | 版本信息                           |
| -help                 | 输出标准选项的提要                 |
| -X                    | 输出非标准选项的提要               |
| -J                    | 直接将标志传递给运行时的系统       |


# 标识符

*    区分大小写: Myname与myname是两个不同的标识符
*    首字符,可以是下划线(_)或美元符或字母,但不能是数字
*    除首字符外其他字符,可以是下划线(_)、美元符、字母和数字
*    关键字不能作为标识符

# 关键字

## abstract

### 修饰类

abstract修饰类，这个类就是抽象类，抽象类中可以有非抽象变量和成员变量，也可以有普通方法、构造方法。但是不能实例化，只能被子类继承。
如果子类不是抽象类，则必须重写父类的抽象方法。

```java
public abstract class AbstractList<E> extends AbstractCollection<E> implements List<E> {
    ...
}
```

### 修饰方法

abstract修饰方法，这个方法就是抽象方法。抽象方法必须存在于抽象类中。抽象方法不能有具体实现。

```java
abstract public E get(int index);
```

## assert

```java
assert 表达式;// 表达式为真，程序继续执行；若表达式为假，则抛出一个AssertionError异常
assert 表达式:错误信息;// 使用assert时不能在表达式中完成任何程序实际所需的行为（只能做判断）。因为正常发布的代码都是断言无效的，即正常发布的代码中断言语句都不不执行的
```

## boolean

boolean是Java的基本类型之一（默认值false）。

只有两个值：true和false。

区别C的判断句，Java不能直接使用1和0来表示真假，且boolean类型也不能强转到其他基本类型。

```java
boolean a = true;
boolean b = false;
```

## break

### switch块

break在switch中用于跳出switch块，停止switch向下穿透的现象。

```
case value:expression;
    break;
```

### 循环

用于跳出循环

```java
while(...){
    ...
    break;
}
```

加标签形式

```jave
flag:
for(...){
    for(...){
        break flag;
    }
}
```

## byte

byte是Java的基本类型之一（默认值0）。表示8位有符号整数。

范围：-128~127

## case

case用于switch中，用于判断和执行语句。

```java
case 变量值:语句;
```

## catch

catch用于捕获异常。

在try/catch语句块中，catch捕获发生的异常，并应对错误做一些处理。
当catch捕获到异常后，try中执行的语句终止，并跳到catch后的语句中。

```java
catch(异常类型 异常){...}
```

## char

char是Java的基本类型之一（默认值\u000）。表示16位、在Unicode编码表中的字符。使用单引号来表示字符常量，例如’A’。

范围：0-65535

## class

class表示类。用于声明一个类。

```java
[访问控制] (abstract) class 类名 (implements){...}
```

## const

const是Java的一个保留关键字，没有实际意义，但是不能用于做变量名（因为被保留作为关键字了）。

## continue

continue用于在循环中跳过本次循环。

```java
while(...){
    ...
    continue;
}
```

在后面接标签，在一些嵌套比较复杂的循环中跳过一次循环。

```java
flag:
for(...){
    for(...){
        continue flag;
    }
}
```

## default

### switch

用于switch做默认分支

```java
default:语句；
```

### 接口

用于接口,让接口实现具体的方法

```java
public interface a{
    default void b(){
        具体方法;
    }
}
```

default用于接口时，必须要有具体实现。

## do

do用于和while组成循环，do/while循环不同于while循环，属于先执行循环体再判断。

```java
do{
	循环体;
}while(...)
```

## double

double是Java的基本类型之一（默认值0.0d），表示双精度、64位的浮点数。

## else

else用于分支结构中的判断。

```java
if(判断1){
    语句1;
}else if(判断2){
    语句2;
}else{
    语句3;
}
```

## enum

enum表示枚举，用于限制变量值的类型

枚举类中可以有成员变量和方法。

## extends

extends表示继承。

```java
class 子类 extends父类{}
```

## final

final修饰的变量即成为常量，只能赋值一次，但是final所修饰局部变量和成员变量有所不同。

### 变量

将变量变为常量，在初始化变量后不能再改变值。

01.	final修饰的局部变量必须使用之前被赋值一次才能使用。
02.	final修饰的成员变量在声明时没有赋值的叫“空白final变量”。空白final变量必须在构造方法或静态代码块中初始化。

### 方法

被final修饰的方法不能被子类重写。

final修饰的方法不能被子类覆盖。有时也是出于设计安全的目的，父类中的方法不想被别人覆盖，这是可以使用final关键字修饰父类中方法。

### 类

被final修饰的类不能被继承。

final修饰的类不能被继承。有时出于设计安全的目的，不想让自己编写的类被别人继承，这时可以使用final关键字修饰父类。

## finally

finally在try/catch语句块中处理一些后续的工作。例如关闭网络连接和输入输出流等。

如果在try/catch中使用return，则finally会撤销这个return，无论如何都会执行finally中的语句。

## float

float是Java的基本类型之一（默认值0.0f）。表示单精度、32位的浮点数。

## for

for用于循环

```java
for(初始化循环变量; 判断执行条件;更新循环变量){
    语句
}
for(变量:数组){
    语句
}
```

## goto

Java中的保留关键字，没有实际意义，但是不能用做变量名。在C中表示无条件跳转语句。

## if

if用于分支结构中的判断。常与else和else if使用。

```java
if(表达式){语句}
```

## implements

implements用于接入接口。接上接口的类必须实现接口的抽象方法（可以不实现默认方法和静态方法）。

```java
class A implements B{
    @Override
    do(){
        ...
    }
}
```

## import

用于导入包。

```java
import android.content.Intent;
```

## instanceof

instanceof用于判断类与对象的关系。

```java
a instanceof b// 若a是b的一个实例(或子类对象)，则整个表达式的结果是true，否则结果为false
```

## int

int是Java的基本类型之一（默认值为0）。表示32位、有符号的整数。

范围：[-231,231-1)

## interface

interface用于声明一个接口

## long

long是Java的基本类型之一（默认值为0L），表示64位、有符号的整数。

范围：[-263,263)

## native

native可以让Java运行非Java实现的方法。例如c语言，要编译后用javah产生一个.h文件。导入该.h文件并且实现native方法，编译成动态链接库文件。在Java加载动态链接库文件，这个native方法就可以在Java中使用了。

```java
public native void aVoid();
```

## new

new用于生成类的实例

```java
Object a = new Object()；
```

## package

package用于规定当前文件的包

## private

访问控制的一种。
私有的方法和变量只能在本类中访问。类和接口不能为私有。

## protected

访问控制的一种。
受保护的方法和变量只能给子类和基类访问。

## public

访问控制的一种。
公有的方法、类、变量、接口能够被任何其他类访问。

## return

方法中返回数据，并结束方法。

## strictfp

使用strictfp关键字来声明一个类、接口或者方法时，那么该类、接口或者方法会遵循IEEE-754标准来执行，提高浮点运算的精度，并且减少不同硬件平台之间由于浮点运算带来的差异。

## short

short是Java的基本类型之一（默认值0）,表示16位、有符号的整数。

范围：[-215,215)

## static

static修饰的语句块存放在堆的方法区中。

### 静态变量

依附在类中的变量，可以被类的所有的实例共用

### 静态方法

依附在类中的方法。静态方法只能访问类中的静态变量和静态方法。

### 静态块

在类加载的时候执行块中的语句，块中不能访问非静态变量

### 静态内部类

用static修饰内部类

## super

super即超类

引用父类的的成员

```java
super.xxx
```

变量或方法重名时用super调用父类的成员或方法。

调用父类的构造方法:

```java
super(xxx);
```

## switch

switch用于分支结构，判断某个变量与一系列值是否相等。switch 语句中的变量类型可以是： byte、short、int 、char、String、enum。

```java
switch(变量){
	case value1:语句1;
		break;
	case value2:语句2;
		break;
	...
	default:语句;
}
```

*    若变量和case后的值相等则执行语句。
*    当语句执行到break时跳到switch块后，如果没有break会产生穿透现象。
*    default分支必须为最后一个分支，在没有值和case变量相等时执行该语句。

## synchronized

synchronized关键字用于保证线程安全。由这个关键字修饰的方法或者代码块保证了同一时刻只有一个线程执行该代码。

```java
synchronized(obj){...}
```

当一个线程访问同步代码块时，检查obj是否有锁，如果有就挂起。如果没有就获得这个obj的锁，也就是把其他线程锁在了外面。当代码执行完毕时释放该锁，其他线程获得锁继续执行代码。

## this

*    指向当前对象：this.xxx
*    形参和成员名字重名时时用this区分。
*    引用构造函数。

## throw

用于抛出一个异常。

```java
throw (Exception);
```

## throws

在方法中将发生的异常抛出。

```java
[控制访问](返回类型)(方法名)([参数列表])[throws(异常类)]{...}
```

## transient

类接上序列化接口后，可以通过transient关键字将某些变量变得无法序列化。

## try

在try/catch中，将可能出现异常的语句放在try{}块中，出现异常之后代码将会终止并跳到catch中继续执行。

```java
try{
    ...
}catch(Exception e){
    ...
}finally{
    ...
}
```

## void

修饰方法，表示方法没有返回值。

## volatile

volatile关键字修饰的变量在多线程中保持同步。相比synchronized效率要高，不会阻塞线程。但只能保证数据的可见性，不能保证数据的原子性。例如在处理i++的时候另外一个线程修改i的值，那么i的值将会发生错误，这是原子性导致的。

## while

*    方法1

```java
while(判读语句){
    循环体...
}
```

*    方法2

```java
do{
	循环体...
}while(判读语句)
```

## 保留字

### goto

在其他语言中叫做“无限跳转”语句，在Java语言中不再使用goto语句，因为“无限跳转”语句会破坏程序结构。在Java语言中goto的替换语句可以通过break、continue和return实现“有限跳转”。

### const

在其他语言中是声明常量关键字，在Java语言中声明常量使用public static final 方式声明。

# 分隔符

在Java源代码中，有一些字符被用作分隔，称为分隔符。分隔符主要有：分号（;）、左右大括号（{}）和空白。

## 分号

分号是Java语言中最常用的分隔符，它表示一条语句的结束。

## 大括号

在Java语言中，以左右大括号（{}）括起来语句集合称为语句块（block）或复合语句，语句块中可以有0~n条语句。在定义类或方法时，语句块也被用做分隔类体或方法体。语句块也可以嵌套，且嵌套层次没有限制。

## 空白

在Java源代码中元素之间允许有空白，空白的数量不限。空白包括空格、制表符（Tab键输入）和换行符（Enter键输入），适当的空白可以改善对源代码可读性。

# 变量与常量

## 变量

变量和常量是构成表达式的重要部分，变量所代表的内部是可以被修改的。

```java
数据类型 变量名 [=初始值];
```

变量名要遵守用标识符命名规范，却在相关的作用域中不能有重复的变量名。变量作用域是变量的使用范围，在此范围内变量可以使用，超过作用域，变量内容则被释放，根据作用域不同分为：成员变量和局部变量

## 常量

常量事实上是那些内容不能被修改的变量，常量与变量类似也需要初始化，即在声明常量的同时要赋予一个初始值。常量一旦初始化就不可以被修改。

```java
final 数据类型 变量名 = 初始值;
```

final关键字表示最终的，它可以修改很多元素，修饰变量就变成了常量。

常量有三种类型：静态常量、成员常量和局部常量。

*    在很多情况下,程序员在使用符号常量的时候,只关心它的实际意义,并不关心它的具体值。

## 作用域

*    Java并未规定变量定义的具体位置,也就是说,程序员可以在需要使用变量的地方开始定义它,随后就可以使用它,直到包含该定义的方法结束为止,变量都是有效的。这个有效区域,称为变量的作用域。

# 规范

## 命名

命名方法很多，但是比较有名的且被广泛接受的命名法包括下面两种。

### 匈牙利命名

一般只是命名变量，原则是：变量名 = 类型前缀 + 描述，如bFoo表示布尔类型变
量，pFoo表示指针类型变量。匈牙利命名还是有一定争议的，在Java编码规范中基本不被采用。

### 驼峰命名

又称“骆驼命名法”，是指混合使用大小写字母来命名。驼峰命名又分为小驼峰法和大驼峰法。小驼峰法就是第一个单词是全部小写，后面的单词首字母大写

除了包和常量外，Java编码规范命名方法采用驼峰法

*    包名：包名是全小写字母，中间可以由点分隔开。作为命名空间，包名应该具有唯一性，推荐采用公司或组织域名的倒置，如com.apple.quicktime.v2但Java核心库包名不采用域名的倒置命名，如java.awt.event。
*    类和接口名：采用大驼峰法，如SplitViewController。
*    文件名：采用大驼峰法，如BlockOperation.java。
*    变量：采用小驼峰法，如studentNumber。
*    常量名：全大写，如果是由多个单词构成，可以用下划线隔开，如YEAR和WEEK_OF_MONTH。
*    方法名：采用小驼峰法，如balanceAccount、isButtonPressed等。

## 注释规范

Java中注释的语法有三种：单行注释（//）、多行注释（/* ...*/）和文档注释（/**... */）。

### 文件注释

文件注释就是在每一个文件开头添加注释。文件注释通常包括如下信息：版权信息、文件名、所在模块、作者信息、历史版本信息、文件内容和作用等。

### 文档注释

文档注释就是指这种注释内容能够生成API帮助文档，JDK中javadoc命令能够提取这些注释信息并生成HTML文件。文档注释主要对类（或接口）、实例变量、静态变量、实例方法和静态方法等进行注释。

文档是要给别人看的帮助文档，一般注释的实例变量、静态变量、实例方法和静态方法都应该是非私有的，那些只给自己看的内容可以不用文档注释。

| 标签        | 描述                       |
| ----------- | -------------------------- |
| @auther     | 说明类或接口的作者         |
| @deprecated | 说明类、接口或成员已经废弃 |
| @param      | 说明方法参数               |
| @return     | 说明返回值                 |
| @see        | 参考另一个主题的链接       |
| @exception  | 说明方法所抛出的异常类     |
| @throws     | 同@exception标签           |
| @version    | 类或接口的版本             |

### 代码注释

程序代码中处理文档注释还需要在一些关键的地方添加代码注释，文档注释一般是给一些看不到源代码的人看的帮助文档，而代码注释是给阅读源代码的人参考的。代码注释一般是采用单行注释（//）和多行注释（/*... */）。

## 代码排版

### 空行

用以将逻辑相关的代码段分隔开，以提高可读性。

01.	类声明和接口声明之间保留两个空行。
02.	两个方法之间保留一个空行。
03.	方法的第一条语句之前保留一个空行。
04.	代码注释（尾端注释外）之前保留一个空行。
05.	一个方法内的两个逻辑段之间。

### 空格

1.   赋值符号“=”前后各有一个空格。
2.   所有的二元运算符都应该使用空格与操作数分开。
3.   一元操作符：负号“-”、自增“++”和自减“--”等，它们与操作数之间没有空格。
4.   小左括号“(”之后，小右括号“)”之前不应有空格。
5.   大左括号“{”之前有一个空格。
6.   方法参数列表小左括号“(”之前没有空格，小右括号“)”之后有一个空格，参数列表中参数逗号“,”之后也有一个空格。
7.   关键字之后紧跟着小左括号“(”，关键字之后应该有一个空格。

### 缩进

1.   在方法、Lambda、控制语句等包含大括号“{}”的代码块中，代码块的内容相对于首行缩进一个级别（4个空格）。
2.   如果是if语句中条件表达式的断行，那么新的一行应该相对于上一行缩进两个级别（8个空格），再往后的断行要与第一次的断行对齐。

### 断行

一行代码的长度应尽量不要超过80个字符

01.	在一个逗号后面断开。
02.	在一个操作符前面断开，要选择较高级别的运算符（而非较低级别的运算符）断开。
03.	新的一行应该相对于上一行缩进两个级别（8个空格）。

### 其他规范

1.   在声明变量或常量时推荐一行一个声明。
2.   左大括号“{”位于声明语句同行的末尾。右大括号“}”另起一行，与相应的声明语句对齐，除非是一个空语句，右大括号“}”应紧跟在左大括号“{”之后。
3.   每行至多包含一条语句。
4.   虽然Java语言允许if、for等控制语句只有一行代码情况下，省略左右两个大括号，但是编码规范并不推荐这样使用。

# 数据

## 数据类型

*    与C/C++不同, Java中没有无符号型整数,而且明确规定了各种整型数据所占的内存字节数,这样就保证了平台无关性。

*    整数类型：byte、short、int和long
*    浮点类型：float和double
*    字符类型：char
*    布尔类型：boolean

### 整型类型

Java中整数类型包括：byte、short、int和long ，它们之间的区别仅仅是宽度和范围的不同。Java中整数都是有符号，与C不同没有无符号的整数类型。

Java的数据类型是跨平台的（与平台无关），无论你计算机是32位的还是64位的，byte类型整数都是一个字节（8位）。

| 整数类型 | 宽度   | 取值范围             |
| -------- | ------ | -------------------- |
| byte     | 8bits  | -128~127             |
| short    | 16bits | -$2^{15}$~$2^{15}-1$ |
| int      | 32bits | -$2^{31}$~$2^{31}-1$ |
| long     | 64bits | -$2^{63}$~$2^{63}-1$ |

### 浮点类型

浮点类型主要用来储存小数数值，也可以用来储存范围较大的整数。它分为浮点数（float）和双精度浮点数（double）两种，双精度浮点数所使用的内存空间比浮点数多

| 浮点类型 | 宽度   |
| -------- | ------ |
| float    | 32bits |
| double   | 64bits |

### 数字表示方式

*    二进制数：以 0b 或0B为前缀，注意0是阿拉伯数字，不要误认为是英文字母o。
*    八进制数：以0为前缀，注意0是阿拉伯数字。
*    十六进制数：以 0x 或0X为前缀，注意0是阿拉伯数字。
*    指数表示：进行数学计算时往往会用到指数表示的数值。如果采用十进制表示指数，需要使用大写或小写的e表示幂，e2表示${10}^2$。

### 字符类型

*    字符类型表示单个字符，Java中char声明字符类型，Java中的字符常量必须用单引号括起来的单个字符
*    Java字符采用双字节Unicode编码，占两个字节（16位），因而可用十六进制（无符号的）编码形式表示，它们的表现形式是\un，其中n为16位十六进制数，所以'A'字符也可以用Unicode编码'\u0041'表示

### 转义符

| 字符表示 | Unicode编码 | 说明          |
| -------- | ----------- | ------------- |
| \t       | \u0009      | 水平制表符TAB |
| \n       | \u000a      | 换行          |
| \r       | \u000d      | 回车          |
| \\"      | \u0022      | 双引号        |
| \\'      | \u0027      | 单引号        |
| \\\\     | \u005c      | 反斜线        |

### 布尔类型

在Java语言中声明布尔类型的关键字是boolean，它只有两个值：true和false。

提示　在C语言中布尔类型是数值类型，它有两个取值：1和0。而在Java中的布尔类型取值不能用1和0替代，也不属于数值类型，不能与int等数值类型之间进行数学计算或类型转化。

### 数值类型相互转换

#### 自动类型转换

char类型比较特殊，char自动转换为int、long、float和double，但byte和short不能自动转换为char，而且char也不能自动转换为byte或short。

| 操作数1类型                         | 操作数2类型 | 转换后的类型 |
| ----------------------------------- | ----------- | ------------ |
| byte、short、char                   | int         | int          |
| byte、short、char、int              | long        | long         |
| byte、short、char、int、long        | float       | float        |
| byte、short、char、int、long、float | double      | double       |

#### 强制类型转换

在数值类型转换过程中，除了需要自动类型转换外，有时还需要强制类型转换，强制类型转换是在变量或常量之前加上“(目标类型)”实现。

```java
[typename] name = ([typename]) object;
```

当大宽度数值转换为小宽度数值时，大宽度数值的高位被截掉，这样就会导致数据精度丢失。除非大宽度数值的高位没
有数据，就是这个数比较小的情况

### 引用数据类型

在Java中除了8种基本数据类型外，其他数据类型全部都是引用（reference）数据类型

包含：类、接口和数组声明的数据类型

Java中的引用数据类型，相当于C等语言中指针（pointer）类型，引用事实上就是指针，是指向一个对象的内存地址。引用数据类型变量中保持的是指向对象的内存地址。

## 数据结构

### 数组

#### 基本特性

01.	一致性：数组只能保存相同数据类型元素，元素的数据类型可以是任何相同的数据类型。
02.	有序性：数组中的元素是有序的，通过下标访问。
03.	不可变性：数组一旦初始化，则长度（数组中元素的个数）不可变。

在Java中数组的下标是从零开始的，事实上很多计算机语言的数组下标从零开始的。Java数组下标访问运算符是中括号

ava中的数组本身是引用数据类型，它的长度属性是length。数组可以分为：一维数组和多维数组

#### 一维数组

##### 一维数组声明

数组的声明就宣告这个数组中元素类型，数组的变量名。

```java
元素数据类型[] 数据变量名；
元素数据类型 数组变量名[];
```

可见数组的声明有两种形式：一种是两个中括号（[]）跟在元素数据类型之后；另一种是两个中括号（[]）跟在变量名之后。

```java
数组类型 数组名 [];
数组名 = new 数据类型 [数组长度];
```

```java
数据类型 数组名 [] = new 数据类型 [数组长度];
```

##### 数组初始化

声明完成就要对数组进行初始化，数组初始化的过程就是为数组每一个元素分配内存空间，并为每一个元素提供初始值。初始化之后数组的长度就确定下来不能再变化了。

数组初始化可以分为静态初始化和动态初始化。

###### 静态初始化

静态初始化就是将数组的元素放到大括号中，元素之间用逗号（,）分隔。

```java
数据类型 数组名[]= {值1,值2. ..,值n};
```

###### 动态初始化

动态初始化使用new运算符分配指定长度的内存空间

```java
new 元素数据类型[数组长度];
```

new分配数组内存空间后，数组中的元素内容是数组类型的默认值

| 基本类型 | 默认值    |
| -------- | --------- |
| byte     | 0         |
| short    | 0         |
| int      | 0         |
| long     | 0L        |
| float    | 0.0f      |
| double   | 0.0d      |
| char     | '\\u0000' |
| boolean  | false     |
| 引用     | null      |

#### 多维数组

当数组中每个元素又可以带有多个下标时，这种数组就是“多维数组”。

##### 二维数组声明

```cpp
元素数据类型[][] 数组变量名;
元素数据类型 数组变量名[][];
元素数据类型[] 数组变量名[];
```

##### 二维数组的初始化

###### 静态初始化

```java
元素数据类型 数组名称 [][]={{...},{...},...};
```

###### 动态初始化

```java
new 元素数据类型[高维数组长度][低维数组长度];
```

高维数组就是最外面的数组，低维数组是每一个元素的数组。

```java
int 名称[][];
名称 = new int[高维][];
名称[0] = new int[低维];
名称[1] = new int[低维];
名称[2] = new int[低维];
...
名称[高维-1] = new int[低维];
```

#### 不规则数组

先初始化高维数组，然后再分别逐个初始化低维数组。

>    下标越界异常（ArrayIndexOutOfBoundsException）是试图访问不存在的下标时引发的。例如一个一维array数组如果有10个元素，那么表达式array[10]就会发生下标越界异常，这是因为数组下标是从0开始的，最后一个元素下标是数组长度减1，所以array[10]访问的元素是不存在的。

不规则数组访问和遍历可以使用for和for-each循环，但要注意下标越界异常发生。

#### clone()

```java
数据类型 数组名1 [] = {数组成员};
数据类型 数组名2 [] = (数据类型 [])数组名1.clone(); 
```

#### 引用其他数组

```java
数据类型 [] 数组名1 = 数组名2；
```

这种方法实质上是增加了一个对数组名2的引用(有点类似于C中的指针),数组名1和数组名2指向了同一个数组,无论是通过数组名1还是数组名2对数组进行的操作,对另外一个都会造成影响。如果一个数组创建对象后,发现大小不符合要求,可以随时用new来调整大小,但之前存储的内容不会保留。

### 字符串

Java SE提供了三个字符串类：String、StringBuffer和StringBuilder。

String是不可变字符串， StringBuffer和StringBuilder是可变字符串。

空字符串不是null，空字符串是分配内存空间，而null是没有分配内存空间。

#### 不可变字符串

##### String

| 方法                                            | 说明                                                         |
| ----------------------------------------------- | ------------------------------------------------------------ |
| char  charAt(int index)                         | 返回指定位置的字符                                           |
| int  compareTo(String anotherString)            | 比较本字符串与anotherString中的字符串是否相等                |
| int  compareToIgnoreCase(String str)            | 同上，但忽略大小写                                           |
| String  concat(String str)                      | 将str加到本字符串的后面，返回新生成的字符串(本字符串并没有改变) |
| static  String copyValueOf(char[] data)         | 用字符型数组data的值生成一个String对象，并返回               |
| int  indexOf(int ch)                            | 返回字符ch在本字符串中出现的位置                             |
| int  indexOf(String str)                        | 返回字符串str在本字符串中出现的位置                          |
| int  length()                                   | 返回本字符串的长度                                           |
| String  replace(char oldChar, char newChar)     | 将本字符串的oldChar字符用newChar字符替代，返回新生成的字符串(本字符串并没有改变) |
| String  substring(int beginIndex, int endIndex) | 从本字符串的beginIndex位置开始到endIndex-1位置结束，截取一个子串，并返回该子串 |
| char[]  toCharArray()                           | 用本字符串生成一个字符型数组并返回                           |
| String  toLowerCase()                           | 将本字符串中的字符转换成小写，返回新生成的字符串(本字符串并没有改变) |
| String  toUpperCase()                           | 将本字符串中的字符转换成大写，返回新生成的字符串(本字符串并没有改变) |
| String  trim()                                  | 将本字符串的头、尾空格去掉，返回新生成的字符串               |


Java中不可变字符串类是String，属于java.lang包，它也是Java非常重要的类。

###### 构造方法

*    String()：使用空字符串创建并初始化一个新的String对象。
*    String(String original)：使用另外一个字符串创建并初始化一个新的 String 对象。
*    String(StringBuffer buffer)：使用可变字符串对象（StringBuffer）创建并初始化一个新的 String对象。
*    String(StringBuilder builder)：使用可变字符串对象（StringBuilder）创建并初始化一个新的String 对象。
*    String(byte[] bytes)：使用平台的默认字符集解码指定的byte数组，通过byte数组创建并初始化一个新的 String 对象。
*    String(char[] value)：通过字符数组创建并初始化一个新的 String 对象。
*    String(char[] value, int offset, int count)：通过字符数组的子数组创建并初始化一个新的 String 对象；offset参数是子数组第一个字符的索引，count参数指定子数组的长度。

```java
String 变量名;
```

###### 初始化

```java
String 变量名 = "[字符串]";
```

```java
String 变量名 = new String("[字符串]");
```

##### 字符串池

==运算符比较的是两个引用是否指向相同的对象

Java中的不可变字符串String常量，采用字符串池（String Pool）管理技术，字符串池是一种字符串驻留技术。

##### 去前后空格

*    String trim()：去前后空格，返回String

##### 字符串大小写转换

*    String toLowerCase()：将本字符串中的字符转换成小写字符，返回新生成的字符串(本字符串并没有发生变化)
*    String toUpperCase()：将本字符串中的字符转换成大写字符，返回新生成的字符串(本字符串并没有发生变化)

##### 返回指定位置字符

*    char charAt(int index)：返回定位置的字符

##### 字符型数组生成String对象

*    static String copyValueOf(char[] data)：用字符型数组data的值生成一个String对象,并返回

##### String对象生成字符型数组

*    char[] toCharArray()：用本字符串生成一个字符型数组并返回

##### 字符串拼接

String字符串虽然是不可变字符串，但也可以进行拼接只是会产生一个新的对象。

String字符串拼接可以使用+运算符或String的concat(String str)方法。+运算符优势是可以连接任何类型数据拼接成为字符串，而concat方法只能拼接String类型字符串。

*    String concat(String str)：将str加到本字符串的后面,返回新生成的字符串(注意:本字符串并没有变)

##### 字符串查找

在给定的字符串中查找字符或字符串是比较常见的操作。在String类中提供了indexOf和lastIndexOf方法用于查找字符或字符串，返回值是查找的字符或字符串所在的位置，-1表示没有找到。

*    int indexOf(char ch)：从前往后搜索字符ch，返回第一次找到字符ch所在处的索引。
*    int indexOf(char ch, int fromIndex)：从指定的索引开始从前往后搜索字符ch，返回第一次找到字符ch所在处的索引。
*    int indexOf(String str)：从前往后搜索字符串str，返回第一次找到字符串所在处的索引。
*    int indexOf(String str, int fromIndex)：从指定的索引开始从前往后搜索字符串str，返回第一次找到字符串所在处的索引。
*    int lastIndexOf(char ch)：从后往前搜索字符ch，返回第一次找到字符ch所在处的索引。
*    int lastIndexOf(char ch, int fromIndex)：从指定的索引开始从后往前搜索字符ch，返回第一次找到字符ch所在处的索引。
*    int lastIndexOf(String str)：从后往前搜索字符串str，返回第一次找到字符串所在处的索引。
*    int lastIndexOf(String str, int fromIndex)：从指定的索引开始从后往前搜索字符串str，返回第一次找到字符串所在处的索引。

##### 字符串替换

*    String replace(char oldChar, char newChar)：将本字符串的oldChar字符用newChar字符代替,返回新生成的字符串(注意:本字符串并没有变)

##### 字符串截取

*    String substring(int beginlndex, int endIndex)：从本字符串的beginIndex位置开始到endIndex-1位置结束,截取一个子串,并返回该子串

##### 字符串比较

###### 比较相等

*    boolean equals(Object anObject)：比较两个字符串中内容是否相等。
*    boolean equalsIgnoreCase(String anotherString)：类似equals方法，只是忽略大小写。

###### 比较大小

*    int compareTo(String anotherString)：按字典顺序比较两个字符串。如果参数字符串等于此字符串，则返回值 0；如果此字符串小于字符串参数，则返回一个小于 0 的值；如果此字符串大于字符串参数，则返回一个大于 0 的值。
*    int compareToIgnoreCase(String str)：类似compareTo，只是忽略大小写。

###### 比较前缀和后缀

*    boolean endsWith(String suffix)：测试此字符串是否以指定的后缀结束。 如果字符串以指定的前缀开始，则返回 true；否则返回 false。
*    boolean startsWith(String prefix)：测试此字符串是否以指定的前缀开始。如果字符串以指定的前缀开始，则返回 true；否则返回 false。

###### 字符串截取

*    String substring(int beginIndex)：从指定索引beginIndex开始截取一直到字符串结束的子字符串。
*    String substring(int beginIndex, int endIndex)：从指定索引beginIndex开始截取直到索引endIndex -1处的字符，注意包括索引为beginIndex处的字符，但不包括索引为endIndex处的字符。
*    String[] split(String regex)：根据给定正则表达式的匹配拆分此字符串。该方法的作用就像是使用给定的表达式和限制参数 0 来调用两参数 split方法。所得数组中不包括结尾空字符串。

#### 可变字符串

可变字符串在追加、删除、修改、插入和拼接等操作不会产生新的对象。

##### StringBuffer和StringBuilder

| 方法                                                  | 说明                                  |
| ----------------------------------------------------- | ------------------------------------- |
| StringBuffer  insert(int offset, String str)          | 将字符串str插入到本字符串指定的位置   |
| StringBuffer  append(String str)                      | 将字符串str追加到本字符串的末尾       |
| int  capacity()                                       | 返回本对象可以容纳的字符数目          |
| char  charAt(int index)                               | 返回index位置的字符                   |
| StringBuffer  delete(int start, int end)              | 删除掉从start到end位置的子字符串      |
| StringBuffer  deleteCharAt(int index)                 | 删除掉index位置的字符                 |
| int  length()                                         | 返回本对象中实际存储的字符数目        |
| StringBuffer  replace(int start, int end, String str) | 将从start到end位置的子字符串同str代替 |
| void  setCharAt(int index, char ch)                   | 将字符char填充到index位置             |


Java提供了两个可变字符串类StringBuffer和StringBuilder，中文翻译为“字符串缓冲区”。

StringBuffer是线程安全的，它的方法是支持线程同步 ，线程同步会操作串行顺序执行，在单线程环境
下会影响效率。StringBuilder是StringBuffer单线程版本，Java 5之后发布的，它不是线程安全的，但它的执行效率很高。

>    线程同步是一个多线程概念，就是当多个线程访问一个方法时，只能由一个优先级别高的线程先访问，在访问期间会锁定该方法，其他线程只能等到它访问完成释放锁，才能访问。

StringBuffer和StringBuilder具有完全相同的API，即构造方法和普通方法等内容一样。

###### 构造方法

*    StringBuilder()：创建字符串内容是空的StringBuilder对象，初始容量默认为16个字符。
*    StringBuilder(CharSequence seq)：指定CharSequence字符串创建StringBuilder对象。CharSequence接口类型，它的实现类有：String、StringBuffer、StringBuilder等，所以参数seq可以是String、 StringBuffer和StringBuilder等类型。
*    StringBuilder(int capacity)：创建字符串内容是空的StringBuilder对象，初始容量由参数capacity指定的。
*    StringBuilder(String str)：指定String字符串创建StringBuilder对象。

>    字符串长度和字符串缓冲区容量区别。字符串长度是指在字符串缓冲区中目前所包含字符串长度，通过length()获得；字符串缓冲区容量是缓冲区中所能容纳的最大字符数，通过capacity()获得。当所容纳的字符超过这个长度时，字符串缓冲区自动扩充容量，但这是以牺牲性能为代价的扩容。

###### 返回指定位置字符

*    char charAt(int index)：返回index位置的字符

###### 字符串追加

*    append()：StringBuilder的追加法与StringBuffer完全一样。

###### 插入

*    StringBuilder insert(int offset, String str)：在字符串缓冲区中索引为offset的字符位置之前插入str， insert有很多重载方法，可以插入任何类型数据。

###### 删除

*    StringBuffer delete(int start, int end)：在字符串缓冲区中删除子字符串，要删除的子字符串从指定索引start开始直到索引end - 1处的字符。start和end两个参数与substring(int beginIndex, int endIndex)方法中的两个参数含义一样。
*    StringBuffer deleteCharAt(int index)：删除掉index位置的字符

###### 替换

*    StringBuffer replace(int start, int end, String str)字符串缓冲区中用str替换子字符串，子字符串从指定索引start开始直到索引end - 1处的字符。start和end同delete(int start, int end)方法。

###### 填充

*    void setCharAt(int index,char ch)：将字符char填充到index位置

###### StringBuilder转String

*    StringBuilder toString()：StringBuilder转String

### Collection接口

Java库中用于集合类的基本接口是Collection接口,该接口用于表示任何对象或元素组。想要尽可能以常规方式处理一组元素时,就使用这一接口。Collection支持如添加和移除等基本操作。设法除去一个元素时,如果这个元素存在,除去的仅仅是集合中此元素的个实例。两个基本操作方法为:

*    boolean add(Object element):添加元素到集合中
*    boolean remove(Object element):从集合中删除元素
*    int size():返回集合中元素的数目
*    boolean isEmpty):判断集合是否为空
*    boolean contains(Object obj):如果集合中包含了一个obj对象,则返回true
*    boolean containsAll(Collection c):如果集合中包含了c中所有的元素,则返回true
*    boolean equals(Object other):如果集合相等则返回true
*    boolean addAll(Collection from):将from中的所有元素添加到集合中,成功则返回true
*    boolean remove(Object obj):删除元素obj,成功则返回true
*    boolean removeAll(Collection c):删除集合中所有与c中相同的元素,只要集合发生变化则返回true
*    void clear():将本集合清空
*    boolean retainAll(Collection c):删除集合中所有不在c中的元素,只要集合发生变化则返回true
*    Object [] toArray[]:返回集合中所有元素组成的数组

不过,如果实现Collection的每个类都要提供这么多方法,那将是一件很麻烦的事情。为了减轻程序员的工作量,系统用一个AbstractCollection类来实现这个接口,程序员可以直接继承这个类。由于接口中的方法都已经实现,只有少数几个可能要根据需要来修改,这样就大大减少了重复劳动。

*    Iterator iterator():该方法用于返回一个能够实现Iterator接口的对象,此对象也被称为迭代器。程序员可以使用这个迭代对象,逐个访问集合中的各个元素。它有下面3个基本方法:
     *    Object next();通过反复调用next()方法,可以逐个访问集合中的各个元素。但是如果到了集合的末尾,那么next()方法将抛出一个NoSuchElementException异常。因此,在调用next()方法之前,必须先调用hasNext()方法进行测试。如果测试的对象仍然拥有可供访问的元素,那么hasNext()将返回true
     *    boolean hasNext();
     *    void remove();使用remove()方法必须要小心。在调用remove()方法时,删除的是上次调用next()返回的元素。如果你要删除某个位置上的元素,首先要跳过这个元素

```java
Iterator it = c.iterator();
it.next ();//越过第一个元素
it.remove (); //删除它
```

>    由于remove()和next()方法是互相关联的,在调用remove()方法之前,至少要保证调用了一次next()方法,否则将会抛出一个IlegalStateException异常。

### List集合

*    List接口继承自Collection接口，List接口中的很多方法都继承自Collection接口的。
*    List接口的实现类有：ArrayList 和 LinkedList。ArrayList是基于动态数组数据结构的实现，LinkedList是基于链表数据结构的实现。ArrayList访问元素速度优于LinkedList，LinkedList占用的内存空间比较大，但LinkedList在批量插入或删除数据时优于ArrayList。
     *    ArrayList:一个用数组实现的List。能进行快速的随机访问,但是往列表中间插入和删除元素的时候比较慢。Listlterator只能用在反向遍历ArrayList的场合,不要用它来插入和删除元素,因为相比LinkedList,在ArrayList里面用Listlterator的系统开销比较高。
     *    LinkedList:对顺序访问进行了优化。在List中间插入和删除元素的代价也不高。随机访问的速度相对较慢。此外它还有addFirst(), addLast(), getFirst()、 getLast(),removeFirst)和removeLast()等方法,在实际应用中,根据方法的具体实现,可以把LinkedList当成栈(stack) 、队列(queue)或双向队列(deque)来用。
*    两个抽象的List实现类: AbstractList和AbstractSequentialList
     *    像AbstractSet类一样,它们覆盖了equals()和hashCode()方法以确保两个相等的集合返回相同的散列码。若两个集大小相等且包含顺序相同的相同元素,则这两个集相等。这里的hashCode()实现,在List接口定义中指定,而在抽象类中实现。除了equals()和hashCode()实现, AbstractList和AbstractSequentialList实现了其余List方法的一部分。因为数据源随机访问和顺序访问是分别实现的,使得具体列表实现的创建更为容易。

```java
List list=new ArrayList();			// ArrayList
List list=new LinkedList();			// LinkedList
```

#### 操作元素

*    get(int index)：返回List集合中指定位置的元素。
*    set(int index, Object element)：用指定元素替换List集合中指定位置的元素。
*    add(Object element)：在List集合的尾部添加指定的元素。该方法是从Collection集合继承过来的。
*    add(int index, Object element)：在List集合的指定位置插入指定元素。
*    remove(int index)：移除List集合中指定位置的元素。
*    remove(Object element)：如果List集合中存在指定元素，则从List集合中移除第一次出现的指定元素。该方法是从Collection集合继承过来的。
*    clear()：从List集合中移除所有元素。该方法是从Collection集合继承过来的。

#### 判断元素

*    isEmpty()：判断List集合中是否有元素，没有返回true，有返回false。该方法是从Collection集合继承过来的。
*    contains(Object element)：判断List集合中是否包含指定元素，包含返回true，不包含返回false。该方法是从Collection集合继承过来的。

#### 查询元素

*    indexOf(Object o)：从前往后查找List集合元素，返回第一次出现指定元素的索引，如果此列表不包含该元素，则返回-1。
*    lastIndexOf(Object o)：从后往前查找List集合元素，返回第一次出现指定元素的索引，如果此列表不包含该元素，则返回-1。

#### 迭代器

*    iterator()：返回迭代器（Iterator）对象，迭代器对象用于遍历集合。该方法是从Collection集合继承过来的。

#### 元素数

*    size()：返回List集合中的元素数，返回值是int类型。该方法是从Collection集合继承过来的。

#### 子集合

*    subList(int fromIndex, int toIndex)：返回List集合中指定的 fromIndex（包括 ）和toIndex（不包括）之间的元素集合，返回值为List集合。

#### 遍历集合

##### 方法

*    使用for循环遍历：List集合可以使用for循环进行遍历，for循环中有循环变量，通过循环变量可以访问List集合中的元素。
*    使用for-each循环遍历：for-each循环是针对遍历各种类型集合而推出的，笔者推荐使用这种遍历方法。
*    使用迭代器遍历：Java提供了多种迭代器，List集合可以使用Iterator和ListIterator迭代器。

```java
for(Object item:list){
    type name=(type)item;
}
```

```java
Iterator pos = list.iterator();
while (pos.hasNext()) {

    type item = (type) pos.next();
    System.out.println(item);
}
```

### Set集合

>    List集合中的元素是有序的、可重复的，而Set集合中的元素是无序的、不能重复的。List集合强调的是有序，Set集合强调的是不重复。当不考虑顺序，且没有重复元素时，Set集合和List集合可以互相替换的。

*    Set接口继承Collection接口,而且它不允许集合中存在重复项
*    所有原始方法都是现成的,没有引入新方法。具体的Set实现类依赖添加的对象的equals()方法来检查等同性
*    Set接口有两个具体的实现类,分别为HashSet和TreeSet
*    HashSet是为优化查询速度而设计的Set,添加到HashSet的对象需要采用恰当分配散列码的方式来实现hashCode()方法。虽然大多数系统类覆盖了Object中默认的hashCode()实现,但当编程中需要创建自己的要添加到HashSet的类时,需要覆盖hashCode()
*    TreeSet是一个有序的Set,其底层是一棵树,添加到TreeSet的元素也必须是可排序的,这样在使用时就能从Set里面提取一个有序序列了。一般来说,先把元素添加到HashSet,再把集合转换为TreeSet来进行有序遍历会更快。HashSet和TreeSet都实现了Cloneable接口
*    AbstractSet类覆盖了equals()和hashCode()方法,以确保两个相等的集返回相同的散列码。若两个集大小相等且包含相同元素,则这两个集相等。按定义,集散列码是集中元素散列码的总和。因此,不论集的内部顺序如何,两个相等的集会返回相同的散列码
*    Set接口也继承自Collection接口，Set接口中大部分都是继承自Collection接口。
*    Set接口直接实现类主要是HashSet，HashSet是基于散列表数据结构的实现。

```java
Set set=new HashSet();
```

#### 操作元素

*    add(Object element)：在Set集合的尾部添加指定的元素。该方法是从Collection集合继承过来的。
*    remove(Object element)：如果Set集合中存在指定元素，则从Set集合中移除该元素。该方法是从Collection集合继承过来的。
*    clear()：从Set集合中移除所有元素。该方法是从Collection集合继承过来的。

#### 判断元素

*    isEmpty()：判断Set集合中是否有元素，没有返回true，有返回false。该方法是从Collection集合继承过来的。
*    contains(Object element)：判断Set集合中是否包含指定元素，包含返回true，不包含返回false。该方法是从Collection集合继承过来的。

#### 迭代器

*    iterator()：返回迭代器（Iterator）对象，迭代器对象用于遍历集合。该方法是从Collection集合继承过来的。

#### 元素数

*    size()：返回Set集合中的元素数，返回值是int类型。该方法是从Collection集合继承过来的。

#### 遍历

*    Set集合中的元素由于没有序号，所以不能使用for循环进行遍历，但可以使用for-each循环和迭代器进行遍历。

```java
for(Object item:list){
    type name=(type)item;
}
```

```java
Iterator pos = list.iterator();
while (pos.hasNext()) {

    type item = (type) pos.next();
    System.out.println(item);
}
```

### Map集合

*    Map（映射）集合表示一种非常复杂的集合，允许按照某个键来访问元素。
*    Map集合是由两个集合构成的，一个是键（key）集合，一个是值（value）集合。
*    键集合是Set类型，因此不能有重复的元素。而值集合是Collection类型，可以有重复的元素。Map集合中的键和值是成对出现的。
*    Map接口直接实现类主要是HashMap，HashMap是基于散列表数据结构的实现。

#### 操作元素

*    get(Object key)：返回指定键所对应的值；如果Map集合中不包含该键值对，则返回null。
*    put(Object key, Object value)：指定键值对添加到集合中。
*    remove(Object key)：移除键值对。
*    clear()：移除Map集合中所有键值对。

#### 判断元素

*    isEmpty()：判断Map集合中是否有键值对，没有返回true，有返回false。
*    containsKey(Object key)：判断键集合中是否包含指定元素，包含返回true，不包含返回false。
*    containsValue(Object value)：判断值集合中是否包含指定元素，包含返回true，不包含返回false。

#### 查看集合

*    keySet()：返回Map中的所有键集合，返回值是Set类型。
*    values()：返回Map中的所有值集合，返回值是Collection类型。
*    size()：返回Map集合中键值对数。

#### Map.Entry

##### 获得Map.Entry

*    entrySet()：返回Map.Entry

##### Map.Entry方法

*    getKey()：获取键
*    getValue()：获取值

#### 遍历

*    Map集合遍历与List和Set集合不同，Map有两个集合，因此遍历时可以只遍历值的集合，也可以只遍历键的集合，也可以同时遍历。这些遍历过程都可以使用for-each循环和迭代器进行遍历。

```java
Iterator pos=map.entrySet().iterator();
while(pos.hasNext()){
    
    Map.Entry entry=(Map.Entry)pos.next();
    
    type key= (type) entry.getKey();
    type value=(type)entry.getValue();
    
    // TODO:System.out.println(key+":"+value);
}
```

```java
for (Map.Entry<Character, Integer> entry : map.entrySet()) {
            
    System.out.println(entry.getKey() + " " + entry.getValue());
}
```

# 运算符

## 算术运算符

### 一元运算符

| 运算符 | 名称     | 说明                         | 例子        |
| ------ | -------- | ---------------------------- | ----------- |
| -      | 取反符号 | 取反运算                     | b = -a      |
| ++     | 自加一   | 先取值再加一，或先加一再取值 | a++或++a    |
| - -    | 自减一   | 先取值再减一，或先减一再取值 | a- -或- - a |

### 二元运算符

| 运算符 | 名称 | 说明                                               | 例子 |
| ------ | ---- | -------------------------------------------------- | ---- |
| +      | 加   | 求a加b的和，还可用于String类型，进行字符串连接操作 | a+b  |
| -      | 减   | 求a减b的差                                         | a-b  |
| **     | 乘   | 求a乘以b的积                                       | a*b  |
| /      | 除   | 求a除以b的商                                       | a/b  |
| %      | 取余 | 求a除以b的余数                                     | a%b  |

## 算术赋值运算符

| 运算符 | 名称     | 例子         |
| ------ | -------- | ------------ |
| +=     | 加赋值   | a+=b、a+=b+3 |
| -=     | 减赋值   | a-=b         |
| *=     | 乘赋值   | a*=b         |
| /=     | 除赋值   | a/=b         |
| %=     | 取余赋值 | a%=b         |

## 关系运算符

| 运算符 | 名称     | 说明                                | 例子   |
| ------ | -------- | ----------------------------------- | ------ |
| ==     | 等于     | a等于b时返回true，否则返回false     | a == b |
| !=     | 不等于   | 与==相反                            | a != b |
| >      | 大于     | a大于b时返回true，否则返回false     | a > b  |
| <      | 小于     | a小于b时返回true，否则返回false     | a < b  |
| >=     | 大于等于 | a大于等于b时返回true，否则返回false | a >= b |
| <=     | 小于等于 | a小于等于b时返回true，否则返回false | a <= b |

## 逻辑运算符

| 运算符 | 名称   | 说明                                                         |        |
| ------ | ------ | ------------------------------------------------------------ | ------ |
| !      | 逻辑非 | a为true时,值为false , a为false时,值为true                    | !a     |
| &      | 逻辑与 | ab全为true时,计算结果为true,否则为false                      | a&b    |
| \|     | 逻辑或 | ab全为false时,计算结果为false ,否则为true                    | a\|b   |
| &&     | 短路与 | ab全为true时，计算结果为true，否则为false。&&与&区别：如果a为false，则不计算b | a&&b   |
| \|\|   | 短路或 | ab全为false时，计算结果为false，否则为true。\|\|与\|区别：如果a为true，则不计算b | a\|\|b |

## 位运算符

| 运算符 | 名称       | 例子   | 说明                         |
| ------ | ---------- | ------ | ---------------------------- |
| ~      | 位反       | ~x     | 将x的值按位取反              |
| &      | 位与       | x&y    | x与y位进行位与运算           |
| \|     | 位或       | x\|y   | x与y位进行位或运算           |
| ^      | 位异或     | x^a    | x与y位进行位异或运算         |
| >>     | 有符号右移 | x>>a   | x右移a位，高位采用符号位补位 |
| <<     | 左移       | x<<a   | x左移a位，低位用0补位        |
| >>>    | 无符号右移 | a>>>b  | x右移a位，高位用0补位        |
| &=     | 位与等于   | a&=b   | 等价于a=a&b                  |
| \|=    | 位或等于   | a\|=b  | 等价于a=a\|b                 |
| ^=     | 位异或等于 | a^=b   | 等价于a=a^b                  |
| <<=    | 左移等于   | a<<=b  | 等价于a=a<<b                 |
| >>=    | 右移等于   | a>>=b  | 等价于a=a>>b                 |
| >>>=   | 右移等于   | a>>>=b | 等价于a=a>>>b                |

## 其他运算符

*    三元运算符（? :）。例如x?y:z;，其中x、y和z都为表达式。
*    小括号。起到改变表达式运算顺序的作用，它的优先级最高。
*    中括号。数组下标。
*    引用号（.）。对象调用实例变量或实例方法的操作符，也是类调用静态变量或静态方法的操作符。
*    赋值号（=）。赋值是用等号运算符（=）进行的。
*    instanceof。判断某个对象是否为属于某个类。
*    new。对象内存分配运算符。
*    箭头（->）。Java 8新增加的，用来声明Lambda表达式。
*    双冒号（::）。Java 8新增加的，用于Lambda表达式中方法的引用。

# 控制语句

## 分支语句

### if-else if-else语句

```java
if(条件表达式){
	// TODO
}else if(条件表达式2){
	// TODO
}else{
	// TODO
}
```

### switch语句

```java
switch(表达式){
    case value1:
        // TODO
    case value2:
        // TODO
    default:
        // TODO
}
```

## 循环语句

### while语句

```java
while(循环条件){
    // TODO
}
```

### do-while语句

```java
do{
    // TODO
}while(循环条件);
```

### for语句

```java
for(初始化;循环条件;迭代){
    // TODO
}
```

### for-each语句

*    遍历集合

```java
for([typename] item: [container]){
    // TODO
}
```

## 跳转语句

### break语句

break语句可用于上一节介绍的while、repeat-while和for循环结构，它的作用是强行退出循环体，不再执行循环体中剩余的语句。

```java
break;			// 不带标签
break label;	// 带标签
```

### continue语句

continue语句用来结束本次循环，跳过循环体中尚未执行的语句，接着进行终止条件的判断，以决定是否继续循环。对于for语句，在进行终止条件的判断前，还要先执行迭代语句。

```java
continue;			// 不带标签
continue label;		// 带标签
```

# 面向对象

面向对象的编程思想：按照真实世界客观事物的自然规律进行分析，客观世界中存在什么样的实体，构建的软件系统就存在什么样的实体。

## 面向对象三个基本特性

面向对象思想有三个基本特性：封装性、继承性和多态性。

### 封装性

封装能够使外部访问者不能随意存取对象的内部数据，隐藏了对象的内部细节，只保留有限的对外接口。

外部访问者不用关心对象的内部细节，使得操作对象变得简单。

### 继承性

在Java语言中一般类称为“父类”，特殊类称为“子类”。

Java语言是单继承的，即只能有一个父类，但Java可以实现多个接口，可以防止多继承所引起的冲突问题。

### 多态性

多态性是指在父类中成员变量和成员方法被子类继承之后，可以具有不同的状态或表现行为。

## 类

类是Java中的一种重要的引用数据类型，是组成Java程序的基本要素。它封装了一类对象的数据和操作。

### Class

| <U> 类<?  extends U> asSubclass(类<U> clazz)                 | 类这个 类对象来表示由指定的类对象表示的类的子类。            |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| T cast(Object obj)                                           | 施放一个目的是通过本表示的类或接口 类对象。                  |
| boolean desiredAssertionStatus()                             | 如果要在调用此方法时初始化该类，则返回将分配给此类的断言状态。 |
| static 类<?>  forName(String className)                      | 返回与给定字符串名称的类或接口相关联的 类对象。              |
| static 类<?>  forName(String name,  boolean initialize, ClassLoader loader) | 使用给定的类加载器返回与给定字符串名称的类或接口相关联的 类对象。 |
| AnnotatedType[] getAnnotatedInterfaces()                     | 返回一个 AnnotatedType对象的数组， AnnotatedType使用类型指定由此 AnnotatedType对象表示的实体的超级 类 。 |
| AnnotatedType getAnnotatedSuperclass()                       | 返回一个 AnnotatedType对象，该对象表示使用类型来指定由此 类对象表示的实体的 类类。 |
| <A extends Annotation>  getAnnotation(类<A> annotationClass) | 返回该元素的，如果这样的注释 ，否则返回null指定类型的注释。  |
| Annotation[] getAnnotations()                                | 返回此元素上 存在的注释。                                    |
| <A extends Annotation>  getAnnotationsByType(类<A> annotationClass) | 返回与此元素相关 联的注释 。                                 |
| String getCanonicalName()                                    | 返回由Java语言规范定义的基础类的规范名称。                   |
| 类<?>[] getClasses()                                         | 返回包含一个数组 类表示所有的公共类和由此表示的类的成员接口的对象 类对象。 |
| ClassLoader getClassLoader()                                 | 返回类的类加载器。                                           |
| 类<?> getComponentType()                                     | 返回 类数组的组件类型的Class。                               |
| Constructor<T>  getConstructor(类<?>... parameterTypes)      | 返回一个 Constructor对象，该对象反映 Constructor对象表示的类的指定的公共 类函数。 |
| Constructor<?>[] getConstructors()                           | 返回包含一个数组 Constructor对象反射由此表示的类的所有公共构造 类对象。 |
| <A extends Annotation>  getDeclaredAnnotation(类<A> annotationClass) | 如果这样的注释 直接存在 ，则返回指定类型的元素注释，否则返回null。 |
| Annotation[] getDeclaredAnnotations()                        | 返回 直接存在于此元素上的注释。                              |
| <A extends Annotation>  getDeclaredAnnotationsByType(类<A> annotationClass) | 如果此类注释 直接存在或 间接存在，则返回该元素的注释（指定类型）。 |
| 类<?>[] getDeclaredClasses()                                 | 返回一个反映所有被这个 类对象表示的类的成员声明的类和 类对象的数组。 |
| Constructor<T>  getDeclaredConstructor(类<?>... parameterTypes) | 返回一个 Constructor对象，该对象反映 Constructor对象表示的类或接口的指定 类函数。 |
| Constructor<?>[]  getDeclaredConstructors()                  | 返回一个反映 Constructor对象表示的类声明的所有 Constructor对象的数组 类 。 |
| Field getDeclaredField(String name)                          | 返回一个 Field对象，它反映此表示的类或接口的指定已声明字段 类对象。 |
| Field[] getDeclaredFields()                                  | 返回的数组 Field对象反映此表示的类或接口声明的所有字段 类对象。 |
| 方法  getDeclaredMethod(String name, 类<?>... parameterTypes) | 返回一个 方法对象，它反映此表示的类或接口的指定声明的方法 类对象。 |
| 方法[] getDeclaredMethods()                                  | 返回包含一个数组 方法对象反射的类或接口的所有声明的方法，通过此表示 类对象，包括公共，保护，默认（包）访问和私有方法，但不包括继承的方法。 |
| 类<?> getDeclaringClass()                                    | 如果由此 类对象表示的类或接口是另一个类的成员，则返回表示其声明的类的 类对象。 |
| 类<?> getEnclosingClass()                                    | 返回底层类的即时封闭类。                                     |
| Constructor<?>  getEnclosingConstructor()                    | 如果此类对象表示构造函数中的本地或匿名类，则返回表示底层类的立即封闭构造函数的Constructor对象。 |
| 方法 getEnclosingMethod()                                    | 如果此类对象表示方法中的本地或匿名类，则返回表示基础类的即时封闭方法的方法对象。 |
| T[] getEnumConstants()                                       | 返回此枚举类的元素，如果此Class对象不表示枚举类型，则返回null。 |
| Field getField(String name)                                  | 返回一个 Field对象，它反映此表示的类或接口的指定公共成员字段 类对象。 |
| Field[] getFields()                                          | 返回包含一个数组 Field对象反射由此表示的类或接口的所有可访问的公共字段 类对象。 |
| Type[] getGenericInterfaces()                                | 返回 Type表示通过由该对象所表示的类或接口直接实现的接口秒。  |
| Type getGenericSuperclass()                                  | 返回 Type表示此所表示的实体（类，接口，基本类型或void）的直接超类 类 。 |
| 类<?>[] getInterfaces()                                      | 确定由该对象表示的类或接口实现的接口。                       |
| 方法  getMethod(String name, 类<?>... parameterTypes)        | 返回一个 方法对象，它反映此表示的类或接口的指定公共成员方法 类对象。 |
| 方法[] getMethods()                                          | 返回包含一个数组 方法对象反射由此表示的类或接口的所有公共方法 类对象，包括那些由类或接口和那些从超类和超接口继承的声明。 |
| int getModifiers()                                           | 返回此类或接口的Java语言修饰符，以整数编码。                 |
| String getName()                                             | 返回由 类对象表示的实体（类，接口，数组类，原始类型或空白）的名称，作为 String 。 |
| 软件包 getPackage()                                          | 获取此类的包。                                               |
| ProtectionDomain getProtectionDomain()                       | 返回 ProtectionDomain 。                                     |
| URL getResource(String name)                                 | 查找具有给定名称的资源。                                     |
| InputStream  getResourceAsStream(String name)                | 查找具有给定名称的资源。                                     |
| Object[] getSigners()                                        | 获得这个类的签名者。                                         |
| String getSimpleName()                                       | 返回源代码中给出的基础类的简单名称。                         |
| 类<? super T> getSuperclass()                                | 返回 类表示此所表示的实体（类，接口，基本类型或void）的超类 类 。 |
| String getTypeName()                                         | 为此类型的名称返回一个内容丰富的字符串。                     |
| TypeVariable<类<T>>[]  getTypeParameters()                   | 返回一个 TypeVariable对象的数组，它们以声明顺序表示由此 GenericDeclaration对象表示的通用声明声明的类型变量。 |
| boolean isAnnotation()                                       | 如果此 类对象表示注释类型，则返回true。                      |
| boolean isAnnotationPresent(类<?  extends Annotation> annotationClass) | 如果此元素上 存在指定类型的注释，则返回true，否则返回false。 |
| boolean isAnonymousClass()                                   | 返回 true当且仅当基础类是匿名类时。                          |
| boolean isArray()                                            | 确定此 类对象是否表示数组类。                                |
| boolean  isAssignableFrom(类<?> cls)                         | 确定由此 类对象表示的类或接口是否与由指定的Class 类表示的类或接口相同或是超类或 类接口。 |
| boolean isEnum()                                             | 当且仅当该类在源代码中被声明为枚举时才返回true。             |
| boolean isInstance(Object obj)                               | 确定指定的Object是否与此 Object表示的对象分配 类 。          |
| boolean isInterface()                                        | 确定指定 类对象表示接口类型。                                |
| boolean isLocalClass()                                       | 返回 true当且仅当基础类是本地类时。                          |
| boolean isMemberClass()                                      | 返回 true当且仅当基础类是成员类时。                          |
| boolean isPrimitive()                                        | 确定指定 类对象表示一个基本类型。                            |
| boolean isSynthetic()                                        | 如果这个类是一个合成类，返回true ; 返回false其他。           |
| T newInstance()                                              | 创建由此 类对象表示的类的新实例。                            |
| String toGenericString()                                     | 返回描述此 类的字符串，包括有关修饰符和类型参数的信息。      |
| String toString()                                            | 将对象转换为字符串。                                         |

### 类声明

Java语言中一个类的实现包括：类声明和类体。

```java
[public][abstract|final] class className [extends superclassName][implements interfaceNameList]{
    // TODO
}
```

*    class是声明类的关键字
*    className是自定义的类名
*    class前面的修饰符public、abstract、final用来声明类，它们可以省略
*    superclassName为父类名，可以省略，如果省略则该类继承Object类，Object类所有类的根类，所有类都直接或间接继承Object
*    interfaceNameList是该类实现的接口列表，可以省略，接口列表中的多个接口之间用逗号分隔。

### 构造方法

构造方法是类中一种特殊的方法,它一般由系统在创建对象(即类实例化)时自动调用。构造方法是对象中第一个被执行的方法,主要用于申请内存以及对类的成员变量进行初始化等操作。构造方法虽然也位于类里面,但在很多情况下与普通成员方法表现不同,所以也有人认为它不是成员方法,而且将其称为“构造器”。

#### 一般形式(不带参数)

有些人认为不带参数的构造方法能够被子类自动继承。但实际上,这种继承与普通方法的继承本质上并不相同,它其实是一种自动调用。

```java
构造方法名([参数列表]){
    [this ([参数列表])]|[super ([参数列表])];
    语句序列
}
```

注意

*    构造方法的名字必须和类的名字完全相同。
*    除了访问权修饰符之外,不能有其他任何修饰符,也就不能有返回值。
*    尽管没有返回值,但并不能用void修饰。
*    构造方法不能用static和final来修饰。一般也不用private修饰,这会导致无法在外部创建对象。
*    构造方法不能由对象显式地调用。
*    不能被static, final, synchronized, abstract和native修饰。
*    一般通过new关键字来调用,或者用this和super来调用。
*    构造方法的参数列表可以为空,也可以有参数。根据参数的有无,可以将构造方法分为无参数的构造方法和带参数的构造方法。
*    用户定义的类可以拥有多个构造方法,但要求参数列表不同。
*    当用户定义的类未提供任何构造方法时,系统会自动为其提供一个无参数的构造方法。

#### 带参数(构造方法重载)

在很多时候,需要根据不同的情况为成员变量赋不同的初值,这就需要传递参数给构造方法。因此, Java中允许定义带参数的构造方法,而且这种带参数的构造方法还可以定义多个(前提是参数列表有区别) ,这种现象被称为构造方法的重载。

Java规定,如果程序员一个构造方法都不定义,那么系统会自动为其加上一个不带参数的构造方法。如果程序员至少定义了一个构造方法,那么系统不会再提供不带参数的构造方法。

带参数的构造方法,不会由子类继承,也不会自动调用。

当用new来创建对象时,需要提供类型相容的参数,否则编译器将报错。

##### 无参数构造方法的覆盖

构造方法在覆盖时,只可能是访问权限不同,而且它遵循普通方法的规则,只允许访问权限更宽松。Java还规定,子类中无论当哪个构造方法在执行时,都会先执行父类中无参数的构造方法。

##### this关键字和构造方法的调用

this关键字还有一个作用,就是用来显示地调用构造方法。

```java
this ([参数列表])
```

系统将根据参数列表来决定调用哪一个构造方法。

注意

*    用this调用构造方法时,该语句只能用在构造方法中。
*    this语句必须是构造方法中的第一条语句。
*    和new不同, this虽然可以调用构造方法,但它只是执行构造方法中的语句,并不会创建对象。

##### super引用父类成员

子类的变量和方法都可以和父类中的同名。在这种情况下,父类中的同名成员就被屏蔽起来-注意仅仅只是屏蔽,而不是清除。如果想在子类中访问父类,的成员,就需要用到关键字super。

###### 一般用法

```cpp
super.变量名
super.方法名([参数列表])
```

##### 使用super调用父类的构造方法

前面已经说过,子类的构造方法会自动调用父类不带参数的构造方法,但是不会调用·带参数的构造方法。如果子类确实有必要调用父类带参数的构造方法,就必须使用super关键字来实现。

###### 一般用法

```cpp
super([参数列表])
```

###### 用法

*    它只能用在构造方法中。
*    它只能是第一条执行语句一个构造方法中只能有一条super语句。

### 成员变量

```java
class className{
    [public|protected|private][static][final] type variableName;// 成员变量
}
```

其中type是成员变量数据类型，variableName是成员变量名。type前的关键字都是成员变量修饰符

#### 访问权限

public、protected和private修饰符用于封装成员变量。

static修饰符用于声明静态变量，所以静态变量也称为“类变量”。

final修饰符用于声明变量，该变量不能被修改。

### 成员方法

```java
class className{
     [public | protected | private ] [static] [final | abstract] [native] [synchronized] type methodname([paramList])[throws exceptionList]{
         
         [memberVariableDeclarations]// 定义成员变量
         [constructorDeclarations]// 定义构造方法
         [methodDeclarations]// 定义成员方方法
     }
}
```

其中type是方法返回值数据类型，methodName是方法名。type前的关键字都是方法修饰符

*    public、protected和private修饰符用于封装方法。
*    static修饰符用于声明静态方法，所以静态方法也称为“类方法”。
*    final | abstract不能同时修饰方法，final修饰的方法不能在子类中被覆盖；abstract用来修饰抽象方法，抽象方法必须在子类中被实现。
*    native修饰的方法，称为“本地方法”，本地方法调用平台本地代码（如：C或C++编写的代码），不能实现跨平台。
*    synchronized修饰的方法是同步的，当多线程方式同步方法时，只能串行地执行，保证是线程安全的。

#### 方法的访问权限

<table>
    <tr><th></th><th>public</th><th>protected</th><th>默认</th><th>private</th></tr>
    <tr><th>本类内部</th><th>√</th><th>√</th><th>√</th><th>√</th></tr>
    <tr><th>同一包中的子类</th><th>√</th><th>√</th><th>√</th><th>×</th></tr>
    <tr><th>同一包中非子类</th><th>√</th><th>√</th><th>√</th><th>×</th></tr>
    <tr><th>不同包中的子类</th><th>√</th><th>继承访问</th><th>×</th><th>×</th></tr>
    <tr><th>不同包中非子类</th><th>√</th><th>×</th><th>×</th><th>×</th></tr>
</table>

#### 调用方法

##### 位与同一类中

```java
[this.]方法名([实际参数列表])
```

##### 类的外部

```java
对象名.方法名([实际参数列表])
```

### 定义成员周期

定义类的最终目的是要使用它。一般情况下,要使用类需要通过类的实例对象来实现。在定义类时,只是通知编译器需要准备多大的内存空间,并没有为它分配内存空间。只有用类创建了对象后,才会真正占用内存空间。

#### 方法调用的参数

##### 基本类型作为参数

*    它所传递的实参的值是一个副本。
*    单值传递。实参本质上是一个可求值的表达式,它所求出来的值是一个基本类型。
*    单向传递。方法内部可以修改形参的值,但这种修改不会影响到对应的实参。

##### 复合类型作为参数

*    如果实参是一个类的对象,那么在调用相应的方法时,系统会将该对象的地址值传递给形参。

### 包

#### 包作用

包是一组由类和接口所组成的集合, Java程序可以由若干个包组成,每一个包拥有自己独有的名字。包的引入,体现了封装特性,它将类与接口封装在一个包内,每个包中可以有若干类和接口,同一个包中不允许有同名的类和接口,但不同包中的类和接口不受此限制。

包的引入,解决了类命名冲突的问题,包提供了一种命名机制和可见性控制机制,起到了既可以划分类名空间,又可以控制类之间访问的作用。

由于同一包中的类默认可以相互访问,所以在一般情况下,总是将具有相似功能和具有共用性质的类放在同一个包中。

使用包的另外一个好处是有利于实现不同程序间类的复用。

包本身也是分级的,包中还可以有子包。Java的包可以用文件系统存放,也可以存放在数据库中。

在Java中为了防止类、接口、枚举和注释等命名冲突引用了包（package）概念，包本质上命名空间（namespace）。

在包中可以定义一组相关的类型（类、接口、枚举和注释），并为它们提供访问保护和命名空间管理。

命名空间，也称名字空间、名称空间等，它表示着一个标识符（identifier）的可见范围。一个标识符可在多个命名空间中定义，它在不同命名空间中的含义是互不相干的。这样，在一个新的命名空间中可定义任何标识符，它们不会与任何已有的标识符发生冲突，因为已有的定义都处于其他命名空间中。

#### 包定义

Java中使用package语句定义包，package语句应该放在源文件的第一行，在每个源文件中只能有一个包定义语句，并且package语句适用于所有类型（类、接口、枚举和注释）的文件。

```java
package pkg1[.pkg2[.pkg3...]];
```

pkg1~ pkg3都是组成包名一部分，之间用点（.）连接，它们命名应该是合法的标识符，其次应该遵守Java包命名规范，即全部小写字母。

包名一般是公司域名的倒置。

如果在源文件中没有定义包，那么类、接口、枚举和注释类型文件将会被放进一个无名的包中，也称为默认包。

#### 包引入

为了能够使用一个包中类型（类、接口、枚举和注释），需要在Java程序中明确引入该包。使用import语句实现引入包，import语句应位于package语句之后，所有类的定义之前，可以有0~n条import语句。

```java
 import package1[.package2…].(类型名|*);
```

“包名.类型名”形式只引入具体类型，“包名.*”采用通配符，表示引入这个包下所有的类型。但从编程规范的角度提倡明确引入类型名，即“包名.类型名”形式可以提高程序的可读性。

当前源文件与要使用的类型（类、接口、枚举和注释）在同一个包中，可以不用引入包。

#### 使用包

##### 在引用类(或接口)名前面加上它所在的包名

这种方法其实是以包名作为类名的前缀,这与以类名作为成员的前缀有些类似。

```java
包名.成员
```

##### 使用关键字import引入指定类

```java
import 包名.类名;
```

##### 使用import引入包中所有类

```java
import 包名.*;
```



#### 常用包

##### java.lang包

*    java.lang包含中包含了Java语言的核心类，如Object、Class、String、包装类和Math等，还有包装类Boolean、Character、Integer、Long、Float和Double。使用java.lang包中的类型，不需要显示使用import语句引入，它是由解释器自动引入。

##### java.io包

*    java.io包含中提供多种输入/输出流类，如InputStream、OutputStream、Reader和Writer。还有文件管理相关类和接口，如File和FileDescriptor类以及FileFilter接口。

##### java.net包

*    java.net包含进行网络相关的操作的类，如URL、Socket和ServerSocket等。

##### java.util包

*    java.util包含一些实用工具类和接口，如集合、日期和日历相关类和接口。

##### java.text包

*    java.text包中提供文本处理、日期式化和数字格式化等相关类和接口。

##### java.awt和javax.swing包

*    java.awt和javax.swing包提供了Java图形用户界面开发所需要的各种类和接口。java.awt提供是一些基础类和接口，javax.swing提供了一些高级组件。

### 抽象类与接口

设计良好的软件系统应该具备“可复用性”和“可扩展性”，能够满足用户需求的不断变更。使用抽象类和接口是实现“可复用性”和“可扩展性”重要的设计手段。

#### 抽象类

##### 抽象类声明和实现

在Java中抽象类和抽象方法的修饰符是abstract

```java
public abstract class name{
    
    // TODO
}
```

-    如果一个方法被声明为抽象的，那么这个类也必须声明为抽象的。而一个抽象类中，可以有0~n个抽象方法，以及0~n具体方法。
-    设计抽象方法目的就是让子类来实现的，否则抽象方法就没有任何意义(override重写)
-    抽象类不能被实例化,只有具体类才能被实例化。

#### 使用接口

-    比抽象类更加抽象的是接口，在接口中所有的方法都是抽象的。
-    接口可以有成员变量。

##### 接口声明和实现

-    在Java中接口的声明使用的关键字是interface

```java
public interface name{
    // 接口中静态成员变量，省略public static final
    // 接口中函数，省略public
}
```

-    某个类实现接口时，要在声明时使用implements关键字，当实现多个接口之间用逗号（,）分隔。实现接口时要实现接口中声明的所有方法。

```java
public class name implements interfacename{
    
    // override
}
```

##### 接口与多继承

-    在Java中只允许继承一个类，但可实现多个接口。通过实现多个接口方式满足多继承的设计需求。如果多个接口中即便有相同方法，它们也都是抽象的，子类实现它们不会有冲突。

```java
public interface InterfaceA {
    // TODO
}

public interface InterfaceB{
    // TODO
}

public class name implements InterfaceA,InterfaceB{
    // TODO
}
```

###### 接口继承

-    Java语言中允许接口和接口之间继承。由于接口中的方法都是抽象方法，所以继承之后也不需要做什么，因此接口之间的继承要比类之间的继承简单的多。

```java
public interface InterfaceA {
    // TODO
}

public interface InterfaceB extends InterfaceA{
    // TODO
}

public class name implements InterfaceB{
    // TODO
}
```

##### 默认方法和静态方法

###### java 8之前的特性

*    不能可选实现方法，接口的方法全部是抽象的，实现接口时必须全部实现接口中方法，哪怕是有些方法并不需要，也必须实现。
02.	没有静态方法。

###### Java 8新特性默认方法和静态方法

02.	接口中的默认方法类似于类中具体方法，给出了具体实现，只是方法修饰符是default。接口中静态方法类似于类中静态方法。

```java
public interface InterfaceA{
    
    // 默认方法
    default type name(){
        
        // TODO
    }
    
    // 静态方法
    static type name1(){
        
        // TODO
    }
}
```

02.	默认方法可以根据需要有选择实现（覆盖）。
02.	静态方法不需要实现，实现类中不能拥有接口中的静态方法。

#### 抽象类与接口区别

*    接口支持多继承，而抽象类（包括具体类）只能继承一个父类。
*    接口中不能有实例成员变量，接口所声明的成员变量全部是静态常量，即便是变量不加public static final修饰符也是静态常量。抽象类与普通类一样各种形式的成员变量都可以声明。
*    接口中没有包含构造方法，由于没有实例成员变量，也就不需要构造方法了。抽象类中可以有实例成员变量，也需要构造方法。
*    抽象类中可以声明抽象方法和具体方法。Java 8之前接口中只有抽象方法，而Java 8之后接口中也可以声明具体方法，具体方法通过声明默认方法实现。

### 枚举类

#### 特性

-    Java枚举类型本质上是一种继承java.lang.Enum类，是引用数据类型，因此也称为“枚举类”。
-    Java枚举类型是一种类，是引用类型，具有了面向对象特性，可以添加方法和成员变量等。
02.	Java枚举类型父类是java.lang.Enum，不需要显式声明。
03.	Java枚举类型可以实现接口，与类实现接口类似。
04.	Java枚举类型不能被继承，不存在子类。

#### 声明和定义

```java
public enum name{
    // 枚举常量表
    // MONDAY("星期一",0),TUESDAY("星期二",1),...
    
    // 实例变量
    [public|private|protected] type param_name;
    
    // 静态变量
    [public|private|protected] static type param_name;
    
    // 构造方法
    [public|private|protected] name(type param_name){
        
        // TODO
    }
    
    @Override
    public String toString(){
        
        // TODO
    }
}
```

#### 枚举方法

所有枚举类都继承java.lang.Enum类，Enum中定义了一些枚举中常用的方法：

*    int ordinal()：返回枚举常量的顺序。这个顺序根据枚举常量声明的顺序而定，顺序从零开始。
*    枚举类型[] values()：静态方法，返回一个包含全部枚举常量的数组。
*    枚举类型 valueOf(String str)：静态方法，str是枚举常量对应的字符串，返回一个包含枚举类型实例。

### 常用类

#### Java根类——Object

-    java.lang.Object类，它是Java所有类的根类，Java所有类都直接或间接继承自Object类，它是所有类的“祖先”。
-    Object类属于java.lang包中的类型，不需要显示使用import语句引入，它是由解释器自动引入。

##### 方法

###### String toString()

返回该对象的字符串表示。

为了日志输出等处理方便，所有的对象都可以以文本方式表示，需要在该对象所在类中覆盖toString()方法。如果没有覆盖toString()方法，默认的字符串是“类名@对象的十六进制哈希码”。

>    哈希码（hashCode），每个Java对象都有哈希码（hashCode）属性，哈希码可以用来标识对象，提高对象在集合操作中的执行效率。

###### boolean equals(Object obj)

指示其他某个对象是否与此对象“相等”。

```java
public class Name {
	
	// equals override
    public boolean equals(Object _object){

        [public|protected|private] type value;
        
        if(_object instanceof Name){

            Person _otherPerson=(Person)_otherObject;
            return this.value == _otherPerson.value;
        }

        return false;
    }
}
```

#### 包装类

*    在Java中8种基本数据类型不属于类，不具备“对象”的特征，没有成员变量和方法，不方便进行面向对象的操作。
*    Java提供包装类（Wrapper Class）来将基本数据类型包装成类，每个Java基本数据类型在java.lang包中都有一个相应的包装类，每个包装类对象封装一个基本数据类型数值。

| 基本数据类型 | 包装类    |
| ------------ | --------- |
| boolean      | Boolean   |
| byte         | Byte      |
| char         | Character |
| short        | Short     |
| int          | Integer   |
| long         | Long      |
| float        | Float     |
| double       | Double    |

*    包装类都是final的，不能被继承。包装类都是不可变类，类似于String类，一旦创建了对象，其内容就不可以修改。

##### 数值包装类

###### 构造方法类似

*    [包装类] (int value):通过指定一个数值构造包装类对象
*    [包装类] (String str):通过指定一个字符串str构造对象，s是十进制字符串表示的数值

###### 共同的父类

*    这6个数值包装类有一个共同的父类——Number，Number是一个抽象类，除了这6个子类还有：AtomicInteger、AtomicLong、BigDecimal和BigInteger
*    Number是抽象类，要求它的子类必须实现如下6个方法
     *    如果数值本身很大，可以会导致精度的丢失。
          *    byte byteValue()：将当前包装的对象转换为byte类型的数值。
          *    double doubleValue()：将当前包装的对象转换为double类型的数值。
          *    float floatValue()：将当前包装的对象转换为float类型的数值。
          *    int intValue()：将当前包装的对象转换为int类型的数值。
          *    long longValue()：将当前包装的对象转换为long类型的数值。
          *    short shortValue()：将当前包装的对象转换为short类型的数值。

###### doubleValue()

*    获取double值

###### intValue()

*    获取int值

###### compareTo()方法

*    每一个数值包装类都有int compareTo(数值包装类对象)方法，可以进行包装对象的比较。方法返回值是int，如果返回值是0，则相等；如果返回值小于0，则此对象小于参数对象；如果返回值大于0，则此对象大于参数对象。

###### 字符串转换为基本数据类型

*    每一个数值包装类都提供一些静态parseXXX()方法将字符串转换为对应的基本数据类型
     *    static type parseXXX(String s):将字符串s转换为有符号的十进制
     *    static int parseInt(String s,int radix):将字符串s转换有符号的整数，radix是指定基数，基数用来指定进制。注意这种指定基数的方法在浮点数包装类（Double和Float）中没有的。

###### 基本数据类型转换为字符串

*    每一个数值包装类都提供一些静态toString()方法实现将基本数据类型数值转换为字符串。
     *    static String toString(int i)：将该整数i转换为有符号的十进制表示的字符串。
     *    static String toString(int i, int radix)：将该整数i转换为有符号的特定进制表示的字符串， radix是基数可以指定进制。注意这种指定基数的方法在浮点数包装类（Double和Float）中没有的。

###### 转换为二进制、八进制、十六进制字符串

```java
Integer.toBinaryString(number);
Integer.to
```

###### 数值转换parse & toString

*    String 转 int

```java
int [intname] = Integer.parseInt("[Stringvalue]");
```

*    int 转 String

```java
String [stringname] = Integer.toString([intvalue]);
```

*    int 转 x进制，并返回String对象

```java
String strname = Integer.toString(int [intvalue], int x);
```

##### Character类

Character类是char类型的包装类。

###### 方法

*    Character(char value)：构造方法，通过char值创建一个新的Character对象。
*    char charValue()：返回此Character对象的值。
*    int compareTo(Character anotherCharacter)：方法返回值是int，如果返回值是0，则相等；如果返回值小于0，则此对象小于参数对象；如果返回值大于0，则此对象大于参数对象。

##### Boolean类

###### 构造方法

*    Boolean(boolean value)：通过一个boolean值创建Boolean对象。
*    Boolean(String s)：通过字符串创建Boolean对象。s不能为null，s如果是忽略大小写"true"则转换为true对象，其他字符串都转换为false对象。

###### compareTo()

-    Boolean类有int compareTo(Boolean包装类对象)方法，可以进行包装对象的比较。方法返回值是int，如果返回值是0，则相等；如果返回值小于0，则此对象小于参数对象；如果返回值大于0，则此对象大于参数对象。

###### 字符串转换为boolean类型

-    Boolean包装类都提供静态parseBoolean()方法实现将字符串转换为对应的boolean类型
-    static boolean parseBoolean(String s)：将字符串转换为对应的boolean类。s不能为null，s如果是忽略大小写"true"则转换为true，其他字符串都转换为false。

##### 自动装箱/拆箱

*    ava 5之后提供了拆箱(unboxing )功能，拆箱能够将包装类对象自动转换为基本数据类型的数值，而不需要使用intValue()或doubleValue()等方法。
*    类似Java 5还提供了相反功能，自动装箱( autoboxing )，装箱能够自动地将基本数据类型的数值自动转换为包装类对象，而不需要使用构造方法。

##### Math类

###### 舍入方法

*    static double ceil(double a)：返回大于或等于a最小整数。 
*    static double floor(double a)：返回小于或等于a最大整数。 
*    static int round(float a)：四舍五入方法。

###### 最大值和最小值

*    static int min(int a, int b)：取两个int整数中较小的一个整数。
*    static int min(long a, long b)：取两个long整数中较小的一个整数。
*    static int min(float a, float b)：取两个float浮点数中较小的一个浮点数。 
*    static int min(double a, double b)：取两个double浮点数中较小的一个浮点数。

###### 绝对值

*    static int abs(int a)：取int整数a的绝对值。
*    static long abs(long a)：取long整数a的绝对值。
*    static float abs(float a)：取float浮点数a的绝对值。 
*    static double abs(double a)：取double浮点数a的绝对值。

###### 三角函数

*    static double sin(double a)：返回角的三角正弦。
*    static double cos(double a)：返回角的三角余弦。 
*    static double tan(double a)：返回角的三角正切。 
*    static double asin(double a)：返回一个值的反正弦。 
*    static double acos(double a)：返回一个值的反余弦。 
*    static double atan(double a)：返回一个值的反正切。
*    static double toDegrees(double angrad)：将弧度转换为角度。 
*    static double toRadians(double angdeg)：将角度转换为弧度。

###### 对数运算

*    static double log(double a)：返回a的自然对数。

###### 平方根

*    static double sqrt(double a)：返回a的正平方根。

###### 幂运算

*    static double pow(double a, double b)：返回第一个参数的第二个参数次幂的值。

###### 计算随机值

-    static double random()：返回大于等于 0.0 且小于 1.0随机数。

###### 常量

*    圆周率PI
*    自然对数的底数E。

##### 大数值

-    BigInteger和BigDecimal，这里两个类都继承自Number抽象类。

###### BigInteger

-    java.math.BigInteger是不可变的任意精度的大整数。
-    构造方法
     -    BigInteger(String val)：将十进制字符串val转换为BigInteger对象。
     -    BigInteger(String val, int radix)：按照指定基数radix将字符串val转换为BigInteger对象。
-    int compareTo(BigInteger val)：将当前对象与参数val进行比较，方法返回值是int，如果返回值是0，则相等；如果返回值小于0，则此对象小于参数对象；如果返回值大于0，则此对象大于参数对象。
-    BigInteger add(BigInteger val)：加运算，当前对象数值加参数val。
-    BigInteger subtract(BigInteger val)：减运算，当前对象数值减参数val。
-    BigInteger multiply(BigInteger val)：乘运算，当前对象数值乘参数val。
-    BigInteger divide(BigInteger val)：除运算，当前对象数值除以参数val。

###### BigDecimal

*    构造方法
     *    BigDecimal(BigInteger val)：将BigInteger对象val转换为BigDecimal对象。
     *    BigDecimal(double val)：将double转换为BigDecimal对象，参数val是double类型的二进制浮点值准确的十进制表示形式。
     *    BigDecimal(int val)：将int转换为BigDecimal对象。
     *    BigDecimal(long val)：将long转换为BigDecimal对象。
     *    BigDecimal(String val)：将字符串表示数值形式转换为BigDecimal对象。
*    int compareTo(BigDecimal val)：将当前对象与参数val进行比较，方法返回值是int，如果返回值是0，则相等；如果返回值小于0，则此对象小于参数对象；如果返回值大于0，则此对象大于参数对象。
*    BigDecimal add(BigDecimal val)：加运算，当前对象数值加参数val。
*    BigDecimal subtract(BigDecimal val)：减运算，当前对象数值减参数val。
*    BigDecimal multiply(BigDecimal val)：乘运算，当前对象数值乘参数val。
*    BigDecimal divide(BigDecimal val)：除运算，当前对象数值除以参数val。
*    BigDecimal divide(BigDecimal val, int roundingMode)：除运算，当前对象数值除以参数val。 roundingMode要应用的舍入模式。
*    

#### 日期时间相关类

##### Date类

###### 构造方法

*    Date()：用当前时间创建Date对象，精确到毫秒。
*    Date(long date)：指定标准基准时间以来的毫秒数创建Date对象。标准基准时间是格林威治时间1970年1月1日00:00:00。

###### 方法

*    boolean after(Date when)：测试此日期是否在when日期之后。
*    boolean before(Date when)：测试此日期是否在when日期之前。
*    int compareTo(Date anotherDate)：比较两个日期的顺序。如果参数日期等于此日期，则返回值0；如果此日期在参数日期之前，则返回小于0的值；如果此日期在参数日期之后，则返回大于0的值。
*    long getTime()：返回自1970年1月1日00:00:00以来此Date对象表示的毫秒数。
*    void setTime(long time)：用毫秒数time设置日期对象，time是自1970年1月1日00:00:00以来此Date对象表示的毫秒数。

###### 日期格式化和解析

*    日期格式化类是java.text.DateFormat，DateFormat是抽象类，它的常用具体类是java.text.SimpleDateFormat。
     *    String format(Date date)：将一个Date格式化为日期/时间字符串。
     *    Date parse(String source)：从给定字符串的开始解析文本，以生成一个日期对象。如果解析失败则抛出ParseException。
     *    并不是所有的字符串都能够转换为日期，如果转换失败parse方法会抛出异常ParseException。

```java
public static void main(String[] args) throws ParseException {...}
```

*    构造方法
     *    SimpleDateFormat()：用默认的模式和默认语言环境的日期格式符号构造SimpleDateFormat。
     *    SimpleDateFormat(String pattern)：用给定的模式和默认语言环境的日期格式符号构造SimpleDateFormat。pattern参数是日期和时间格式模式。

| 字母 | 日期或时间元素  |
| ---- | --------------- |
| y    | 年              |
| M    | 年中的月份      |
| D    | 年中的天数      |
| d    | 月份中的天数    |
| H    | 一天中的小时数  |
| h    | AM/PM中的小时数 |
| a    | AM/PM标记       |
| m    | 小时中的分钟数  |
| s    | 分钟中的秒数    |
| S    | 毫秒数          |
| Z    | 时区            |

##### Calendar类

*    有时为了取得更多的日期时间信息，或对日期时间进行操作，可以使用java.util.Calendar类，Calendar是一个抽象类，不能实例化，但是通过静态工厂方法getInstance()获得Calendar实例。

###### 方法

*    static Calendar getInstance()：使用默认时区和语言环境获得一个日历。
*    void set(int field, int value)：将给定的日历字段设置为给定值。
*    void set(int year,int month,int date)：设置日历字段YEAR、MONTH和DAY_OF_MONTH的值。
*    Date getTime()：返回一个表示此Calendar时间值（从1970年1月1日00:00:00至现在的毫秒数）的Date对象。
*    boolean after(Object when)：判断此Calendar表示的时间是否在指定时间之后，返回判断结果。 
*    boolean before(Object when)：判断此Calendar表示的时间是否在指定时间之前，返回判断结果。
*    int compareTo(Calendar anotherCalendar)：比较两个Calendar对象表示的时间值。

##### LocalDate、LocalTime和LocalDateTime

*    都位于java.time包中，LocalDate表示一个不可变的日期对象；LocalTime表示一个不可变的时间对象；LocalDateTime表示一个不可变的日期和时间。

###### 方法

*    now()
     *    static LocalDate now()：LocalDate静态工厂方法，该方法使用默认时区获得当前日期，返回LocalDate对象。
     *    static LocalTime now()：LocalTime静态工厂方法，该方法使用默认时区获得当前时间，返回LocalTime对象。
     *    static LocalDateTime now()：LocalDateTime静态工厂方法，该方法使用默认时区获得当前日期时间，返回LocalDateTime对象。
*    of()
     *    static LocalDateTime of(int year, int month, int dayOfMonth, int hour, int minute, int second)：按照指定的年、月、日、小时、分钟和秒获得LocalDateTime实例，将纳秒设置为零。
     *    static LocalTime of(int hour, int minute, int second)：按照指定的小时、分钟和秒获取一个LocalTime实例。
     *    static LocalDate of(int year, int month, int dayOfMonth)：按照指定的年、月和日获得一个LocalDate实例，日期中年、月和日必须有效，否则将抛出异常。

| 参数       | 说明                              |
| ---------- | --------------------------------- |
| year       | 从-999,999,999到999,999,999的年份 |
| month      | 一年中的月份，从1至12             |
| dayOfMonth | 月中的天，从1至31                 |
| hour       | 从0到23表示的小时                 |
| minute     | 从0到59表示的分钟                 |
| second     | 从0到59表示的秒                   |

###### 日期格式化和解析

-    Java 8提供的日期格式化类是java.time.format.DateTimeFormatter，DateTimeFormatter中本身没有提供日期格式化和日期解析方法，这些方法还是由LocalDate、LocalTime和LocalDateTime提供的。
-    日期格式化
     -    日期格式化方法是format，这三个类每一个都有String format(DateTimeFormatter formatter)，参数formatter是DateTimeFormatter类型

```java
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss");
```

-    日期解析
     -    static LocalDateTime parse(CharSequence text)：使用默认格式，从一个文本字符串获取一个LocalDateTime实例。
     -    static LocalDateTime parse(CharSequence text, DateTimeFormatter formatter)：使用指定格式化，从文本字符串获取LocalDateTime实例。
     -    static LocalDate parse(CharSequence text)：使用默认格式，从一个文本字符串获取一个LocalDate实例。
     -    static LocalDate parse(CharSequence text, DateTimeFormatter formatter)：使用指定格式化，从文本字符串获取LocalDate实例。
     -    static LocalTime parse(CharSequence text)：使用默认格式，从一个文本字符串获取一个LocalTime实例。
     -    static LocalTime parse(CharSequence text, DateTimeFormatter formatter)：使用指定的格式化，从文本字符串获取LocalTime实例。

### 内部类

*    Java中内部类技术，简单说就是在一个类的内部定义一个类。
     *    内部类技术虽然使程序结构变得紧凑，但是却在一定程度上破坏了Java面向对象思想。

#### 概述

*    Java语言中允许在一个类（或方法、代码块）的内部定义另一个类，后者称为“内部类”（Inner Classes），也称为“嵌套类”（Nested Classes），封装它的类称为“外部类”。内部类与外部类之间存在逻辑上的隶属关系，内部类一般只用在封装它的外部类或代码块中使用。

#### 作用

*    封装。将不想公开的实现细节封装到一个内部类中，内部类可以声明为私有的，只能在所在外部类中访问。
*    提供命名空间。静态内部类和外部类能够提供有别于包的命名空间。
*    便于访问外部类成员。内部类能够很方便访问所在外部类的成员，包括私有成员也能访问。

#### 内部类的分类

严格来说,内部类分为3种:嵌入类(nested) 、内部成员类(inner)和本地类。当类的前面有static修饰符时,它就是嵌入类。嵌入类只能和外部类的成员并列,不能定义在方法中。如果类和外部类的成员是并列定义的,且没有static修饰,则该类称为内部成员类。如果类是定义在某个方法中,则该类称为本地类。

*    内部类
     *    有名内部类
          *    局部内部类
          *    成员内部类
               *    实例成员内部类
               *    静态成员内部类
     *    匿名内部类

#### 成员内部类

成员内部类类似于外部类的成员变量，在外边类的内部，且方法体和代码块之外定义的内部类。

```java
[访问权限修饰符] class 类名[extends 父类名][implements 接口列表]{
    类体
}
```

内部成员类与嵌入类最大的不同在于,它的类体中不允许存在静态成员,包括静态成员变量和静态成员方法,但可以定义静态的常量。

##### 实例内部类(内部成员类)

*    实例内部类与实例变量类似，可以声明为公有级别、私有级别、默认级别或保护级别，即4种访问级别都可以，而外部类只能声明为公有或默认级别。

```java
public class name{
    
    // TODO
    
    // 内部类
    class name2{
        
        // TODO
    }
}
```

##### 静态内部类(嵌入类)

当内部类的前面用static修饰时,它就是一个静态内部类。它和外部类的其他成员属性和方法处在同一层次上。

```java
[访问权限修饰符] static class 类名[extends 父类名][implements 接口列表]{
    类体
}
```

在嵌入类的类体中,可以定义任何类型的成员属性和方法,这一点与顶层类完全相同。·它本身可以是final类型或者是abstract类型,也可以被其他类所继承。

*    在静态内部类中可以访问外部类的静态成员，但是不能访问非静态成员。
*    静态内部类与静态变量类似，在声明的时候使用关键字static修饰，静态内部类只能访问外部类静态成员，所以静态内部类使用的场景不多。但可以提供有别于包的命名空间。

```java
public class name{
    
    // static
    static [public|protected|private] type value;
    
    // 内部类
    static class name2{
        
        // TODO
        // use outer static value
    }
}
```

##### 局部内部类(本地类)

*    局部内部类就是在方法体或代码块中定义的内部类，局部内部类的作用域仅限于方法体或代码块中。
*    局部内部类访问级别只能是默认的，不能是公有的、私有的和保护的访问级别，即不能使用public、 private和protected修饰。局部内部类也不能是静态，即不能使用static修饰。局部内部类可以访问外部类所有成员。

```java
public class Outer {

    // TODO

    // 在方法体或代码块中
    public type function([parameter] value) {

        // TODO

        // 在方法体或代码块中定义的内部类
        // 局部内部类访问级别只能是默认的
        class Inner {

            void function_2()) {

                // TODO
            }
        }

        new Inner().function_2();
    }
}
```

##### 匿名内部类

-    匿名内部类是没有名字的内部类，本质上是没有名的局部内部类，具有局部内部类所有特征。

```java
new interfaceName () {
    类体
}
```

-    匿名类是没有名字的, iterfceName和superClassName,并不是它的名字,而是它要继承的接口或类的名字。括号中的参数是用来传递给父类的构造方法。
-    匿名内部类可以使你的代码更加简洁，你可以在定义一个类的同时对其进行实例化。它与局部类很相似，不同的是它没有类名，如果某个局部类你只需要用一次，那么你就可以使用匿名内部类
-    由于构造方法必须与类名相同,而匿名类没有类名,所以匿名类没有构造方法。取而代之的是将参数传递给父类的构造方法。如果是实现接口,则不能有任何参数。
-    使用一个匿名内部类,通常按照下面的形式

```java
superclassName oa =new superClassName (参数) {类体};
```

唯一的区别在于匿名内部类后面有大括号括起来的类体。

-    有时候,程序员需要将由匿名类创建的对象作为实际参数传递给某个方法。此时,对象也可以没有名字:

```java
function ( new superclass(){类体};);
```

##### 拥有成员

<table>
    <tr><th></th><th>静态常量</th><th>静态变量</th><th>实例变量</th><th>实例常量</th><th>静态方法</th><th>实例方法</th></tr>
    <tr><th>嵌入类</th><th>√</th><th>√</th><th>√</th><th>√</th><th>√</th><th>√</th></tr>
    <tr><th>内部成员类</th><th>√</th><th></th><th>√</th><th>√</th><th></th><th>√</th></tr>
    <tr><th>本地类</th><th>√</th><th></th><th>√</th><th>√</th><th></th><th>√</th></tr>
</table>
#### 在外部使用内部类

对于嵌入类和内部成员类,只要它们的访问权限不是private,则可以在外部使用这些类,只是使用的方式有所不同。对于本地类,在外部是无法使用的。如果是嵌入类,可以像使用静态成员一样,通过“外部类名.嵌入类名”的方式使用。由于内部成员类是非静态的,必须通过外部类的实例进行引用。

### 抽象类

#### 抽象类与抽象方法

类的继承结构中,越往上的类越具有通用性,也就越抽象。当它抽象到一定的程度,就变成了一个概念或框架,不能再产生实例化的对象了。

对应这一现象, Java中提供了抽象类,它只能作为父类,不能实例化。定义抽象类的作用是将一类对象的共同特点抽象出来,成为代表该类共同特性的抽象概念,其后在描述某一具体对象时,只要添加与其他子类对象的不同之处,而不需要重复类的共同特性。这样就使得程序概念层次分明,开发更高效。与抽象类紧密相连的是抽象方法-它总是用在抽象类或接口中。

#### 抽象方法的声明

抽象方法是一种只有方法声明而没有方法体定义的特殊方法。它的声明部分和一般方法并没有太大的区别,也有访问权限和返回值类型等。只是需要在前面加上一个关键字abstract

```java
abstract 访问权限返回类型 方法名([参数列表]);
```

声明抽象方法时有以下几个限制:

*    构造方法不能声明为abstract;
*    静态方法不能声明为abstract;
*    private方法不能声明为abstract:
*    final方法不能声明为abstract;
*    抽象方法只能出现在抽象类或接口中。

#### 抽象类的定义

```java
abstract class className{
    类体
}
```

在抽象类中,可以有0个或多个抽象方法,也可以有普通的实例方法和静态方法,还可以有其他的成员变量和构造方法。如果类中没有任何形式的抽象方法,那么可以由程序员自主决定是否将类声明成abstract类型,但是只要是下面这些情况之一,则类必定为抽象类,必须加上abstract修饰:

*    类中明确声明有abstract方法。
*    类是从抽象类继承下来的,而且没有实现父类中全部的抽象方法。
*    类实现了一个接口,但没有将其中所有的抽象方法实现。

使用抽象类的唯一途径是派生一个子类,如果这个子类实现了抽象类中所有的抽象方法,那么这个子类就是一个普通的类,它可以用来创建对象。

#### 抽象方法与回调函数

在抽象类中,既可以有抽象方法,也可以有普通方法,而且普通方法还可以调用抽象方法。

所谓回调函数,是指函数f1调用了函数f2,函数f2又调用了函数f3,但是函数f3的函数体并不是确定的,它是由函数f1在调用f2时作为参数传递给f2的,则f3被称为回调函数。

回调函数的实现需要用到函数指针, Java是完全面向对象的语言,没有函数指针,只能通过上述机制来实现。

### 最终类和最终方法

#### 最终类

如果一个类不希望被其他类继承,则可以声明成final类,这样就可以防止其他类以它作为父类。

最终类显然不可能是抽象类。由于最终类不能有子类,那么它所拥有的所有方法都不可能被覆盖,因此它其中所有的方法都是最终方法。

```java
[访问权限] final class类名{
    类体
}
```

最终类可以从其他类派生出来。由于它没有子类,所以声明成最终类的变量一定不会引用它子类的对象,因此它的变量不存在运行时多态的问题。

#### 最终方法

编译器可以在编译时确定每个方法的调用,这样可以加快执行速度。如果一个类允许被其他类继承,只是其中的某些方法不允许被子类覆盖,那么可以将这些方法声明成为最终方法,这需要在声明前面加上关键字final

```java
[访问权限] final 返回类型 方法名([参数列表])
```

使用最终方法时,有两点需要注意

*    最终方法可以出现在任何类中,但不能和abstract修饰符同时使用。
*    最终方法不能被覆盖,但是可以被重载。

## 封装性与访问控制

|      | 同一个类 | 同一个包 | 不同包的子类 | 不同包非子类 |
| ---- | -------- | -------- | ------------ | ------------ |
| 私有 | Y        |          |              |              |
| 默认 | Y        | Y        |              |              |
| 保护 | Y        | Y        | Y            |              |
| 公有 | Y        | Y        | Y            | Y            |

### 私有级别

私有级别的关键字是private，私有级别的成员变量和方法只能在其所在类的内部自由使用，在其他的类中则不允许直接访问。

私有级别限制性最高。

### 默认级别

默认级别没有关键字，也就是没有访问修饰符，默认级别的成员变量和方法，可以在其所在类内部和同一个包的其他类中被直接访问，但在不同包的类中则不允许直接访问。

### 公有级别

公有级别的关键字是public，公有级别的成员变量和方法可以在任何场合被直接访问，是最宽松的一种访问控制等级。

### 保护级别

保护级别的关键字是protected，保护级别在同一包中完全与默认访问级别一样，但是不同包中子类能够继承父类中的protected变量和方法，这就是所谓的保护级别，“保护”就是保护某个类的子类都能继承该类的变量和方法。

>    访问成员有两种方式：一种是调用，即通过类或对象调用它的成员；另一种是继承，即子类继承父类的成员变量和方法。

访问类成员时，在能满足使用的前提下，应尽量限制类中成员的可见性，访问级别顺序是：私有级别→默认级别→保护级别→公有级别。

## 静态变量和静态方法

### 静态变量

Java 中被 static 修饰的成员称为静态成员或类成员。它属于整个类所有，而不是某个对象所有，即被类的所有对象所共享。

静态成员可以使用类名直接访问，也可以使用对象名进行访问。

*    静态变量可以直接使用类名来访问，无需创建对象

使用 static 可以修饰变量、方法和代码块。

静态成员属于整个类，当系统第一次使用该类时，就会为其分配内存空间直到该类被卸载才会进行资源回收

### 静态方法

实例方法必须在类实例化之后通过对象来调用,而静态方法可以在类实例化之前就使用。与成员变量不同的是:无论哪种方法,在内存中只有一份，无论该类有多少个实例,都共用同一个方法。

```java
[访问权限修饰符] static [返回值类型]方法名([参数列表]){
    语句序列
}
```

### 静态代码块

```java
static{
	语句序列
}
```

*    静态代码块只能定义在类里面,它独立于任何方法,不能定义在方法里面。
*    静态代码块里面的变量都是局部变量,只在本块内有效。
*    静态代码块会在类被加载时自动执行,而无论加载者是JVM还是其他的类。
*    一个类中允许定义多个静态代码块,执行的顺序根据定义的顺序进行。
*    静态代码块只能访问类的静态成员,而不允许访问实例成员。

### 静态变量与静态方法关系

*    静态方法中可以直接调用同类中的静态成员，但不能直接调用非静态成员
*    如果希望在静态方法中调用非静态变量，可以通过创建类的对象，然后通过对象来访问非静态变量。
*    在普通成员方法中，则可以直接访问同类的非静态变量和静态变量
*    静态方法中不能直接调用非静态方法，需要通过对象来访问非静态方法。在外部调用静态方法时,可以使用“类名.方法名”的方式,也可以使用“对象名.方法名”的方式;而实例方法只有后面这种方式。
*    静态方法在访问本类的成员时,只允许访问静态成员(即静态成员变量和静态方法) ,而不允许访问实例成员变量和实例方法;实例方法则无此限制。

### 执行顺序

程序运行时静态初始化块最先被执行，然后执行普通初始化块，最后才执行构造方法。

### main()方法

```java
public static void main(String[] args){
    // TODO
}
```

main()方法是一个重要而又特殊的方法。它是Java应用程序的入口, JVM在运行字节码文件时,做完初始化之后,就会查找main()方法,从这里开始整个程序的运行。

main()方法是静态方法,它由类共有而不是属于类的某个实例,所以系统可以直接调用main()方法而无需创建它所属的类的实例。因此在运行main()方法时,只能使用该类中的静态成员,如果要使用实例成员,需要先创建该类的实例对象,然后用对象来访问实例成员。

main()方法只能被系统调用,不能被其他任何方法或类调用,这是它和一般静态方法的区别。

在main()方法的括号里面并不为空,它有一个形式参数String args[]。其中, String是Java预定义的字符串类, args]是一个数组,它有若干个元素,每个元素都是一个字符串。

#### 使用命令行参数

对于控制台程序而言,在命令行执行一个程序通常的形式是:

```java
java 类名 [参数列表]
```



## 局部变量

### 一般形式

*    变量修饰符可以是final,表示这是常量。
*    变量类型可以是Java中任意合法的基本类型或复合类型。
*    变量名是用户自定义标识符,遵循标识符的一般规则。
*    可以在一行中定义多个局部变量,以逗号分隔。
*    定义变量时可以同时赋初值。局部变量必须要先定义后使用。

```java
[变量修饰符]变量类型 变量名;
```

### 局部变量和成员变量的区别

*    局部变量没有访问权限修饰符,不能用public, private和protected来修饰。这是因为它只能在定义它的方法内部使用。
*    局部变量不能用static修饰,没有“静态局部变量",这是Java和C/C++的一个细微差别。
*    系统不会自动为局部变量赋初值,但对于成员变量,系统会自动赋初值。
*    基本类型的初值为0,复合类型的初值为null。
*    局部变量的作用域仅限于定义它的方法,在该方法的外部无法访问它。
*    成员变量的作用域在整个类内部都是可见的,所有成员方法都可以使用它。如果访问权限允许,还可以在类的外部使用成员变量。
*    局部变量的生存周期与方法的执行期相同。当方法执行到定义局部变量的语句时,局部变量被创建;执行到它所在的作用域的最后一条语句时,局部变量被销毁。
*    类的成员变量,如果是实例成员变量,则它和对象的生存期相同。而静态成员变量的生存期是整个程序运行期。
*    在同一个方法中,不允许有同名的局部变量。在不同的方法中,可以有同名的局部变量,它们互不干涉。
*    局部变量可以和成员变量同名,且在使用时,局部变量具有更高的优先级。

## 对象

类实例化可生成对象，实例方法就是对象方法，实例变量就是对象属性。一个对象的生命周期包括三个阶段：创建、使用和销毁。

### 创建对象

创建对象包括两个步骤：声明和实例化。

#### 声明

*    声明对象与声明普通变量没有区别

```java
type objectName;
```

##### 空对象

*    一个引用变量没有通过new分配内存空间，这个对象就是空对象，Java使用关键字null表示空对象。
*    引用变量默认值是null。当试图调用一个空对象的实例变量或实例方法时，会抛出空指针异常NullPointerException
*    应该避免调用空对象的成员变量和方法

##### 初始化对象

```java
类名 对象名=new 构造方法名([参数列表]);
```

#### 实例化

*    实例化过程分为两个阶段：为对象分配内存空间和初始化对象，首先使用new运算符为对象分配内存空间，然后再调用构造方法初始化对象。

### 使用对象

#### 对象变量的使用

```java
对象名.成员变量名
```

#### 对象方法的调用

```java
对象名.成员方法名([参数列表])
```

### 构造方法

*    构造方法名必须与类名相同。
*    构造方法没有任何返回值，包括void。
*    构造方法只能与new运算符结合使用。

```java
public class name{
    // default
    public name([parameter] value){
        // TODO
    }
}
```

#### 默认构造方法

*    有时在类中根本看不到任何的构造方法。Java虚拟机为没有构造方法的类，提供一个无参数的默认构造方法，默认构造方法其方法体内无任何语句

```java
public class name{
    public name(){}
}
```

#### 构造方法重载

*    在一个类中可以有多个构造方法，它们具体有相同的名字（与类名相同），参数列表不同，所以它们之间一定是重载关系。

#### 构造方法封装

```java
public class name{
    // 公有级别限制
    public name([parameter] value){
        // TODO
    }
    
    // 私有级别限制
    private name([parameter] value){
        // TODO
    }
    
    // 默认级别限制，默认级别只能在同一个包中访问
    name([parameter] value){
        // TODO
    }
    
    // 保护级别限制，该构造方法在同一包中与默认级别相同，在不同包中可以被子类继承
    protected name([parameter] value){
        // TODO
    }
}
```

>    单例模式是一种常用的软件设计模式，单例模式可以保证系统中一个类只有一个实例。

*    不同访问权限而相同参数的构造函数不能共存。

#### 方法

```java
[方法修饰符] [方法返回值类型] 方法名 ([形式参数表])
```

*    访问权限修饰符包括private, protected,public和默认。它们的含义也和成员变量中的完全相同
*    final表示最终方法。
*    static表示静态方法。
*    方法的返回值类型也和成员变量的数据类型一样,可以是基本类型: int,char和double等,也可以是类类型。
*    返回值类型可以是void,表示没有返回值。
*    形式参数列表是方法可以接收的参数,它由外部调用者提供具体的值。参数可以有多个,中间用逗号分隔。也可以没有参数,但圆括号不能省略。

##### return

如果是void类型的方法,则可以不需要return语句。如果有return语句,则return语,句后面的表达式应为空,

## this关键字

*    这个this是Java定义中的一个关键字。
*    为了让程序员能够在方法中使用this, Java会将this作为一个隐含的参数传递给每一个实例方法。
*    它其实是指向当前对象的一根指针,直观地理解,它就是表示“本对象”的意思。
*    this作为隐含参数传递,最重要的作用是区分各个对象所拥有的成员。

this指向对象本身，一个类可以通过this来获得一个代表它自身的对象变量。

#### 使用

*    调用实例变量。
*    调用实例方法。
*    调用其他构造方法。

#### 作用

*    命名冲突，参数是作用域为整个方法的局部变量，为了防止局部变量与成员变量命名发生冲突，可以使用this调用成员变量。
*    this也可以调用本对象的方法

## 多态

### 条件

*    继承。多态发生一定要子类和父类之间。
*    覆盖。子类覆盖了父类的方法。
*    声明的变量类型是父类类型，但实例则指向子类实例。

多态发生时，Java虚拟机运行时根据引用变量指向的实例调用它的方法，而不是根据引用变量的类型调用。

### 继承

类的继承性是面向对象语言的基本特性，多态性的前提是继承性。Java支持继承性和多态性。

#### Java中的继承

继承使用的关键字是extends， extends后面的class是父类。

>    一般情况下，一个子类只能继承一个父类，这称为“单继承”，但有的情况下一个子类可以有多个不同的父类，这称为“多重继承”。在Java中，类的继承只能是单继承，而多重继承可以通过实现多个接口实现。也就是说，在Java中，一个类只能继承一个父类，但是可以实现多个接口。

面向对象分析与设计（OOAD）时，会用到UML图 ，其中类图非常重要，用来描述系统静态结构。

UML是Unified Modeling Language的缩写，即统一标准建模语言。它集成了各种优秀的建模方法学发展而来的。UML图常用的有例图、协作图、活动图、序列图、部署图、构件图、类图、状态图。

#### 继承实现方法

*    实现继承是指使用基类的属性和方法而无需额外编码的能力。
*    接口继承是指仅使用属性和方法的名称,但是子类必须提供实现的能力。
*    可视继承是指子窗体(类)使用基窗体(类)的外观和实现代码的能力。

#### Java中子类继承父类的描述及实现

```cpp
[类修饰符] class 子类名 extends 父类名{
    类体
}
```

#### Java 的继承内存分配

对于父类中的成员,当它被子类继承后,并非将其复制了一份放到子类的空间中,它仍然只在父类空间中存在一份。如果程序中通过“子类对象名成员名”的方式使用成员,编译器会首先到子类中查找是否存在此成员,如果没有,则在其父类空间中查找,依次往上推。如果直到Obiect类(该类为所有类的公共祖先)还未发现此成员,则编译器报错。如果成员方法要访问成员变量,也是首先查找本类中是否存在该成员变量。如果没有,则到父类及祖先类空间中查找,直到Object类为止。

为了保证父类和子类有不同的空间,系统在生成子类对象时,会自动生成一个父类的隐藏对象。如果父类还有父类,则依次类堆。

#### 调用父类构造方法

当子类实例化时，不仅需要初始化子类成员变量，也需要初始化父类成员变量，初始化父类成员变量需要调用父类构造方法，子类使用super关键字调用父类构造方法。

```java
public class Base{
    
    public Base([parameter1] value1){
        // TODO
    }
}

public class Plus extends Base{
    
    public Plus([parameter2] value2){
        supper(value1);
        // TODO
    }
}
```

*    super语句必须位于子类构造方法的第一行。

子类构造方法由于没有super语句，编译器会试图调用父类默认构造方法（无参数构造方法），但是如果父类并没有默认构造方法，因此会发生编译错误。解决这个编译错误有三种办法：

*    在父类中添加默认构造方法，子类Student会隐式调用父类的默认构造方法。
*    在子类构造方法添加super语句，显式调用父类构造方法，super语句必须是第一条语句。
*    在子类构造方法添加this语句，显式调用当前对象其他构造方法，this语句必须是第一条语句。

#### 成员变量隐藏

##### 成员变量隐藏

子类成员变量与父类一样，会屏蔽父类中的成员变量，称为“成员变量隐藏”。

```java
public class Base{
    
    [private|public|protected] type value;
    
    public Base(){
        // TODO
    }
}

public class Plus extends Base{
    
    [private|public|protected] type value;// hide the base value
    
    public Plus(){
        super();
        // TODO
    }
}
```

###### 修饰符完全相同的情况

###### 访问权限不相同的情况

Java中规定,子类用于隐藏的变量可以和父类的访问权限不同,如果访问权限被改变,则以子类的权限为准。

###### 数据类型不相同的情况

Java允许子类的变量与父类变量的类型完全不同,以修改后的数据类型为准。

###### 常量修饰符不同的情况

Java允许父类的变量被子类的常量隐藏,也允许父类的常量被子类的变量隐藏。

###### 静态修饰符不同的情况

Java允许用实例成员变量来隐藏静态成员变量,也允许用静态成员变量来隐藏实例成员变量。

### 方法的覆盖（Override）

如果子类方法完全与父类方法相同，即：相同的方法名、相同的参数列表和相同的返回值，只是方法体不同，这称为子类覆盖（Override）父类方法。

#### 方法覆盖条件

*    方法名称必须相同。
*    方法的参数必须完全相同,包括参数的个数、类型和顺序。

#### 覆盖方法

##### 修饰符完全相同的覆盖

##### 访问权限不相同的情况

子类方法的访问权限可以与父类的不相同,但只允许权限更宽松,而不允许更严格。"它遵循的是“公开的不再是秘密”这一原则。没有任何办法能够改变这一原则,这一点和C+有很大的区别。

##### 返回值数据类型不相同的情况

当覆盖时,不允许出现返回值数据类型不相同的情况。也就是说,覆盖与被覆盖的方法的返回值数据类型必须完全相同。

##### final修饰符不同的情况

若方法前面用final修饰,则表示该方法是一个最终方法,它的子类不能覆盖该方法;反之,一个非最终方法,可以在子类中指定final修饰符,将其变成最终方法。

##### 静态修饰符不同的情况

Java规定,静态方法不允许被实例方法覆盖。同样,实例方法也不允许用静态方法覆盖。也就是说,不允许出现父类方法和子类方法覆盖时的static修饰符发生变化。

#### @Override注解

1.   提高程序的可读性。
2.   编译器检查@Override注解的方法在父类中是否存在，如果不存在则报错。

#### 方法覆盖原则

1.	覆盖后的方法不能比原方法有更严格的访问控制（可以相同）。例如将代码第②行访问控制public修改private，那么会发生编译错误，因为父类原方法是protected。
2.	覆盖后的方法不能比原方法产生更多的异常。

### 方法重载（Overload）

这些相同名字的方法之所以能够在一个类中同时存在，是因为它们的方法参数列表，调用时根据参数列表调用相应重载方法。

调用哪一个方法是根据参数列表决定的。如果参数类型不一致，编译器会进行自动类型转换寻找适合版本的方法，如果没有适合方法，则会发生编译错误。

#### 普通方法的重载

*    参数个数不同
*    对应位置上的参数类型不同

#### 构造方法的重载

相对于普通的成员方法,由于构造方法不能是static和final类型,而且也没有返回值,所以它的重载比普通成员方法更简单一些,但一般的规则完全相同。

#### 重载的解析

当类的设计者提供了重载方法之后,类的使用者在使用这些方法时,编译器需要确定调用哪一个方法。确定的唯一依据是参数列表,确定的过程被称为重载的解析。

##### 编译器解析的步骤

1.   根据调用的方法名,查找是否有定义好的同名方法,如果没有,则会报错。
2.   比较形参和实参的数目是否相等,如果没有,则会报错。如果有一个或多个方法符合条件,则这些方法进入候选集。
3.   与候选集中的方法比较参数表,如果对应位置上的每个参数类型完全匹配,或者可以通过扩展转换相匹配,则该方法称为可行方法,并入可行集。若不存在可行方法,则会报错。
4.   在可行集中按照下面的原则选取最佳可行方法。若最佳可行方法为0,则会报错;否则最佳可行方法就是最终确定要调用的方法。

##### 选取的原则

*    若每一参数都可以完全匹配,它就是最佳可行方法。
*    若某方法的每一个参数匹配都不比别的方法差,且至少有一个参数比别的方法好,它就是最佳可行方法。

扩展转换有两条路径,分别为:

<center>byte-short-int-long-float-double和char-int-long-float-double</center>

#### 重载与覆盖的区别

1.   方法重载是同一个类中多个方法之间的关系，是水平关系；而方法覆盖是子类和父类之间的关系，是垂直关系。
2.   方法重载要求参数的列表不同（类型或者数目，仅形参名不同不视为参数列表不同），覆盖则要求参数列表相同（形参名不同亦视为参数列表相同）。
3.   方法重载是多个方法之间的关系；覆盖只能由一个方法，或只能由一对方法产生关系。
4.   重载关系，是根据调用时的实参表与形参表来选择方法体的，覆盖关系，调用哪个方法则是根据对象的类型（对象存储空间，判断是父类还是子类）来决定。

### 运行时多态

运行时多态将多态的特性发挥到极致。它允许程序员不必在编制程序时就确定调用哪一个方法,而是当方法被调用时,系统根据当时对象本身所属的类来确定调用哪个方法,这种技术称为后期(动态)绑定。当然这会降低程序的运行效率,所以只在子类对父类方法进行覆盖时才使用。

#### 实例方法的运行时多态

```java
public class Base{
    
    public type function(){
        
        // TODO
    }
}

public class Plus1 extends Base{
    
    public type function(){
        
        // TODO
    }
}

public class Plus2 extends Base{
    
    public type function(){
        
        // TODO
    }
}

// 多态
Base c_plus1=new Plus1();
Base c_plus2=new Plus2();
c_plus1.function();
c_plus2.function();
```

#### 成员变量运行时多态

对于成员变量,无论是实例成员变量还是静态成员变量,引用在编译时就已经确定好了。

```java
public class Base{
    
    type1 value;
    
    public void setValue(type1 value){
        
        this.value=value;
    }
    
    public type1 getValue(){
        
        return value;
    }
}

public class super extends Base{
    
    type2 value;
    
    public type2;
    
    public void setValue(type2 value){
        
        this.value=value;
    }
    
    public type2 getValue(){
        
        return value;
    }
}
```

#### 静态方法运行时多态

对于静态方法而言,它们是没有运行时多态特性的。

造成这种区别的原因很简单:实例方法总是和某个对象绑定在一起,而静态方法则没有与某个对象绑定在一起,也就无从查找调用时该对象实际所属的类别。

### 引用类型检查

*    在运行时判断一个对象是否属于某个引用类型，这时可以使用instanceof运算符

```java
obj instanceof type;
```

如果obj对象是type引用类型实例则返回true，否则false

```java
if(obj instanceof type){
    
    // true
}else{
    
    // false
}
```

### 引用类型转换

引用类型可以进行转换，但并不是所有的引用类型都能互相转换，只有属于同一棵继承层次树中的引用类型才可以转换。

引用类型转换也是通过小括号运算符实现，类型转换有两个方向：将父类引用类型变量转换为子类类型，这种转换称为向下转型（downcast）；将子类引用类型变量转换为父类类型，这种转换称为向上转型（upcast）。向下转型需要强制转换，而向上转型是自动的。

## 接口

接口是Java中用来实现多重继承的一种结构。它无论是从组织形式还是使用角度来看,都可以看成是一种特殊的抽象类。接口需要使用关键字interface来定义,它也由成员属性和成员方法两部分构成,可以继承其他接口,也可以被其他接口和类继承。当类继承接口时一般称为“实现”。

### 接口的定义和继承

用户可以自行定义接口,一旦接口被定义,任何类都可以实现它。并且,一个类可以实现多个接口。

```java
[访问权限修饰符] interface 接口名 [extends父接口1,父接口2, ...]{
    
    //定义成员变量
    [public] [static] [final] 数据类型变量名=初始值;
    
    //定义成员方法
    [public] [abstract]返回类型 方法名([参数列表]);
}
```

*    interface表明这是一个接口,访问权限修饰符和类使用的一样,默认访问权是包访问权,一般用public来修饰它。和类的区别是,接口都是abstract的,所以无需用abstract来修饰。
*    extends和类中的一样,表明后面的列表是它的父接口。这里的父接口可以有若干个,各个接口名之间用逗号隔开。接口的继承和类的继承基本原则是一样的,但是更简单
*    接口中的成员变量都是常量。在默认情况下,接口中的成员变量具有public. static和final所联合规定的属性,这3个修饰符中, static和final没有替代的关键字,这意味所有的成员属性都是静态的、最终的,也就是静态常量。唯一可能改变的是访问权限修饰符public,但在接口中,不允许使用protected和private关键字,这意味着所有的属性都是public类型的。
*    接口中的成员方法都是抽象方法。在默认情况下,接口中的成员方法具有public和abstract所联合规定的属性。同样, public在这里不可改变, abstract没有可以替代的关键字。又由于abstract和static不可联合使用,所以不可能是静态方法,故所有的方法都是具有public访问权限的抽象实例方法。
*    接口中的方法都是抽象的,而构造方法不可能为抽象方法,因此,接口中没有构造方法。

### 接口实现

接口最终要用类来实现。类对接口的继承被称为接口的实现。不过类在实现接口时,不再使用关键字extends,而是使用implements.

若干没有继承关系的类可以实现同一个接口,一个类也可以实现多个接口,这些接口都称为该类的父接口或超接口。

由于接口中只有抽象方法,所以一个非抽象的类必须实现父接口中所有的方法。若父接口继承了其他的接口,则这些接口的抽象方法也要由该类来实现。若是该类同时是某些类的子类,而其父类实现了这些接口中的一部分方法,则该类只要能继承这些方法,也就视为对这些抽象方法的实现。

抽象类不受此限制,因为它可以将实现抽象方法的任务交由它的子类来完成。

```java
[类修饰符] class 类名 [extends 父类名] [implements 接口名1[,接口名2, ...]]{
    // 实现接口中的抽象方法
    public [返回值类型] 方法名 ([参数表]){
        //方法体
    }
}
```

## 终结处理与垃圾回收

### 对象销毁

对象不再使用时应该销毁。C++语言对象是通过delete语句手动释放，Java语言对象是由垃圾回收器（Garbage Collection）收集然后释放，程序员不用关心释放的细节。

垃圾回收器（Garbage Collection）的工作原理是：当一个对象的引用不存在时，认为该对象不再需要，垃圾回收器自动扫描对象的动态内存区，把没有引用的对象作为垃圾收集起来并释放。

### 对象的释放和垃圾收集机制

*    Java通过一个“垃圾收集机制”来解决对象释放后的内存管理问题。
*    当一个对象不再被引用的时候,垃圾收集机制会收回它占领的空间,供以后的新对象使用。
*    Java有堆内存和栈内存之分,其中堆是一个运行时数据区,类的实例(对象)从中分配空间。
*    Java虚拟机(JVM)的堆中储存着正在运行的应用程序所建立的所有对象,这些对象通过new、newarray, anewarray和multianewarray等指令建立,但是它们不需要程序代码来显式地释放。
*    一般来说,堆是由垃圾回收来负责的,尽管JVM规范并不要求特殊的垃圾回收技术,甚至根本就不需要垃圾回收,但是由于内存的有限性, JVM在实现的时候都有一个由垃圾回收所管理的堆。
*    垃圾回收是一种动态存储管理技术,它自动地释放不再被程序引用的对象,按照特定的垃圾收集算法来实现资源自动回收的功能。

#### 优点

*    垃圾收集能自动释放内存空间,减轻编程的负担。
*    它能使编程效率提高。
*    在没有垃圾收集机制的时候,可能要花许多时间来解决一个难懂的存储器问题。在用Java语言编程的时候,靠垃圾收集机制可大大缩短时间
*    其次是它保护程序的完整性,垃圾收集是Java语言安全性策略的一个重要部分。

#### 缺点

*    它的开销影响程序性能。Java虚拟机必须追踪运行程序中有用的对象, 而且最终释放没用的对象。这一个过程需要花费处理器的时间。
*    垃圾收集算法的不完备性,早先采用的某些垃圾收集算法就不能保证100%收集到所有的废弃内存。当然随着垃圾收集算法的不断改进以及软硬件运行效率的不断提升,这些问题都可以迎刃而解。为了节省存储空间,对象在不再需要之后就应该被释放掉。Java和C++一个显著的区别就是对象的释放是自动的,无需程序员操心。这极大地降低了程序员编程上的负担,也使得内存泄漏发生的风险降到最低。

### finalize()终结处理方法

像C++这样的语言,有显示的析构器方法,其中放置了一些当对象不再使用时所需要用到的清理代码,最常见的是回收分配给对象的内存空间。由于Java有自动垃圾收集机制,,不需要程序员干预,所以Java不支持析构器。

垃圾收集器只知道释放那些由new分配的内存,所以不知道如何释放对象的“特殊”内存,如果对象使用了内存之外的其他资源,如没有使用new创建的内存区域,当这类资源不再需要的时候, JVM将无法自动释放。

为解决这个问题, Java提供了一个finalize()方法,又称为结束方法。它是从Object类中继承下来的,每一个类都拥有此方法。它的工作原理是:一旦垃圾收集器准备好释放对象占用的存储空间,它首先调用finalize()方法,而且只有在下一次垃圾收集过程中,才会真正回收对象所占用的内存。所以如果使用finalize()方法,就可以在垃圾收集期间进行一些重要的清除或清扫工作。也就是说这个方法会在垃圾收集器清除对象之前被调用,如果用户觉得有必要,可以重写此方法,完成预定义的任务。

```java
protected void finalize(){
    语句序列
}
```

*    但是,程序员无法预测垃圾回收器会在何时启用,也就无法预测结束方法的执行时机,所以不要使用本方法来回收任何短缺的资源。

### Java垃圾回收的工作原理

*    Java的堆更像一个传送带,每分配一个新对象,它就往前移动一格。这意味着对象存储空间的分配速度相当快。Java的“堆指针”只是简单地移动到尚未分配的领域。也就是说,分配空间的时候, “堆指针”只管依次往前移动而不管后面的对象是否还要被释放掉。
*    如果可用内存耗尽之前程序就退出就再好不过了,这样的话垃圾回收器压根就不会被激活。但是由于“堆指针”只管依次往前移动,内存总会有被耗尽的时间,此时垃圾回收器就开始释放内存。
*    JVM会判断当堆栈或静态存储区没有对这个对象的引用时,就表示这个对象已经没有存在的意义了,它就应该被回收了。

#### 遍历堆上的对象找引用

叫做“引用计数法”,意思就是当有引用连接至对象时,引用计数加1,当引用离开作用域或被置为null时,引用计数减1。这种方法有个缺陷,如果对象之间存在循环引用,可能会出现“对象应该被回收,但引用计数却不为零”的情况。

#### 遍历堆栈或静态存储区的引用找对象。

在这种方式下, Java虚拟机采用一种“自适应”的垃圾回收技术,对于找到非垃圾的存活对象。

一种是“停止-复制”。理论上是先暂停程序的运行(所以它不属于后台回收模式) ,然后将所有存活的对象从当前堆复制到另一个堆,没有被复制的全是垃圾。当对象被复制到新堆上时,它们是一个挨着一个的,所以新堆保持紧凑排列(这也是为什么分配对象的时候“堆指针”只管依次往前移动) 。然后就可以按前述方法简单、直接地分配内存了。这将导致大量内存复制行为,内存分配是以较大的“块”为单位的。有了块之后,垃圾回收器就可以不往堆里复制对象了,而是直接就可以往废弃的块里复制对象。

另一种是“标记-清扫”。它的思路同样是从堆栈和静态存储区出发,遍历所有的引用,进而找出所有存活的对象。每当它找到一个存活对象,就会给对象一个标记。这个过程中不会回收任何对象。只有全部标记完成时,没有标记的对象将被释放,不会发生任何复制工作,所以剩下的堆空间是不连续的,然后垃圾回收器重新整理剩余的对象,使它们是连续排列的。当垃圾回收器第一次启动时,它执行的是“停止-复制”方式,因为这个时刻内存有太多的垃圾。然后Java虚拟机会进行监视,如果所有对象都很稳定,垃圾回收器的效率降低的话,就切换到“标记-清扫”方式;同样, Java虚拟机会跟踪“标记-清扫”效果,要是堆空间出现很多碎片,就会切换到“停止-复制”方式。这就是所谓的“自适应”技术。

实质上, “停止-复制”和“标记-清扫”无非就是“在大量的垃圾中找干净的东西和在大量干净的东西里找垃圾”。不同的环境用不同的方式,这样做完全是为了提高效率,要知道,无论哪种方式, Java都会先暂停程序的运行,所以,垃圾回收器的效率其实是很低的。

### 作用和意义

Java用效率换回了C++没有的垃圾回收器和运行时的灵活是十分明智的,而且通过垃圾回收器对对象重新排列,实现了一种高速的、有无限空间可供分配的堆模型。

# Lambda表达式

*    Lambda表达式是一个匿名函数（方法）代码块，可以作为表达式、方法参数和方法返回值。

## 特点

*    **可选类型声明：**不需要声明参数类型，编译器可以统一识别参数值。
*    **可选的参数圆括号：**一个参数无需定义圆括号，但多个参数需要定义圆括号。
*    **可选的大括号：**如果主体包含了一个语句，就不需要使用大括号。
*    **可选的返回关键字：**如果主体只有一个表达式返回值则编译器会自动返回值，大括号需要指定明表达式返回了一个数值。

## 函数式接口

*    Lambda表达式实现的接口不是普通的接口，称为是函数式接口，这种接口只能有一个方法。如果接口中声明多个抽象方法，那么Lambda表达式会发生编译错误

>    The target type of this expression must be a functional interface

```java
//可计算接口
@FunctionalInterface
public interface interfacename {
	
    // 只有一个函数
    public type function(){
        
        // TODO
    }
}
```

```java
public static function(interfacename inter,[parameter]){
    
    // TODO
    // inter.function([parameter]);
}
```

## 语法

```java
(参数列表)->{
    
    // Lambda表达体
};
```

```java
(parameters) -> expression
```

## Lambda表达式简化形式

### 省略参数类型

*    Lambda表达式可以根据上下文环境推断出参数类型。

### 省略return和大括号

*    如果Lambda表达式体中只有一条语句，那么可以省略return和大括号

## 作为参数使用Lambda表达式

*    Lambda表达式一种常见的用途是作为参数传递给方法。这需要声明参数的类型声明为函数式接口类型。

## 访问变量

-    Lambda表达式可以访问所在外层作用域内定义的变量，包括：成员变量和局部变量。

### 访问成员变量

*    静态方法中不能访问实例成员变量
*    实例方法中能够访问静态成员变量和实例成员变量
     *    当访问实例成员变量或实例方法时可以使用this，如果不与局部变量发生冲突情况下可以省略this。

### 捕获局部变量

*    Lambda表达式中捕获变量时，会将变量当成final的，在Lambda表达式中不能修改那些捕获的变量。
*    不管这个变量是否显式地使用final修饰，它都不能在Lambda表达式中修改变量

## 方法引用

*    Java 8之后增加了双冒号“::”运算符，该运算符用于“方法引用”，注意不是调用方法。“方法引用”虽然没有直接使用Lambda表达式，但也与Lambda表达式有关，与函数式接口有关。

### 语法形式

```java
类型名::静态方法        // 静态方法的方法引用
实例名::实例方法        // 实例方法的方法引用
```

# 异常处理

所谓异常处理机制,是指当程序出现错误后,程序如何处理。具体来说,异常·机制提供了程序退出的安全通道。当出现错误后,程序执行的流程发生改变,程序的控制权转移到异常处理器,在编程语言中引入这种机制,可大大简化程序员的工作量,使得程序更加易读、易懂、易维护。

## 特点

*    在应用程序遇到异常情况时,就会产生异常
*    发生异常时,控制流立即跳转到关联的异常处理程序(如果存在)
*    如果给定异常没有异常处理程序,则程序将停止执行,并显示一条错误信息
*    可能导致异常的操作通过try关键字来执行。异常处理程序是在异常发生时执行的代码块。在C#、Java等编程语言中,用catch关键字来定义异常处理程序
*    程序可以使用throw关键字显式地引发异常
*    异常对象包含有关错误的详细信息,其中包括调用堆栈的状态以及有关错误的文本说明。
*    即使引发了异常, finally块中的代码也会执行,从而使程序可以释放资源。

## 异常处理的两种模型

### 终止模型

在应用程序中,对异常进行处理一般有两种模型,一种称为“终止模型”,此模型也是Java与C语言所支持的模型。在这种模型中,将假设错误非常关键,此错误将导致程序无法返回到异常发生的地方继续向下执行,一旦这类异常被抛出,就表明程序错误已无法挽回,不能再回来继续执行代码。

### 恢复模型

另一种模型称为“恢复模型” ,意思是异常处理程序的工作是修正错误,然后重新尝试调用出问题的方法,尽可能地保证程序的后续执行。对于恢复模型,指的是当程序中有异常发生时,对异常情况进行处理并且保证程序的异常处理之后能继续执行。在这种情况下,抛出异常的过程也是异常处理方法被调用并执行的过程,在Java编程语言中,通过配置异常处理方法,可以使异常的程序得以恢复,也就是保证程序不因异常终止,而是调用异常处理方法来修正程序运行错误。

## 异常处理在编程中的优点

在编程语言中使用异常处理机制,至少在3个方面具有优势。

*    在用传统的语言编程时,程序员只能通过函数的返回值来知道错误信息。为了保证程序的健壮性,程序员不得不写下大量的if-else之类的判断语句,而且这些判断语句往往是嵌套的,导致程序的可读性降低,代码也难于维护。引入异常处理机制之后,程序员写程序时完全可以认为不会发生异常,一直按照正常的程序处理流程写下去,直到正常流程写完,之后再写捕获异常并进行相应的处理程序段就可以了。这就避免了书写大量if~else嵌套的麻烦。
*    由于函数只能有一个返回值,所以在很多情况下,难以区分返回的到底是正常值还是错误信息的代码。一种变通的处理方式是用全局变量errno来存储错误类型(在Windows API中,存在大量这样的函数) ,这要求程序员自己主动去查找此全局变量。这不仅增加了编程的负担,而且一旦程序员忘记做这项工作,就会导致一些意想不到的错误。采用异常处理机制后,则不会发生这种情况。一旦有错误发生,被调用的方法会抛出异常。无论调用者是否记得处理这个异常,正常的程序流程都会被终止。
*    在传统语言中,错误代码需要调用链上的函数一层一层返回。比如,有这样一个调用链: A-B-C-D,如果在D中发生错误,将返回一个错误代码,如果C和B不处理这个错误,就必须将这个错误代码返回给上一级。如果其中有一个函数的编写者忘记这项工作,函数A将得不到有关的错误信息。采用异常处理机制后,则不存在这个问题,在D中抛出的异常会存放在异常栈中,如果B和C不处理,仍然会传递给A。极端情况下,即使A不处理它,系统也会处理。

## Java异常的分类

#### 运行时异常

运行时异常也叫非检查型异常,此类异常不遵循处理或声明规则,大多数是由于程序设计不当而引发的错误,但这种错误要在运行期间才会发生和被发现。

#### 检查型异常

除了运行时异常外,其余的异常均为检查型异常,所以也称为“非运行时异常”。此类异常经编译器验证,对于声明抛出异常的任何方法,编译器将强制执行处理或声明规则,这类异常真正的发生仍然是在运行时,不过编译器在编译时会进行检查,一旦发现某些语句使得此类异常有产生的“可能”,就强制要求用户处理这类异常,否则不能通过编译。

#### 自定义异常

如果系统定义的异常不能满足用户需要,用户也可以自己定义异常。自定义异常是为了表示应用程序的一些错误类型,为代码可能发生的一个或多个问题提供新含义。可以显示代码多个位置之间的错误的相似性,也可以区分代码运行时可能出现的相似问题的一个或者多个错误,或给出应用程序中一组错误的特定含义。它们必须是Throwable的直接或间接子类,在实际编程中,多数程序员会将自定义异常写成Exception的直接子类。

## Java异常处理的原则

*    尽可能地处理异常:要尽可能地处理异常,如果条件确实不允许,无法在自己的代码中完成处理,就考虑声明异常。如果人为避免在代码中处理异常,仅作声明,则是一种错误和依赖的实践。
*    具体问题具体解决:异常的部分优点在于能为不同类型的问题提供不同的处理操作。有效异常处理的关键是识别特定故障场景,并开发解决此场景的特定相应行为。为了充分利用异常处理能力,需要为特定类型的问题构建特定的处理器块。
*    记录可能影响应用程序运行的异常:至少要采取一些永久的方式,记录下可能影响应用程序操作的异常。理想情况下,当然是在第一时间解决引发异常的基本问题。不过,无论采用哪种处理操作,一般总应记录下潜在的关键问题。别看这个操作很简单,但它可以帮助您用很少的时间来跟踪应用程序中复杂问题的起因。
*    根据情形将异常转化为业务上下文:若要通知一个应用程序特有的问题,有必要将应用程序转换为不同形式。若用业务特定状态表示异常,则代码更易维护。从某种意义上讲,无论何时将异常传到不同的上下文(即另一技术层) ,都应将异常转换为对新上下文有意义的形式。



## Throwable类

*    所有的异常类都直接或间接地继承于java.lang.Throwable类

### 方法

*    String getMessage()：获得发生异常的详细消息。 
*    void printStackTrace()：打印异常堆栈跟踪信息。 
*    String toString()：获得异常对象的描述。

```java
try {
    
    // TODO
} catch (Throwable throwable) {

    System.out.println("getMessage(): " + throwable.getMessage());
    System.out.println("toString(): " + throwable.toString());
    System.out.println("printStackTrace()输出信息如下: ");
    throwable.printStackTrace();
}
```

### Error和Exception

*    Throwable有两个直接子类：Error和Exception。

#### Error

*    Error是程序无法恢复的严重错误，程序员根本无能为力，只能让程序终止。

#### Exception

*    Exception是程序可以恢复的异常，它是程序员所能掌控的。

##### 受检查异常和运行时异常

###### 受检查异常

*    受检查异常是除RuntimeException以外的异常类。它们的共同特点是：编译器会检查这类异常是否进行了处理，即要么捕获（try-catch语句），要么不抛出（通过在方法后声明throws），否则会发生编译错误。它们种类很多，前面遇到过的日期解析异常ParseException。

###### 运行时异常

*    运行时异常是继承RuntimeException类的直接或间接子类。运行时异常往往是程序员所犯错误导致的，健壮的程序不应该发生运行时异常。它们的共同特点是：编译器不检查这类异常是否进行了处理，也就是对于这类异常不捕获也不抛出，程序也可以编译通过。由于没有进行异常处理，一旦运行时异常发生就会导致程序的终止，这是用户不希望看到的。

## 抛出异常

```java
throw 异常对象名;
```

```cpp
throw new 异常类名();
```

也就是说,一个方法中如果使用throw语句来抛出异常,要么自己捕获它,要么声明抛出了一个异常。声明抛出了异常,需要用throws关键字在方法的头部声明需要用throws关键字在方法的头部声明,格式如下

```java
[修饰符] [返回类型] 方法名 (参数表) throws 异常类名1[,异常类名2[, ...1]
```

## 捕获异常

*    try语句是必须的,它中间的语句序列一旦发生异常,将有可能被捕获。
*    catch语句是可选的,可以有0个或多个。括号中的异常类型必须各不相同。一旦try中发生了异常,系统将从上往下依次查找catch语句中是否有异常类型与其匹配,匹配成功就进入到该catch语句块中。
*    finally语句是资源保护块,也是可选的,可以有0个或1个。无论是否发生了异常,也无论异常是否被catch语句捕获, finally语句都会保证在最后被执行。
*    catch和finally语句至少要存在其中的一条。

### try-catch语句

#### 结构

##### 单层

```java
try{
    // 可能会发生异常的语句
}catch(Throwable e){
    // 处理异常e
}catch(Throwable e){
    // 处理异常e
}catch(Throwable e){
    // 处理异常e
}
```

##### 嵌套

```java
try{
    
    // TODO
    
    try{
        
        // TODO
    }catch(Throwable e){
    	// 处理异常e
	}catch(Throwable e){
    	// 处理异常e
	}
}catch(Throwable e){
    // 处理异常e
}catch(Throwable e){
    // 处理异常e
}
```

```java
try{
    
    // 语句块
    try{
        
        // 语句块
    }catch([异常类型] e){
        
        // 处理
    }
}catch([异常类型] e){
    
    // 处理
}
```

```cpp
try{
    
    // 语句块
}catch([异常类型] e){
    
    try{
        
        // 处理        
        // 语句块
    }catch([异常类型] e){
        
        // 处理
    }
}
```

##### 多重捕获

```java
try{
    
    // 可能会发生异常的语句
}catch(Exception1|Exception2){
    
    //TODO
}
```

#### try代码块

*    try代码块中应该包含执行过程中可能会发生异常的语句。一条语句是否有可能发生异常，这要看语句中调用的方法。
*    静态方法、实例方法和构造方法都可以声明抛出异常，凡是抛出异常的方法都可以通过try-catch进行捕获，当然运行时异常可以不捕获。

#### catch代码块

*    每个try代码块可以伴随一个或多个catch代码块，用于处理try代码块中所可能发生的多种异常。
*    在多个catch代码情况下，当一个catch代码块捕获到一个异常时，其他的catch代码块就不再进行匹配。

>    在捕获到异常之后，通过printStackTrace()语句打印异常堆栈跟踪信息，往往只是用于调试，给程序员提示信息。堆栈跟踪信息对最终用户是没有意义的，

*    在try-catch-finally语句中, catch可以出现多次,但异常类型必须互不相同,如果这些异常没有继承关系,则其顺序可以任意。但如果这些异常类有继承关系,则需要遵循子类,在前、父类在后的规则。这是由于在Java中,父类的变量可以指向子类的对象,而系统在查找匹配的异常类型时,是从上往下依次查找的,所以父类的异常类型必须写在后面。
*    一条throw语句一旦被执行,程序立即转入相应的异常处理程序段,它后面的语句就不再执行了(这一点类似于return语句) ,而且它所在的方法也不再返回有意义的值。一个方法中, throw语句可以有多条,但每一次最多只能执行其中的一条。一般情况下, throw语句写在判断语句块中,以避免每次重复执行该语句。

### 捕获多个异常

```java
try{
    
    // TODO
}catch([异常类型1]|[异常类型2] e){
    
    //TODO
}
```

### 忽略异常

```java
try{
    
    // TODO
}catch([异常类型] ignored){
    
}
```

## 处理字符串异常

### 声明

```cpp
[修饰符] 函数名 ([参数列表]) throws [异常类]{
	
    throw new [异常类];
}
```

### 处理

```java
try{
	
}catch([异常类]){

    System.out.println([异常类].getMessage())
}
```

## 释放资源

*    有时在try-catch语句中会占用一些非Java资源，需要程序员释放。为了确保这些资源能够被释放可以使用finally代码块或Java 7之后提供自动资源管理（Automatic Resource Management）技术。

### finally代码块

```java
try{
    // 可能会生成异常语句
}catch(Throwable e1){
    // 处理异常e1
}catch(Throwable e2){
    // 处理异常e2
}catch(Throwable eN){
    // 处理异常eN
}finally{
    // 释放资源
}
```

*    无论try正常结束还是catch异常结束都会执行finally代码块

### 自动资源管理

-    使用finally代码块释放资源会导致程序代码大量增加，一个finally代码块往往比正常执行的程序还要多。在Java 7之后提供自动资源管理（Automatic Resource Management）技术，可以替代finally代码块，优化代码结构，提高程序可读性。

```java
try(声明或初始化资源语句){
    // 可能会生成异常语句
}catch(Throwable e1){
    // 处理异常e1
}catch(Throwable e2){
    // 处理异常e2
}catch(Throwable eN){
    // 处理异常eN
}
```

*    在try语句后面添加一对小括号“()”，其中是声明或初始化资源语句，可以有多条语句语句之间用分号“;”分隔。

## throws与声明方法抛出异常

*    在一个方法中如果能够处理异常，则需要捕获并处理。但是本方法没有能力处理该异常，捕获它没有任何意义，则需要在方法后面声明抛出该异常，通知上层调用者该方法有可以发生异常。

```java
class className {
    
    [public | protected | private ] [static] [final | abstract] [native] [synchronized] type methodName([paramList]) [throws exceptionList] {
        
        // TODO
    }
}
```

*    其中参数列表之后的[throws exceptionList]语句是声明抛出异常。方法中可能抛出的异常（除了Error和RuntimeException及其子类外）都必须通过throws语句列出，多个异常之间采用逗号（,）分隔。

### 自定义异常类

```java
public class MyException extends Exception{
    public MyException{
        
        // TODO
    }
    
    public MyException(String message){

        super(message);
    }
}
```

*    自定义异常类一般需要提供两个构造方法，一个是无参数的默认构造方法，异常描述信息是空的；另一个是字符串参数的构造方法，message是异常描述信息，getMessage()方法可以获得这些信息。

### throw与显式抛出异常

```java
throw Throwable或其子类的实例
```

# 泛型

-    使用泛型可以最大限度地重用代码、保护类型的安全以及提高性能。泛型特性对Java影响最大是集合框架的使用。
-    强制类型转换是有风险的，如果不进行判断就臆断进行类型转换会发生ClassCastException异常。
-    在集合中如果没有使用泛型，Eclipse等IDE工具都会警告。

## 泛型的本质

泛型在本质上是指类型参数化。所谓类型参数化,是指用来声明数据的类型本身,也是可以改变的,它由实际参数来决定。在一般情况下,实际参数决定了形式参数的值。而类型参数化,则是实际参数的类型决定了形式参数的类型。

在泛型出现之前, Java的程序员可以采用一种变通的办法:将参数的类型均声明为, Object 类型。由于Object类是所有类的父类,所以它可以指向任何类对象,但这样做不能保证类型安全。

## 泛型类

```java
public class 类名<泛型>{
    
    // TODO
}
```

### 有界类型

在指定一个类型参数时,可以指定一个上界,声明所有的实际类型都必须是这个超类的直接或间接子类。

```cpp
class classname <T extends superclass>
```

### 通配符参数

```cpp
genericClassName <?>
```

通配符无法将上界改变得超出泛型类声明时的上界范围。

通配符是用来声明一个泛型类的变量的,而不能创建一个泛型类。

## 泛型方法

```cpp
[访问权限修饰符] [static] [final] <类型参数列表> 返回值类型 方法名([形式参数列表])
```

*    访问权限修饰符(包括private, public和protected) 、 static和final都必须写在类型参数列表的前面。
*    返回值类型必须写在类型参数表的后面。
*    泛型方法可以写在一个泛型类中,也可以写在一个普通类中。
*    由于在泛型类中的任何方法,本质上都是泛型方法,所以在实际使用中,很少会在泛型类中再用上面的形式来定义泛型方法。
*    类型参数可以用在方法体中修饰局部变量,也可以用在方法的参数表中,修饰形式参数。

### 使用方法

```cpp
<对象名|类名>.<实际类型>方法名(实际参数表);
```

```cpp
[对象名|类名].方法名(实际参数表);
```

如果泛型方法是实例方法,要使用对象名作为前缀。如果是静态方法,则可以使用对象名或类名作为前缀。如果是在类的内部调用,且采用第二种形式,则前缀都可以省略。注意到这两种调用方法的差别在于,前面是否显示地指定了实际类型。

是否要使用实际类型,需要根据泛型方法的声明形式以及调用时的实际情况(就是看编译器能否从实际参数表中获得足够的类型信息)来决定。

## 继承泛型类

和普通类一样,泛型类也是可以继承的,任何一个泛型类都可以作为父类或子类。不过泛型类与非泛型类在继承时的主要区别在于:泛型类的子类必须将泛型父类所需要的类型参数,沿着继承链向上传递。这与构造方法参数必须沿着继承链向上传递的方式类似。

### 以泛型类为父类

当一个类的父类是泛型类时,这个子类必须要把类型参数传递给父类,所以这个子类也必定是泛型类。

使用泛型子类和使用其他的泛型类没有区别,使用者根本无需知道它是否继承了其他的类。

```java
public derivedGen<T> extends Gen<T>{
    // TODO
}
```

```java
public derivedGen<R> extends Gen<T>{
    // TODO
}
```

### 以非泛型类为父类

```java
public derivedGen<T> extends Gen{
    // TODO
}
```

### 运行时类型识别

由于在JVM中,泛型类的对象总是一个特定的类型,此时,它不再是泛型。所以,所有的类型查询都只会产生原始类型,无论是getClass()方法,还是instanceof操作符。

## 擦拭

### 擦拭的概念及原理

Java在JDK 1.5以前的版本中是没有泛型的。为了保证对以前版本的兼容, Java采用了与C++的模板完全不同的方式来处理泛型。也可以说, Java的泛型是伪泛型。因为,在编译期间,所有的泛型信息都会被擦除掉。正确理解泛型概念的首要前提是理解类型擦除,即type erasure.

Java中的泛型基本上都是在编译器这个层次来实现的。在生成的Java字节码中是不包含泛型中的类型信息的。使用泛型的时候加上的类型参数会在编译器编译的时候去掉。这个过程被称为类型擦除。

类型擦除的关键在于从泛型的类型中清除类型参数的相关信息,并且在必要的时候添加类型检查和类型转换的方法。类型擦除可以简单地理解为将泛型Java代码转换为普通Java代码。从编译器的层次来理解,就是将泛型Java代码直接转换成普通的Java字节码。

>    javap是由系统提供的一个反编译命令,可以获取class文件中的信息或者是反汇编代码。

所有被T占据的位置都被java.lang.Object所取代

```java
public class Gen<T>{   
    // TODO
}
```

```java
public class Gen extends java.lang.Object{
    // TODO
}
```

如果类型参数指定了上界,那么就会用上界类型来代替它

在使用泛型对象时,实际上所有的类型信息也都会被擦拭,编译器自动插入强制类型转换。

### 擦拭带来的错误

擦拭是一种很巧妙的办法,但它有时候会带来一些意想不到的错误:两个看上去并不相同的泛型类或是泛型方法,由于擦拭的作用,最后会得到相同的类和方法。这种错误,也被称为冲突。

#### 静态成员共享问题

在泛型类中可以有静态的属性或者方法。前面已经介绍过,静态方法不能使用类型参数。静态成员不能使用类型参数或者是本泛型类的对象

#### 重载冲突问题

```java
void conflict (T o){ } 
void conflict (Object o){ }
```

#### 接口实现问题

由于接口也可以是泛型接口,而一个类又可以实现多个泛型接口,所以也可能会引发冲突。

```java
class foo implements Comparable<Integer>, Comparable<Long>
```

## 泛型的局限

### 不能使用基本类型

泛型中使用的所有类型参数都是类类型,不能使用基本类型。比如,可以用Generic\<Integer>,而不能用Generiecint。原因很简单,基本类型无法用Object来替换。

### 不能使用泛型类异常

Java中不能抛出也不能捕获泛型类的异常。事实上,泛型类继承Throwable及其子类都不合法

```java
class MyException<t> extends Exception{...}
```

### 不能使用泛型数组

```java
Generic<Integer> arr[] = new Generic<Ingeger> [10];
```

### 不能实例化参数类型对象

不能直接使用参数类型来构造一个对象。

```java
public class foos T >{
    Tob=new T(); //错误
}
```

## 使用泛型

*    泛型对于Java影响最大就是集合了，Java 5之后所有的集合类型都可以有泛型类型，可以限定存放到集合中的类型。

### LIst

#### 声明

```java
List<type> container = new ArrayList<type>();
```

#### 迭代器

```java
Iterator<type> iter = container.iterator();
while(iter.hasNext()){
    // TODO
}
```

#### for-each

```java
for(type item:container){
    // TODO
}
```

### Map

#### 声明

```java
Map<type1,type2> container = new HashMap<type1,type2>();
```

#### 迭代器

```java
Iterator<Map.Entry<type1,type2>> iter = container.entrySet().iterator();
while(iter.hasNext()){
    
    Map.Entry<type1,type2> entry = iter.next();
    // TODO
}
```

#### for-each

```java
for (Map.Entry<type1, type2> entry : container.entrySet()) {
    // TODO
}
```

## 自定义泛型类

```java
public class name<T>{
    
    // TODO
}
```

## 自定义泛型方法

```java
[public|protected|private] [static] <T> [void|type] functionname([parameter]){
    
    // TODO
}
```

## 泛型接口

```cpp
interface 接口名<类型参数表>
```

通常,如果一个类实现了一个泛型接口,则此类也是泛型类。否则,它无法接受传递给接口的类型参数。

# 文件管理

*    Java语言使用File类对文件和目录进行操作，查找文件时需要实现FilenameFilter或FileFilter接口。另外，读写文件内容可以通过FileInputStream、FileOutputStream、FileReader和FileWriter类实现，它们属于I/O流

## File类

### 构造方法

| 方法                             | 说明                                                         |
| :------------------------------- | ------------------------------------------------------------ |
| File(File parent, String child)  | 创建一个File对象,以parent的绝对路径加上child成为新的目录或文件 |
| File(String pathname)            | 创建一个File对象,将pathname指定路径转换为绝对路径            |
| File(String parent,String child) | 创建一个File对象,以parent的绝对路径加上child成为新的目录或文件 |
| File(URI uri)                    | 创建一个File对象,将URI转换为绝对路径                         |

### 获得文件信息

| 方法                      | 说明                         |
| ------------------------- | ---------------------------- |
| String getName( )         | 获得文件的名称，不包括路径   |
| String getPath( )         | 获得文件的路径               |
| String getAbsolutePath( ) | 获得文件的绝对路径           |
| String getParent( )       | 获得文件的上一级目录名       |
| long lastModified( )      | 获得文件最近一次修改的时间   |
| long length( )            | 获得文件的长度，以字节为单位 |
| boolean isHidden( )       | 测试文件是否为隐藏属性       |

#### 文件创建时间

```java
File file = new File(pathname);
Date date=new Date(file.lastModified());
SimpleDateFormat simpleDateFormat=new SimpleDateFormat("yyyy-MM-dd HH:mm:ss ");
System.out.println(simpleDateFormat.format(date));
```

### 文件属性

| 方法                         | 说明                                 |
| ---------------------------- | ------------------------------------ |
| boolean exists( )            | 测试当前File对象所表示的文件是否存在 |
| boolean canWrite( )          | 测试当前文件是否可写                 |
| boolean canRead( )           | 测试当前文件是否可读                 |
| boolean isFile( )            | 测试当前文件是否是文件               |
| boolean isDirectory( )       | 测试当前文件是否是目录               |
| int compareTo(File pathname) | 按字典值比较两个File对象的绝对路径   |

### 文件操作

| 方法                         | 说明                                                         |
| ---------------------------- | ------------------------------------------------------------ |
| boolean delete( )            | 删除当前文件。成功返回 true，否则返回false                   |
| boolean renameTo(File dest)  | 将重新命名当前File对象所表示的文件。成功返回 true，否则返回false |
| **boolean createNewFile( )** | **创建一个空文件**                                           |
| boolean delete( )            | 删除文件或目录                                               |

### 目录操作

| 方法                                    | 说明                                                         |
| --------------------------------------- | ------------------------------------------------------------ |
| **boolean mkdir( )**                    | **创建当前File对象指定的目录**                               |
| String[] list()                         | 返回当前目录下的文件和目录，返回值是字符串数组               |
| String[] list(FilenameFilter filter)    | 返回当前目录下满足指定过滤器的文件和目录，参数是实现FilenameFilter接口对象，返回值是字符串数组 |
| File[] listFiles()                      | 返回当前目录下的文件和目录，返回值是File数组                 |
| File[] listFiles(FilenameFilter filter) | 返回当前目录下满足指定过滤器的文件和目录，参数是实现FilenameFilter接口对象，返回值是File数组 |
| boolean renameTo(File dest)             | 将文件改名成dest对象所指示的名字                             |
| boolean setLastModified(long time)      | 设置文件或目录的时间                                         |
| boolean setReadOnly()                   | 将文件或目录设置为只读                                       |

对目录操作有两个过滤器接口：FilenameFilter和FileFilter。它们都只有一个抽象方法accept， 

*    FilenameFilter接口中的accept方法如下：
     *    boolean accept(File dir, String name)：测试指定dir目录中是否包含文件名为name的文件。
*    FileFilter接口中的accept方法如下：
     *    boolean accept(File pathname)：测试指定路径名是否应该包含在某个路径名列表中。

## RandomAccessFile文件随机访问

| 方法                                        | 说明                                                         |
| ------------------------------------------- | ------------------------------------------------------------ |
| void close()                                | 关闭此随机访问文件流并释放与流相关联的任何系统资源。         |
| FileChannel getChannel()                    | 返回与此文件关联的唯一的FileChannel对象。                    |
| FileDescriptor getFD()                      | 返回与此流关联的不透明文件描述符对象。                       |
| long getFilePointer()                       | 返回此文件中的当前偏移量。                                   |
| long length()                               | 返回此文件的长度。                                           |
| int read()                                  | 从该文件读取一个字节的数据。                                 |
| int read(byte[] b)                          | 从该文件读取最多 b.length字节的数据到字节数组。              |
| int read(byte[] b, int off,  int len)       | 从该文件读取最多 len个字节的数据到字节数组。                 |
| boolean readBoolean()                       | 从此文件读取一个 boolean 。                                  |
| byte readByte()                             | 从此文件中读取一个带符号的八位值。                           |
| char readChar()                             | 从此文件中读取一个字符。                                     |
| double readDouble()                         | 从此文件读取 double 。                                       |
| float readFloat()                           | 从此文件读取一个 float 。                                    |
| void readFully(byte[] b)                    | 从此文件读取 b.length字节到字节数组，从当前文件指针开始。    |
| void readFully(byte[] b,  int off, int len) | 从此文件中读取 len个字节到字节数组，从当前文件指针开始。     |
| int readInt()                               | 从该文件读取一个带符号的32位整数。                           |
| String readLine()                           | 从此文件中读取下一行文本。                                   |
| long readLong()                             | 从该文件中读取一个带符号的64位整数。                         |
| short readShort()                           | 从此文件中读取一个已签名的16位数字。                         |
| int readUnsignedByte()                      | 从此文件中读取一个无符号的八位数字。                         |
| int readUnsignedShort()                     | 从该文件中读取一个无符号的16位数字。                         |
| String readUTF()                            | 从该文件读取字符串。                                         |
| void seek(long pos)                         | 设置文件指针偏移，从该文件的开头测量，发生下一次读取或写入。 |
| void setLength(long newLength)              | 设置此文件的长度。                                           |
| int skipBytes(int n)                        | 尝试跳过 n字节的输入丢弃跳过的字节。                         |
| void write(byte[] b)                        | 从指定的字节数组写入 b.length个字节到该文件，从当前文件指针开始。 |
| void write(byte[] b, int off,  int len)     | 从指定的字节数组写入 len个字节，从偏移量 off开始写入此文件。 |
| void write(int b)                           | 将指定的字节写入此文件。                                     |
| void writeBoolean(boolean v)                | 将 boolean写入文件作为一个字节值。                           |
| void writeByte(int v)                       | 将 byte写入文件作为单字节值。                                |
| void writeBytes(String s)                   | 将字符串作为字节序列写入文件。                               |
| void writeChar(int v)                       | 将 char写入文件作为两字节值，高字节为先。                    |
| void writeChars(String s)                   | 将一个字符串作为字符序列写入文件。                           |
| void writeDouble(double v)                  | 双参数传递给转换 long使用 doubleToLongBits方法在类 Double ，然后写入该 long值到该文件作为一个八字节的数量，高字节。 |
| void writeFloat(float v)                    | 浮子参数的转换 int使用 floatToIntBits方法在类 Float ，然后写入该 int值到该文件作为一个四字节数量，高字节。 |
| void writeInt(int v)                        | 将 int写入文件为四个字节，高字节 int 。                      |
| void writeLong(long v)                      | 将 long写入文件为八个字节，高字节为先。                      |
| void writeShort(int v)                      | 将 short写入文件作为两个字节，高字节优先。                   |
| void writeUTF(String str)                   | 以机器无关的方式使用 modified UTF-8编码将字符串写入文件。    |

## 文件的访问

*    在访问目录中的条目之前调用FileVisitResult preVisitDirectory(T dir),它返回一个FileVisitResult枚举值,来告诉文件访问程序API下一步做什么。
*    当目录由于某些原因无法访问时,调用FileVisitResult preVisitDirectoryFailed(T dir,IOException exception)。在第二个参数中指出了导致访问失败的异常
*    在当前目录中有文件被访问时,调用FileVisitResult visitFile(T file, BasicFileAttributes attribs)。该文件的属性传递给第二个参数。
*    当访问文件失败时,调用FileVisitResult visitFileFailed(T file, IOExceptionexception)。第二个参数指明导致访问失败的异常。
*    完成对目录及其子目录的访问后,调用FileVisitResult postVisitDirectory(T dir,IOException exception),当目录访问成功时,异常参数为空,或者包含导致目录访问过早结束的异常。

```java
FileVisitor<Path> myFileVisitor = new SimpleFileVisitor<Path>() {
	// 需要传入参数Path和BasicFileAttributes，分别表示路径和属性对象
	public FileVisitResult preVisitDirectory(Path dir, BasicFileAttributes attrs) {

		// 输出想要访问的目录名称
		System.out.println("将要访问的目录为: " + dir);
		return FileVisitResult.CONTINUE;
	}

	public FileVisitResult visitFile(Path file, BasicFileAttributes attributes) {

		System.out.println("正在访问的文件为: " + file + ",此文件的大小为: " + attributes.size());
		return FileVisitResult.CONTINUE;
	}
};

// 获取一个将要访问的目录路径的Path实例
Path headDir = Paths.get("Dir1");

// 通过walkFileTree方法，实现目录的遍历
Files.walkFileTree(headDir, myFileVisitor);
```

# I/O流概述

*    Java将数据的输入输出（I/O）操作当作“流”来处理，“流”是一组有序的数据序列。“流”分为两种形式：输入流和输出流，从数据源中读取数据是输入流，将数据写入到目的地是输出流。
*    以CPU为中心，从外部设备读取数据到内存，进而再读入到CPU，这是输入（Input，缩写I）过程；将内存中的数据写入到外部设备，这是输出（Output，缩写O）过程。所以输入输出简称为I/O。
*    所有的输入形式都抽象为输入流，所有的输出形式都抽象为输出流，它们与设备无关。

## Java I/O体系

*    基于字节操作的IO接口: InputStream和OutputStream
*    基于字符操作的IO接口: Writer和Reader
*    基于磁盘操作的IO接口: File
*    基于网络操作的IO接口; Socket

## 字节流

### 字节输入流

| 类                   | 描述                                      |
| -------------------- | ----------------------------------------- |
| FileInputStream      | 文件输入流                                |
| ByteArrayInputStream | 面向字节数组的输入流                      |
| PipedInputStream     | 管道输入流，用于两个线程之间的数据传递    |
| FilterInputStream    | 过滤输入流，它是一个装饰器扩展其他输入流  |
| BufferedInputStream  | 缓冲区输入流，它是FilterInputStream的子类 |
| DataInputStream      | 面向基本数据类型的输入流                  |

### 字节输出流

| 类                    | 描述                                       |
| --------------------- | ------------------------------------------ |
| FileOutputStream      | 文件输出流                                 |
| ByteArrayOutputStream | 面向字节数组的输出流                       |
| PipedOutputStream     | 管道输入流，用于两个线程之间的数据传递     |
| FilterOutputStream    | 过滤输出流，它是一个装饰器扩展其他输出流   |
| BufferedOutputStream  | 缓冲区输出流，它是FilterOutputStream的子类 |
| DataOutputStream      | 面向基本数据类型的输出流                   |

### InputStream

| 方法                                  | 说明                                                  |
| ------------------------------------- | ----------------------------------------------------- |
| int  available()                      | 返回流中可供读入(或跳过)的字节数目                    |
| void  close()                         | 关闭输入流，释放相关资源                              |
| void  mark(int readlimit)             | 标记输入流中目前的位置                                |
| boolean  markSupported()              | 测试输入流是否支持mark和reset方法                     |
| abstract  int read()                  | 从流中读入一个字节的数据                              |
| int  read(byte[] b)                   | 从流中读入最多b.length大小的数据，并存储到b中         |
| int  read(byte[] b, int off, int len) | 读入最多len个数据存储到b中，off指示开始存放的偏移位置 |
| void  reset()                         | 将流重新置位到mark方法最后一次执行的位置              |
| long  skip(long n)                    | 跳过并抛弃n个流中的数据                               |



### OutputStream

<table>
    <tr><th>方法</th><th>声明</th></tr>
    <tr><th>void close()</th><th>关闭输出流并释放相关资源</th></tr>
    <tr><th>void flush()</th><th>清空缓冲区并强制缓冲区中的数据写出去</th></tr>
    <tr><th>void write(byte[] b)</th><th>将数据b中所有数据写出到流中</th></tr>
    <tr><th>void write(byte[] b,int off,int len)</th><th>将数据b中从off位置起的n个数据写出到流中</th></tr>
    <tr><th>Abstract void write(int b)</th><th>将指定数据b写入到流中</th></tr>
</table>



### FileInputStream

| 构造方法                               | 说明                                           |
| -------------------------------------- | ---------------------------------------------- |
| FileInputStream(File  file)            | 以指定名字的文件对象为数据源建立一个文件输入流 |
| FileInputStream(FileDescriptor  fdObj) | 根据文件描述符对象建立一个文件输入流           |
| FileInputStream(String  name)          | 以指定名字的文件尾数据源建立一个文件输入流     |

#### 控制台上输入

```java
FileInputStream fileInputStream=new FileInputStream(FileDescriptor.in);// FileDescriptor.in表示系统标准输入设备
```

### FileOutputStream

| 方法                                           | 说明                                                         |
| ---------------------------------------------- | ------------------------------------------------------------ |
| FileOutputStream(File  file)                   | 以指定名字的文件对象为接收端建立文件输入流                   |
| FileOutputStream(File  file, boolean append)   | 以指定名字的文件对象为接收端建立文件输入流，append为真时，输出的数据将被追加到文件尾，否则将以覆盖的方式写入文件 |
| FileOutputStream(FileDescriptor  fdObj)        | 根据文件描述符对象建立一个文件输出流                         |
| FileOutputStream(String  name)                 | 以指定名字的文件为接收接收端建立文件输出流                   |
| FileOutputStream(String  name, boolean append) | 以指定名字的文件尾接收端建立文件输出流，append为真时，输出的数据将被追加到文件尾，否则将以覆盖的方式写入文件 |


#### 控制台上输出

```java
FileOutputStream fileOutputStream =new FileOutputStream(FileDescriptor.out);
```

## 字符流

### 字符输入流

| 类                | 描述                                                       |
| ----------------- | ---------------------------------------------------------- |
| FileReader        | 文件输入流                                                 |
| CharArrayReader   | 面向字符数组的输入流                                       |
| PipedReader       | 管道输入流，用于两个线程之间的数据传输                     |
| FilterReader      | 过滤输入流，它是装饰器扩展其他输入流                       |
| BufferedReader    | 缓冲区输入流，它也是装饰器，它不是FilterReader的子类       |
| InputStreamReader | 把字节流转换为字符流，它也是一个装饰器，是FileReader的父类 |

### 字符输出流

| 类                | 描述                                                       |
| ----------------- | ---------------------------------------------------------- |
| FileWriter        | 文件输出流                                                 |
| CharArrayWriter   | 面向字符数组的输出流                                       |
| PipedWriter       | 管道输出流，用于两个线程之间的数据传输                     |
| FilterWriter      | 过滤输出流，它是装饰器扩展其他输入流                       |
| BufferedWriter    | 缓冲区输出流，它也是装饰器，它不是FilterWriter的子类       |
| InputStreamWriter | 把字节流转换为字符流，它也是一个装饰器，是FileWriter的父类 |

### InputStreamReader

| 构造方法                                               | 说明                                                     |
| ------------------------------------------------------ | -------------------------------------------------------- |
| InputStreamReader(InputStream  in)                     | 创建一个建立在输入流in之上的对象，采用系统默认的编码方式 |
| InputStreamReader(InputStrea  in, Charset cs)          | 创建一个建立在输入流in之上的对象，采用cs对象指定的字符集 |
| InputStreamReader(InputStream  in, CharsetDecoder dec) | 创建一个建立在输入流in之上的对象，采用dec指定的解码方式  |
| InputStreamReader(InputStream  in, Stream charsetName) | 创建一个建立在输入流in之上的对象，采用指定名称的字符集   |


#### 控制台上输入

```java
InputStreamReader inputStreamReader = new InputStreamReader(System.in);
```

### OutputStreamWriter

| 构造方法                                                  | 说明                                                      |
| --------------------------------------------------------- | --------------------------------------------------------- |
| OutputStreamWriter(OutputStream  out)                     | 创建一个建立在输出流out之上的对象，采用系统默认的编码方式 |
| OutputStreamWriter(OutputStream  out, Charset cs)         | 创建一个建立在输出流out之上的对象，采用cs对象指定的字符集 |
| OutputStreamWriter(OutputStream  out, CharsetEncoder enc) | 创建一个建立在输出流out之上的对象，采用enc指定的编码方式  |
| OutputStreamWriter(OutputStream  out, String charsetName) | 创建一个建立在输出流out之上的对象，采用指定名称的字符集   |


#### 控制台上输出

```java
OutputStreamWriter outputStreamWriter = new OutputStreamWriter(System.out);
```

### BufferedInputStream

#### 构造方法

*    BufferedInputStream(InputStream in)：通过一个底层输入流in对象创建缓冲流对象，缓冲区大小是默认的，默认值8192。
*    BufferedInputStream(InputStream in, int size)：通过一个底层输入流in对象创建缓冲流对象，size指定的缓冲区大小，缓冲区大小应该是2的n次幂，这样可提供缓冲区的利用率。

### BufferedOutputStream

#### 构造方法

*    BufferedOutputStream(OutputStream out)：通过一个底层输出流out 对象创建缓冲流对象，缓冲区大小是默认的，默认值8192。
*    BufferedOutputStream(OutputStream out, int size)：通过一个底层输出流out对象创建缓冲流对象， size指定的缓冲区大小，缓冲区大小应该是2的n次幂，这样可提高缓冲区的利用率。

## 字节流转换字符流

### InputStreamReader

*    InputStreamReader(InputStream in)：将字节流in转换为字符流对象，字符流使用默认字符集。
*    InputStreamReader(InputStream in, String charsetName)：将字节流in转换为字符流对象， charsetName指定字符流的字符集，字符集主要有：US-ASCII、ISO-8859-1、UTF-8和UTF-16。如果指定的字符集不支持会抛出UnsupportedEncodingException异常。

### OutputStreamWriter

*    OutputStreamWriter(OutputStream out)：将字节流out转换为字符流对象，字符流使用默认字符集。
*    OutputStreamWriter(OutputStream out,String charsetName)：将字节流out转换为字符流对象， charsetName指定字符流的字符集，如果指定的字符集不支持会抛出UnsupportedEncodingException异常。

## 顺序输入流

$File\longrightarrow InputStream\longrightarrow SequenceInputStream$

顺序输入流( SequencelnputStream)可以将多个输入流顺序连接在一起。在进行输入时,顺序输入流依次打开每个输入流并读取数据,在读取完毕后将该流关闭,然后自动切换到下一个输入流。它的构造方法如下。

*    SequencelnputStream(Enumeration e):创建一个串行输入流,连接枚举对象e中的所有输入流。
*    SequencelnputStream(InputStream s1,InputStream s2):创建一个串行输入流,连接流s1和s2

## 管道输入输出流

管道输入输出流(PipedInputStream和PipedOutputStream)可以实现程序内部线程间的通信或不同程序间的通信。

*    PipedInputStream是一个通信管道的接收端,它必须与一个作为发送端的PipedOutputStream对象相连。
*    PipedOutputStream是通信管道的发送端,它必须与PipedInputStream对象相连。

### 连接方法

*    PipedInputStream (PipedOutputStream src) :创建一个管道输入流,并将其连接到src指定的管道输出流。
*    PipedOutputStream (PipedInputStream src) :创建一个管道输出流,并将其连接到src指定的管道输入流。

## 过滤输入输出流

$File\longrightarrow FileInputStream/FileOutputStream\longrightarrow DataInputStream/DataOutputStream$

过滤输入输出流( FilterlnputStream和FilterOutputStream)是两个抽象类,它们又分别派生出DatalnputStream和DataOutputStream等子类。

过滤输入输出流的主要特点是,其建立在基本输入输出流之上,能够对基本输入输出流所传输的数据进行指定类型或格式的转换,即可实现对二进制字节数据的理解和编码转换,常用的过滤流是数据输入输出流DatalnputStream和DataOutputStream,它们可用于对不同类型数据的读写

其构造方法如下。

*    DatalnputStream(InputStream in):建立一个新的数据输入流,从指定的输入流in中读数据。
*    DataOutputStream(OutputStream out):建立一个新的数据输出流,向指定的输出流out中写数据。

DatalnputStream中定义了多个针对不同类型数据的读方法,如readByte()、readBoolean(), readChar(), readInt(), readFloat()和readDouble()等。同样, DataOutputStream也定义了对应的针对不同类型数据的输出方法,如writeByte(), writeChar(),writelnt()writeFloat()和writeDouble()等。

## 控制台IO处理

### 控制台输入类Scanner

| 方法                         | 说明                                                       |
| ---------------------------- | ---------------------------------------------------------- |
| boolean  hasNext()           | 测试是否还有下一个输入项                                   |
| boolean  hasNextByte()       | 测试下一个输入项是否能按照默认的进制被解释成为一个byte数据 |
| boolean  hasNextDouble()     | 测试下一个输入项是否能被解释成为一个double数据             |
| boolean  hasNextInt()        | 测试下一个输入是否能被解释成为一个int数据                  |
| byte  nextByte()             | 以byte类型获取下一个输入项                                 |
| double  nextDouble()         | 以double类型获取下一个输入项                               |
| int  nexInt()                | 以int类型获取下一个输入项                                  |
| String  nextLine()           | 读到本行末尾                                               |
| Scanner  useRadix(int radix) | 设置本对象的默认进制                                       |


#### 控制台上输入

```java
Scanner scanner = new Scanner(System.in);
```

## 格式化输出printf

#### 格式转换符

| 格式转换符 | 作用                                                 |
| ---------- | ---------------------------------------------------- |
| d          | 以十进制形式输出整数(以实际长度输出,正数不输出符号)  |
| o          | 以无符号八进制形式输出整数(不输出前导0)              |
| x或X       | 以无符号十六进制形式输出整数(不输出前导0x)           |
| a或A       | 以十六进制形式输出浮点数                             |
| c或C       | 以字符形式输出,只输出一个字符                        |
| s或S       | 输出字符串                                           |
| f          | 以小数形式输出单、双精度数,隐含输出6位小数           |
| e或E       | 以标准指数形式输出单、双精度数,数字部分小数位数为6位 |
| g或G       | 选用%f或%e输出宽度较短的一种格式,不输出无意义的0     |
| h或H       | 输出哈希码                                           |
| b或B       | 输出布尔值                                           |
| tx         | 输出日期时间(x可用其他符号替换)                      |
| n          | 输出与平台有关的行分隔符                             |
| %          | 输出%本身                                            |


#### 格式修饰符

| 格式修饰符 | 作用                                                         |
| ---------- | ------------------------------------------------------------ |
| +          | 输出正数和负数前面的符号                                     |
| 空格       | 在正数之前添加空格                                           |
| m.n        | 输出项总共占m位,小数部分占n位,  m和n都必须是正整数常量。默认为右对齐 |
| 0          | 数字前面补0,凑齐指定宽度                                     |
| -          | 左对齐,后面补空格                                            |
| (          | 将负数输出在括号内                                           |
| ,          | 数字每3位添加一个“, ”号作为分隔符                            |
| #          | 如果是f格式,输出小数点,即便小数部分为0                       |
| #          | 如果是x或0格式,添加前缀0x或o                                 |
| ^          | 十六进制数以大写形式输出                                     |
| $          | 指定将被格式化的参数索引                                     |
| <          | 格式化前面说明的数值                                         |

## Java序列化技术

要让一个类能够序列化,首先,这个类要实现Serializable接口。

```java
class [类名] implements Serializable{ ....}
```

由于Serializable接口中没有任何方法,所以不需要对自己的类进行任何修改。随后要做的事情,是需要打开一个ObjectOutputStream对象

```java
FileOutputStream fileOutputStream = new FileOutputStream("[文件名]");
ObjectOutputStream out = new ObjectOutputStream (fileOutputStream);
```

随后只需要使用ObjectOutputStream类中的writeObject方法

```java
// 初始化类
out.writeObject ([类名]);
```

要读取对象,首先要取得一个ObjectInputStream对象:

```java
ObjectInputStream in = new objectInputstream (new FileInputstream("[文件名]"));
```

然后,按照当初写入对象的顺序,用readObject方法读取对象

```java
[类型] [类名] = ([类型])in.readobject();
```

### serializable接口

protected transient int serializable

可序列化的数量  BeanContextServceProvider

### ObjectOutputStream

$File\longrightarrow FileOutputStream\longrightarrow ObjectOutputStream$

ObjectOutputStream将Java对象的原始数据类型和图形写入OutputStream。 可以使用ObjectInputStream读取（重构）对象。 可以通过使用流的文件来实现对象的持久存储。 如果流是网络套接字流，则可以在另一个主机上或另一个进程中重构对象。

只有支持java.io.Serializable接口的对象才能写入流中。 每个可序列化对象的类被编码，包括类的类名和签名，对象的字段和数组的值以及从初始对象引用的任何其他对象的关闭。

方法writeObject用于将一个对象写入流中。 任何对象，包括字符串和数组，都是用writeObject编写的。 多个对象或原语可以写入流。 必须从对应的ObjectInputstream读取对象，其类型和写入次序相同。

原始数据类型也可以使用DataOutput中的适当方法写入流中。 字符串也可以使用writeUTF方法写入。

对象的默认序列化机制写入对象的类，类签名以及所有非瞬态和非静态字段的值。 引用其他对象（除了在瞬态或静态字段中）也会导致这些对象被写入。 使用引用共享机制对单个对象的多个引用进行编码，以便可以将对象的图形恢复为与原始文件相同的形状。

```java
File file = new File("[路径]");
FileOutputStream fileOutputStream = new FileOutputStream(file);
ObjectOutputStream objectOutputStream=new ObjectOutputStream(fileOutputStream);
```

#### 方法

| 方法                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| protected void  annotateClass(类<?> cl)                      | 子类可以实现此方法，以允许类数据存储在流中。                 |
| protected void  annotateProxyClass(类<?> cl)                 | 子类可以实现这种方法来存储流中的自定义数据以及动态代理类的描述符。 |
| void close()                                                 | 关闭流。                                                     |
| void defaultWriteObject()                                    | 将当前类的非静态和非瞬态字段写入此流。                       |
| protected void drain()                                       | 排除ObjectOutputStream中的缓冲数据。                         |
| protected boolean  enableReplaceObject(boolean enable)       | 启用流来替换流中的对象。                                     |
| void flush()                                                 | 刷新流。                                                     |
| ObjectOutputStream.PutField putFields()                      | 检索用于缓冲要写入流的持久性字段的对象。                     |
| protected Object  replaceObject(Object obj)                  | 该方法将允许ObjectOutputStream的可信子类在序列化期间将一个对象替换为另一个对象。 |
| void reset()                                                 | 复位将忽略已写入流的任何对象的状态。                         |
| void useProtocolVersion(int version)                         | 指定在编写流时使用的流协议版本。                             |
| void write(byte[] buf)                                       | 写入一个字节数组。                                           |
| void write(byte[] buf, int off,  int len)                    | 写入一个子字节数组。                                         |
| void write(int val)                                          | 写一个字节。                                                 |
| void writeBoolean(boolean val)                               | 写一个布尔值。                                               |
| void writeByte(int val)                                      | 写入一个8位字节。                                            |
| void writeBytes(String str)                                  | 写一个字符串作为字节序列。                                   |
| void writeChar(int val)                                      | 写一个16位的字符。                                           |
| void writeChars(String str)                                  | 写一个字符串作为一系列的字符。                               |
| protected void  writeClassDescriptor(ObjectStreamClass desc) | 将指定的类描述符写入ObjectOutputStream。                     |
| void writeDouble(double val)                                 | 写一个64位的双倍。                                           |
| void writeFields()                                           | 将缓冲的字段写入流。                                         |
| void writeFloat(float val)                                   | 写一个32位浮点数。                                           |
| void writeInt(int val)                                       | 写一个32位int。                                              |
| void writeLong(long val)                                     | 写一个64位长                                                 |
| void writeObject(Object obj)                                 | 将指定的对象写入ObjectOutputStream。                         |
| protected void  writeObjectOverride(Object obj)              | 子类使用的方法来覆盖默认的writeObject方法。                  |
| void writeShort(int val)                                     | 写一个16位短。                                               |
| protected void writeStreamHeader()                           | 提供了writeStreamHeader方法，因此子类可以在流中附加或预先添加自己的头。 |
| void writeUnshared(Object obj)                               | 将“非共享”对象写入ObjectOutputStream。                       |
| void writeUTF(String str)                                    | 此字符串的原始数据写入格式为 modified UTF-8 。               |

### ObjectInputStream

ObjectInputStream反序列化先前使用ObjectOutputStream编写的原始数据和对象。

ObjectOutputStream和ObjectInputStream可以分别为与FileOutputStream和FileInputStream一起使用的对象图提供持久性存储的应用程序。 ObjectInputStream用于恢复先前序列化的对象。 其他用途包括使用套接字流在主机之间传递对象，或者在远程通信系统中进行封送和解组参数和参数。

ObjectInputStream确保从流中创建的图中的所有对象的类型与Java虚拟机中存在的类匹配。 根据需要使用标准机制加载类。

只能从流中读取支持java.io.Serializable或java.io.Externalizable接口的对象。

方法readObject用于从流中读取对象。 应使用Java的安全铸造来获得所需的类型。 在Java中，字符串和数组是对象，在序列化过程中被视为对象。 读取时，需要将其转换为预期类型。

可以使用DataInput上的适当方法从流中读取原始数据类型。

对象的默认反序列化机制将每个字段的内容恢复为写入时的值和类型。 声明为瞬态或静态的字段被反序列化过程忽略。 对其他对象的引用导致根据需要从流中读取这些对象。 使用参考共享机制正确恢复对象的图形。 反序列化时总是分配新对象，这样可以防止现有对象被覆盖。

读取对象类似于运行新对象的构造函数。 为对象分配内存，并初始化为零（NULL）。 对非可序列化类调用无索引构造函数，然后从最接近java.lang.object的可序列化类开始，从串中还原可序列化类的字段，并使用对象的最特定类完成。

$File\longrightarrow FileInputStream\longrightarrow ObjectInputStream$

```java
File file = new File("[路径]");
FileInputStream fileInputStream = new FileInputStream(file);
ObjectInputStream objectInputStream=new ObjectInputStream(fileInputStream);
```

>    readObject()没有像read()独到末尾返回-1，也没有像readline()独到末尾返回null。他就是返回对象，读完了就异常。

#### 方法

| int available()                                              | 返回可以读取而不阻塞的字节数。                               |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| void close()                                                 | 关闭输入流。                                                 |
| void defaultReadObject()                                     | 从此流读取当前类的非静态和非瞬态字段。                       |
| protected boolean  enableResolveObject(boolean enable)       | 启用流以允许从流中读取的对象被替换。                         |
| int read()                                                   | 读取一个字节的数据。                                         |
| int read(byte[] buf, int off,  int len)                      | 读入一个字节数组。                                           |
| boolean readBoolean()                                        | 读取布尔值。                                                 |
| byte readByte()                                              | 读取一个8位字节。                                            |
| char readChar()                                              | 读一个16位字符。                                             |
| protected ObjectStreamClass  readClassDescriptor()           | 从序列化流读取类描述符。                                     |
| double readDouble()                                          | 读64位双倍。                                                 |
| ObjectInputStream.GetField readFields()                      | 从流中读取持久性字段，并通过名称获取它们。                   |
| float readFloat()                                            | 读32位浮点数。                                               |
| void readFully(byte[] buf)                                   | 读取字节，阻塞直到读取所有字节。                             |
| void readFully(byte[] buf,  int off, int len)                | 读取字节，阻塞直到读取所有字节。                             |
| int readInt()                                                | 读取一个32位int。                                            |
| String readLine()                                            | 已弃用                                                       |
| long readLong()                                              | 读64位长。                                                   |
| Object readObject()                                          | 从ObjectInputStream读取一个对象。                            |
| protected Object  readObjectOverride()                       | 此方法由ObjectOutputStream的受信任子类调用，该子类使用受保护的无参构造函数构造ObjectOutputStream。 |
| short readShort()                                            | 读取16位短。                                                 |
| protected void readStreamHeader()                            | 提供了readStreamHeader方法来允许子类读取和验证自己的流标题。 |
| Object readUnshared()                                        | 从ObjectInputStream读取一个“非共享”对象。                    |
| int readUnsignedByte()                                       | 读取一个无符号的8位字节。                                    |
| int readUnsignedShort()                                      | 读取无符号16位短。                                           |
| String readUTF()                                             | 以 modified UTF-8格式读取字符串。                            |
| void  registerValidation(ObjectInputValidation obj, int prio) | 在返回图之前注册要验证的对象。                               |
| protected 类<?>  resolveClass(ObjectStreamClass desc)        | 加载本地类等效的指定流类描述。                               |
| protected Object  resolveObject(Object obj)                  | 此方法将允许ObjectInputStream的受信任子类在反序列化期间将一个对象替换为另一个对象。 |
| protected 类<?>  resolveProxyClass(String[] interfaces)      | 返回一个代理类，它实现代理类描述符中命名的接口; 子类可以实现此方法从流中读取自定义数据以及动态代理类的描述符，从而允许它们为接口和代理类使用备用加载机制。 |
| int skipBytes(int len)                                       | 跳过字节。                                                   |

#### 从文件读取对象

```java
[Class] tmp = new [Class]();
try {

	while ((tmp = (Student) objectInputStream.readObject()) != null) {

		// TODO
	}
} catch (IOException | ClassNotFoundException ignored) {

}
```

# 多线程编程

Java编写的程序都运行在Java虚拟机(JVM)中,在JVM的内部,程序的多任务是通过线程来实现的。每当使用Java命令启动一个Java应用程序,就会启动一个JVM进程。在同一个JVM进程中,有且只有一个进程,就是它自己。在这个JVM环境中,所有程序代码的运行都是以线程来运行的。

JVM找到程序的入口点main(),然后运行main()方法,这样就产生了一个线程,这个线程称之为主线程。当main()方法结束后,主线程运行完成。JVM进程也随即退出。对于多个线程来说,多个线程共享JVM进程的内在块,当新的线程产生的时候,操作系统不分配新的内存,而是让新线程共享原有的进程块的内存。JVM负责对进程、线程进行管理,轮流(没有固定的顺序)分配每个进程很短的一段CPU时间(不一定是均分),然后在每个进程内部,程序代码自己处理该进程内部线程的时间分配,多个线程之间相互地切换去执行,这个切换时间也是非常短的。

进程和线程最大的区别在于,进程是由操作系统来控制的,而线程是由进程来控制的。

## 进程

*    一个进程就是一个执行中的程序，而每一个进程都有自己独立的一块内存空间、一组系统资源。在进程的概念中，每一个进程的内部数据和状态都是完全独立的。

## 线程创建

*    线程与进程相似，是一段完成某个特定功能的代码，是程序中单个顺序控制的流程，但与进程不同的是，同类的多个线程是共享一块内存空间和一组系统资源。所以系统在各个线程之间切换时，开销要比进程小的多，正因如此，线程被称为轻量级进程。一个进程中可以包含多个线程。
*    线程(thread)是“进程”中某个单一顺序的控制流,也被称为轻量进程(lightweightprocesses),它是一个比进程更小的执行单位,是程序执行流的最小单元。一个标准的线程由线程ID、当前指令指针(PC) 、寄存器集合和堆栈组成。另外,线程是进程中的一个实体,是被系统独立调度和分派的基本单位,线程自己不拥有系统资源,只拥有一点在运行中必不可少的资源,但它可与同属一个进程的其他线程共享进程所拥有的全部资源。一个线程可以创建和撤销另一个线程,同一进程中的多个线程之间可以并发执行。由于线程之间的相互制约,致使线程在运行中呈现出间断性。

### 主线程

*    Java程序至少会有一个线程，这就是主线程，程序启动后是由JVM创建主线程，程序结束时由JVM停止主线程。主线程它负责管理子线程，即子线程的启动、挂起、停止等等操作。

### 子线程

Java中创建一个子线程涉及到：java.lang.Thread类和java.lang.Runnable接口。

Thread是线程类，创建一个Thread对象就会产生一个新的线程。而线程执行的程序代码是在实现Runnable接口对象的run()方法中编写的，实现Runnable接口对象是线程执行对象。

Thread.currentThread()可以获得当前线程对象。

getName()是Thread类的实例方法，可以获得线程的名。

Thread.sleep(sleepTime)是休眠当前线程
*    static void sleep(long millis)：在指定的毫秒数内让当前正在执行的线程休眠。
*    static void sleep(long millis, int nanos) 在指定的毫秒数加指定的纳秒数内让当前正在执行的线程休眠。

线程创建完成还需要调用start()方法才能执行。start()方法一旦调用线程进入可以执行状态，可以执行状态下的线程等待CPU调度执行，CPU调用后线程进行执行状态，运行run()方法。

但是实际上一台PC通常就只有一颗CPU，在某个时刻只能是一个线程在运行，而Java语言在设计时就充分考虑到线程的并发调度执行。对于程序员来说，在编程时要注意给每个线程执行的时间和机会，主要是通过让线程休眠的办法（调用sleep()方法）来让当前线程暂停执行，然后由其他线程来争夺执行的机会。

### Thread类

线程是程序中执行的线程。 Java虚拟机允许应用程序同时执行多个执行线程。

每个线程都有优先权。 具有较高优先级的线程优先于优先级较低的线程执行。 每个线程可能也可能不会被标记为守护程序。 当在某个线程中运行的代码创建一个新的`Thread`对象时，新线程的优先级最初设置为等于创建线程的优先级，并且当且仅当创建线程是守护进程时才是守护线程。

#### 方法

| 方法                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| boolean isAlive()                                            | 测试这个线程是否活着。                                       |
| boolean isDaemon()                                           | 测试这个线程是否是守护线程。                                 |
| boolean isInterrupted()                                      | 测试这个线程是否被中断。                                     |
| ClassLoader getContextClassLoader()                          | 返回此Thread的上下文ClassLoader。                            |
| int getPriority()                                            | 返回此线程的优先级。                                         |
| long getId()                                                 | 返回此线程的标识符。                                         |
| protected Object clone()                                     | 将CloneNotSupportedException作为线程抛出无法有意义地克隆。   |
| StackTraceElement[] getStackTrace()                          | 返回表示此线程的堆栈转储的堆栈跟踪元素数组。                 |
| static boolean holdsLock(Object obj)                         | 返回 true当且仅当当前线程在指定的对象上保持监视器锁。        |
| static boolean interrupted()                                 | 测试当前线程是否中断。                                       |
| static int activeCount()                                     | 返回当前线程的thread group及其子组中活动线程数的估计。       |
| static int  enumerate(Thread[] tarray)                       | 将当前线程的线程组及其子组中的每个活动线程复制到指定的数组中。 |
| static void dumpStack()                                      | 将当前线程的堆栈跟踪打印到标准错误流。                       |
| static void  setDefaultUncaughtExceptionHandler(Thread.UncaughtExceptionHandler eh) | 设置当线程由于未捕获的异常突然终止而调用的默认处理程序，并且没有为该线程定义其他处理程序。 |
| static void sleep(long millis)                               | 使当前正在执行的线程以指定的毫秒数暂停（暂时停止执行），具体取决于系统定时器和调度程序的精度和准确性。 |
| static void sleep(long millis,  int nanos)                   | 导致正在执行的线程以指定的毫秒数加上指定的纳秒数来暂停（临时停止执行），这取决于系统定时器和调度器的精度和准确性。 |
| static void yield()                                          | 对调度程序的一个暗示，即当前线程愿意产生当前使用的处理器。   |
| static Map<Thread,StackTraceElement[]>  getAllStackTraces()  | 返回所有活动线程的堆栈跟踪图。                               |
| static Thread currentThread()                                | 返回对当前正在执行的线程对象的引用。                         |
| static Thread.UncaughtExceptionHandler  getDefaultUncaughtExceptionHandler() | 返回当线程由于未捕获异常突然终止而调用的默认处理程序。       |
| String getName()                                             | 返回此线程的名称。                                           |
| String toString()                                            | 返回此线程的字符串表示，包括线程的名称，优先级和线程组。     |
| Thread.State getState()                                      | 返回此线程的状态。                                           |
| Thread.UncaughtExceptionHandler  getUncaughtExceptionHandler() | 返回由于未捕获的异常，此线程突然终止时调用的处理程序。       |
| ThreadGroup getThreadGroup()                                 | 返回此线程所属的线程组。                                     |
| void checkAccess()                                           | 确定当前正在运行的线程是否有权限修改此线程。                 |
| void interrupt()                                             | 中断这个线程。                                               |
| void join()                                                  | 等待这个线程死亡。                                           |
| void join(long millis)                                       | 等待这个线程死亡最多 millis毫秒。                            |
| void join(long millis,  int nanos)                           | 等待最多 millis毫秒加上 nanos纳秒这个线程死亡。              |
| void run()                                                   | 如果这个线程使用单独的Runnable运行对象构造，则调用该Runnable对象的run方法; 否则，此方法不执行任何操作并返回。 |
| void  setContextClassLoader(ClassLoader cl)                  | 设置此线程的上下文ClassLoader。                              |
| void setDaemon(boolean on)                                   | 将此线程标记为 daemon线程或用户线程。                        |
| void setName(String name)                                    | 将此线程的名称更改为等于参数 name 。                         |
| void setPriority(int newPriority)                            | 更改此线程的优先级。                                         |
| void  setUncaughtExceptionHandler(Thread.UncaughtExceptionHandler eh) | 设置当该线程由于未捕获的异常而突然终止时调用的处理程序。     |
| void start()                                                 | 导致此线程开始执行; Java虚拟机调用此线程的run方法。          |

### 实现Runnable接口

使用Thread类如下两个构造方法

*    Thread(Runnable target, String name)：target是线程执行对象，实现Runnable接口。name为线程指定一个名字。
*    Thread(Runnable target)：target是线程执行对象，实现Runnable接口。线程名字是由JVM分配的。

在实际编程中,实现Runnable的子类中,通常都会定义一个Thread类的对象,然后利用Thread的构造方法:Thread (Runnable target)或Thread (Runnable target, string name)将本类作为参数传递给Thread对象,这样就可以指定要运行的run)方法。

同时,还可以使用Thread类中定义好的其他辅助方法。除此之外,为了启动这个线程,还需要定义一个start()方法,以启动内部的Thread对象。

### 使用匿名内部类和Lambda表达式实现线程体

如果线程体使用的地方不是很多，可以不用单独定义一个类。可以使用匿名内部类或Lambda表达式直接实现Runnable接口。

Runnable中只有一个方法是函数式接口，可以使用Lambda表达式。

>    在实际的Java程序开发中,我们更倾向于通过实现Runnable接口的方式实现多线程,因为实现Runnable接口相比继承Thread类而言,既可以避免单继承的局限,也可以避免类层次的加深,同时更适合于资源的共享。

## 线程的状态

### 新建状态

新建状态（New）是通过new等方式创建线程对象，它仅仅是一个空的线程对象。

### 就绪状态

当主线程调用新建线程的start()方法后，它就进入就绪状态（Runnable）。此时的线程尚未真正开始执行run()方法，它必须等待CPU的调度。一旦获得CPU资源,就可以脱离创建它的主线程独立运行了。另外,原来处于阻塞状态的线程结束阻塞状态后,也将进入就绪状态。

### 运行状态

CPU的调度就绪状态的线程，线程进入运行状态（Running），处于运行状态的线程独占CPU，执行run()方法。

当一个就绪状态的线程获得CPU时,就进入了运行状态。每个Thread类及其子类对象都有一个run()方法,一旦线程开始运行,就会自动运行该方法。在run()方法中定义了线程所有的操作。

### 阻塞状态

因为某种原因运行状态的线程会进入不可运行状态，即阻塞状态（Blocked），处于阻塞状态的线程JVM系统不能执行该线程，即使CPU空闲，也不能执行该线程。

#### 进入阻塞状态方法

*    当前线程调用sleep()方法，进入休眠状态。
*    被其他线程调用了join()方法，等待其他线程结束。
*    发出I/O请求，等待I/O操作完成期间。
*    当前线程调用wait()方法。

*    处于阻塞状态可以重新回到就绪状态

### 死亡状态

*    线程退出run()方法后，就会进入死亡状态（Dead），线程进入死亡状态有可以是正常实现完成run()方法进入，也可能是由于发生异常而进入的。

## 线程管理

### 线程优先级

*    默认情况下,所有的线程都按照正常的优先级来运行及分配CPU资源。JVM允许程序员自行设置线程优先级。理论上,优先级高的线程比优先级低的线程获得更多的CPU时间。
*    实际上,线程获得的CPU时间通常由包括优先级在内的多个因素决定,一个优先级高的线程自然比优先级低的线程优先。举例来说,当低优先级线程正在运行,而一个高优先级的线程被恢复(例如,从沉睡中或等待1/0中) ,它将抢占低优先级线程所使用的CPU,理论上,等优先级线程有同等的权力使用CPU,但由于Java是被设计成能在很多环境下工作的,一些环境下实现多任务处理从本质上与其他环境不同。为安全起见,等优先级线程偶尔也受控制。这保证了所有线程,在无优先级的操作系统下都有机会运行。实际上,在无优先级的环境下,多数线程仍然有机会运行,因为很多线程不可避免地会遭遇阻塞,例如,等待输入输出。遇到这种情形,阻塞的线程被挂起,其他线程运行。
*    线程的调度程序根据线程决定每次线程应当何时运行，Java提供了10种优先级，分别用1~10整数表示，最高优先级是10用常量MAX_PRIORITY表示；最低优先级是1用常量MIN_PRIORITY；默认优先级是5用常量NORM_PRIORITY表示。
*    Thread类提供了setPriority(int newPriority)方法可以设置线程优先级，通过getPriority()方法获得线程优先级。

### 等待线程结束

*    当前线程调用t1线程的join()方法，则阻塞当前线程，等待t1线程结束，如果t1线程结束或等待超时，则当前线程回到就绪状态。

#### join()

throws InterruptedException

*    void join()：等待该线程结束。
*    void join(long millis)：等待该线程结束的时间最长为millis毫秒。如果超时为0意味着要一直等下去。
*    void join(long millis, int nanos)：等待该线程结束的时间最长为millis毫秒加nanos纳秒。

## 线程让步

*    静态方法yield()，调用yield()方法能够使当前线程给其他线程让步。它类似于sleep()方法，能够使运行状态的线程放弃CPU使用权，暂停片刻，然后重新回到就绪状态。
*    与sleep()方法不同的是，sleep()方法是线程进行休眠，能够给其他线程运行的机会，无论线程优先级高低都有机会运行。而yield()方法只给相同优先级或更高优先级线程机会。

## 线程停止

*    线程体中的run()方法结束，线程进入死亡状态，线程就停止了。

## 线程安全

*    在多线程环境下，访问相同的资源，有可以会引发线程不安全问题。

### 临界资源问题

*    多个线程间共享的数据称为共享资源或临界资源，由于是CPU负责线程的调度，程序员无法精确控制多线程的交替顺序。这种情况下，多线程对临界资源的访问有时会导致数据的不一致性。

### 多线程同步

*    可以通过两种方式实现线程同步，两种方式都涉及到使用synchronized关键字，一种是synchronized方法，使用synchronized关键字修饰方法，对方法进行同步；另一种是synchronized语句，使用synchronized关键字放在对象前面限制一段代码的执行。

#### synchronized方法

*    synchronized关键字修饰方法实现线程同步，方法所在的对象被锁定

synchronized的使用形式有两种,一种是保护整个方法

```java
访问类型 synchronized 返回值方法名([参数表]){...}
```

另外一种是保护某个指定的对象以及随后的代码块:

```java
synchronized (对象名) { }
```

#### synchronized语句

*    synchronized语句方式主要用于第三方类，不方便修改它的代码情况。

## 线程间通信

*    如果两个线程之间有依赖关系，线程之间必须进行通信，互相协调才能完成工作。

### 概念

*    互斥:当多个线程需要访问同一资源,而这一资源在某一时刻只允许一个线程访问,那么这些线程就是互斥的。
*    同步:多个线程需要访问同一资源,而且需要相互配合才能正常工作,那么这些线程运行时就是一种同步关系。
*    临界区:为了实现线程间的互斥和同步,需要将共享资源放入一个区域,该区域一次只允许一个线程进入,该区域被称为临界资源。线程在访问共享资源前需要进行检查,看自己能否对该资源访问。如果有权访问,还需要阻止其他线程进入该区域。该代码段就是临界区。
*    死锁:若有多个线程相互等待其他线程释放资源,且所有线程都不释放自己所占有的资源,从而导致相关线程处于永远等待的状态,这种现象称为线程的死锁。

### 方法

*    void wait()：使当前线程释放对象锁，然后当前线程处于对象等待队列中阻塞状态。
*    void wait(long timeout)：同wait()方法，等待timeout毫秒时间。
*    void wait(long timeout, int nanos)：同wait()方法，等待timeout毫秒加nanos纳秒时间。
*    void notify()：当前线程唤醒此对象等待队列中的一个线程
*    void notifyAll()：当前线程唤醒此对象等待队列中的所有线程
*    synehronized关键字则用来标志被同步使用的资源。这里的资源既可以是数据,也可以是方法,甚至是一段代码。凡是被synchronized修饰的资源,系统都会为它分配一个管程,这样就能保证在某一时间内,只有一个线程对象在享有这一资源。所以synchronized也被称为“对象锁”。而且,上面提到的3个方法,都只能使用在由synchronized控制的代码块中。

# 运行时类型识别RTTI

## RTTI的工作原理

任何一个作为程序一部分的类,都有一个Class对象。换言之,每次写一个新类时,同时也会创建一个Class对象(更恰当地说,是保存在一个完全同名的.class文件中)。在运行期,一旦程序员想生成某个类的一个对象,用于执行程序的Java虚拟机(JVM)首先就会检查该类型的Class对象是否已经载入。若尚未载入,JVM就会查找同名的.class文件,并将其载入。所以, Java程序启动时并不是完全载入的,这一点与许多传统语言都不同。一旦该类型的Class对象进入内存,就用它创建该类型的所有对象。

Class类中间提供了很多有用的方法,其中, forName()方法用来加载一个对象。使用它,可以不必用关键字new来创建对象。

```cpp
Class.forName("类名");
```

new 是静态加载，forName 是动态加载

## Java类识别

### 获取类信息

```cpp
public final Class<? extends Object> getClass()
```

所以所有类都可以直接使用它,但不能覆盖它。

$类\longrightarrow Class$

获得返回值之后,可以利用Class类的各种方法对对象进行处理

### 类标记

如果T是任意的Java类型,那么, T.class就代表匹配的类对象。

```java
类.class
```

### 关键字instanceof

Java提供了一个关键字instanceof,用于帮助程序员判断一个对象真正所属的类。它是一个二元运算符,一般形式如下

```java
objectName instanceof className
```

其中,左侧的操作数是一个对象名,右侧的操作数是类名,计算结果为true或false

# 网络编程

*    Java SE提供java.net包，其中包含了网络编程所需要的最基础一些类和接口。这些类和接口面向两个不同的层次：基于Socket的低层次网络编程和基于URL的高层次网络编程。
*    所谓高低层次就是通信协议的高低层次，Socket采用TCP、UDP等协议，这些协议属于低层次的通信协议。
*    URL采用HTTP和HTTPS这些属于高层次的通信协议。低层次网络编程，因为它面向底层，比较复杂，但是“低层次网络编程”并不等于它功能不强大。恰恰相反，正因为层次低，Socket编程与基于URL的高层次网络编程比较，能够提供更强大的功能和更灵活的控制，但是要更复杂一些。

## TCP/IP协议

*    TCP/IP协议是由IP和TCP两个协议构成的， IP（Internet Protocol）协议是一种低级的路由协议，它将数据拆分成许多小的数据包中，并通过网络将它们发送到某一特定地址，但无法保证都所有包都抵达目的地，也不能保证包的顺序。
*    由于IP协议传输数据的不安全性，网络通信时还需要TCP协议，传输控制协议（Transmission Control Protocol，TCP）是一种高层次的协议，面向连接的可靠数据传输协议，如果有些数据包没有收到会重发，并对数据包内容准确性检查并保证数据包顺序，所以该协议保证数据包能够安全地按照发送时顺序送达目的地。

## HTTP/HTTPS协议

### HTTP协议

*    HTTP是Hypertext Transfer Protocol的缩写，即超文本传输协议。HTTP是一个属于应用层的面向对象的协议，其简捷、快速的方式适用于分布式超文本信息的传输。它于1990年提出，经过多年的使用与发展，得到不断完善和扩展。HTTP协议支持C/S网络结构，是无连接协议，即每一次请求时建立连接，服务器处理完客户端的请求后，应答给客户端然后断开连接，不会一直占用网络资源。

#### 方法

*    HTTP/1.1协议共定义了8种请求方法：OPTIONS、HEAD、GET、POST、PUT、DELETE、 TRACE和CONNECT。在HTTP访问中，一般使用GET和HEAD方法。
     *    GET方法：是向指定的资源发出请求，发送的信息“显式”地跟在URL后面。GET方法应该只用在读取数据，例如静态图片等。GET方法有点像使用明信片给别人写信，“信内容”写在外面，接触到的人都可以看到，因此是不安全的。
     *    POST方法：是向指定资源提交数据，请求服务器进行处理，例如提交表单或者上传文件等。数据被包含在请求体中。POST方法像是把“信内容”装入信封中，接触到的人都看不到，因此是安全的。

### HTTPS协议

*    HTTPS是Hypertext Transfer Protocol Secure，即超文本传输安全协议，是超文本传输协议和SSL的组合，用以提供加密通信及对网络服务器身份的鉴定。
*    简单地说，HTTPS是HTTP的升级版，HTTPS与HTTP的区别是：HTTPS使用https://代替http://， HTTPS使用端口443，而HTTP使用端口80来与TCP/IP进行通信。SSL使用40位关键字作为RC4流加密算法，这对于商业信息的加密是合适的。HTTPS和SSL支持使用X.509数字认证，如果需要的话，用户可以确认发送者是谁。

### URL类

*    URL是Uniform Resource Locator简称，翻译过来是“一致资源定位器”，但人们都习惯URL简称。
*    格式
     *    协议名://资源名
*    “协议名”指明获取资源所使用的传输协议，如http、ftp、gopher和file等，“资源名”则应该是资源的完整地址，包括主机名、端口号、文件名或文件内部的一个引用。
*    Java 的java.net.URL类用于请求互联网上的资源，采用HTTP/HTTPS协议，请求方法是GET方法，一般是请求静态的、少量的服务器端数据。

#### 构造方法

*    URL(String spec)：根据字符串表示形式创建URL对象。
*    URL(String protocol, String host, String file)：根据指定的协议名、主机名和文件名称创建URL对象。
*    URL(String protocol, String host, int port, String file)：根据指定的协议名、主机名、端口号和文件名称创建URL对象。

#### 方法

*    InputStream openStream()：打开到此URL的连接，并返回一个输入流。
*    URLConnection openConnection()：打开到此URL的新连接，返回一个URLConnection对象。

## IP地址

*    为实现网络中不同计算机之间的通信，每台计算机都必须有一个与众不同的标识，这就是IP地址， TCP/IP使用IP地址来标识源地址和目的地址。
*    在IPv4地址模式中IP地址分为A、B、C、D和E等5类。
     *    A类地址用于大型网络，地址范围：1.0.0.1~126.155.255.254。 
     *    B类地址用于中型网络，地址范围：128.0.0.1~191.255.255.254。 
     *    C类地址用于小规模网络，192.0.0.1~223.255.255.254。
     *    D类地址用于多目的地信息的传输和作为备用。
     *    E类地址保留仅作实验和开发用。

## 端口

*    一个IP地址标识这一台计算机，每一台计算机又有很多网络通信程序在运行，提供网络服务或进行通信，这就需要不同的端口进行通信。
*    TCP/IP系统中的端口号是一个16位的数字，它的范围是0~65535。小于1024的端口号保留给预定义的服务

## TCP Socket通信

*    Socket是网络上的两个程序，通过一个双向的通信连接，实现数据的交换。

### Socket类

*    表示双向连接的客户端。

#### 构造方法

*    Socket(InetAddress address, int port) ：创建Socket对象，并指定远程主机IP地址和端口号。
*    Socket(InetAddress address, int port, InetAddress localAddr, int localPort)：创建Socket对象，并指定远程主机IP地址和端口号，以及本机的IP地址（localAddr）和端口号（localPort）。
*    Socket(String host, int port)：创建Socket对象，并指定远程主机名和端口号，IP地址为null，null表示回送地址，即127.0.0.1。
*    Socket(String host, int port, InetAddress localAddr, int localPort)：创建Socket对象，并指定远程主机和端口号，以及本机的IP地址（localAddr）和端口号（localPort）。host主机名，IP地址为null，null表示回送地址，即127.0.0.1。

#### 方法

*    InputStream getInputStream()：通过此Socket返回输入流对象。 
*    OutputStream getOutputStream()：通过此Socket返回输出流对象。 
*    int getPort()：返回Socket连接到的远程端口。
*    int getLocalPort()：返回Socket绑定到的本地端口。
*    InetAddress getInetAddress()：返回Socket连接的地址。 
*    InetAddress getLocalAddress()：返回Socket绑定的本地地址。 
*    boolean isClosed()：返回Socket是否处于关闭状态。
*    boolean isConnected()：返回Socket是否处于连接状态。
*    void close()：关闭Socket。

### ServerSocket类

*    表示双向连接的服务器端。

#### 构造方法

*    ServerSocket(int port, int maxQueue)：创建绑定到特定端口的服务器Socket。
*    maxQueue设置连接的请求最大队列长度，如果队列满时，则拒绝该连接。默认值是50。
*    ServerSocket(int port)：创建绑定到特定端口的服务器Socket。最大队列长度是50。

#### 方法

*    InputStream getInputStream()：通过此Socket返回输入流对象。 
*    OutputStream getOutputStream()：通过此Socket返回输出流对象。 
*    boolean isClosed()：返回Socket是否处于关闭状态。
*    Socket accept()：侦听并接收到Socket的连接。此方法在建立连接之前一直阻塞。
*    void close()：关闭Socket。

## UDP Socket通信

### DatagramSocket类

*    DatagramSocket用于在程序之间建立传送数据报的通信连接。

#### 构造方法

*    DatagramSocket()：创建数据报DatagramSocket对象，并将其绑定到本地主机上任何可用的端口。
*    DatagramSocket(int port)：创建数据报DatagramSocket对象，并将其绑定到本地主机上的指定端口。
*    DatagramSocket(int port, InetAddress laddr)：创建数据报DatagramSocket对象，并将其绑定到指定的本地地址。

#### 方法

*    void send(DatagramPacket p)：从发送数据报包。
*    void receive(DatagramPacket p)：接收数据报包。
*    int getPort()：返回DatagramSocket连接到的远程端口。
*    int getLocalPort()：返回DatagramSocket绑定到的本地端口。 InetAddress getInetAddress()：返回DatagramSocket连接的地址。 
*    InetAddress getLocalAddress()：返回DatagramSocket绑定的本地地址。 boolean isClosed()：返回DatagramSocket是否处于关闭状态。 boolean isConnected()：返回DatagramSocket是否处于连接状态。 void close()：关闭DatagramSocket。

### DatagramPacket类

*    DatagramPacket用来表示数据报包，是数据传输的载体。DatagramPacket实现无连接数据包投递服务，每投递数据包仅根据该包中信息从一台机器路由到另一台机器。从一台机器发送到另一台机器的多个
     包可能选择不同的路由，也可能按不同的顺序到达，不保证包都能到达目的。

#### 构造方法

*    DatagramPacket(byte[] buf, int length)：构造数据报包，buf包数据，length是接收包数据的长度。
*    DatagramPacket(byte[] buf, int length, InetAddress address, int port)：构造数据报包，包发送到指定主机上的指定端口号。
*    DatagramPacket(byte[] buf, int offset, int length)：构造数据报包，offset是buf字节数组的偏移量。
*    DatagramPacket(byte[] buf, int offset, int length, InetAddress address, int port)：构造数据报包，包发送到指定主机上的指定端口号。

#### 方法

*    InetAddress getAddress()：返回发往或接收该数据报包相关的主机的IP地址。 
*    byte[] getData()：返回数据报包中的数据。
*    int getLength()：返回发送或接收到的数据（byte[]）的长度。
*    int getOffset()：返回发送或接收到的数据（byte[]）的偏移量。
*    int getPort()：返回发往或接收该数据报包相关的主机的端口号。

# 图形界面编程

## AWT

*    AWT（Abstract Window Toolkit）是抽象窗口工具包，AWT是Java 程序提供的建立图形用户界面最基础的工具集。AWT支持图形用户界面编程的功能包括：用户界面组件（控件）、事件处理模型、图形图像处理（形状和颜色）、字体、布局管理器和本地平台的剪贴板来进行剪切和粘贴等。AWT是Applet和Swing技术的基础。

## Applet

*    Applet称为Java小应用程序，Applet基础是AWT，但它主要嵌入到HTML代码中，由浏览器加载和运行，由于存在安全隐患和运行速度慢等问题，已经很少使用了。

## Swing

*    Swing是Java主要的图形用户界面技术，Swing提供跨平台的界面风格，用户可以自定义Swing的界面风格。
*    Swing提供了比AWT更完整的组件，引入了许多新的特性。Swing API是围绕着实现AWT各个部分的API构筑的。Swing是由100%纯Java实现的，Swing组件没有本地代码，不依赖操作系统的支持，这是它与AWT组件的最大区别。
*    图形用户界面主要是由窗口以及窗口中的组件构成的，编写Swing程序主要就是创建窗口和添加组件过程。

### Swing程序结构

*    构建Swing程序主要有两种方式：创建JFrame或继承JFrame。
*    图形用户界面主要是由窗口以及窗口中的组件构成的，编写Swing程序主要就是创建窗口和添加组件过程。
*    JFrame有标题、边框、菜单、大小和窗口管理按钮等窗口要素，而JWindow没有标题栏和窗口管理按钮。

#### 构建Swing程序方式

*    创建JFrame方式适合于小项目，代码量少、窗口不多、组件少的情况。继承JFrame
     方式，适合于大项目，可以针对不同界面自定义一个Frame类，属性可以在构造方法中进行设置；缺点是有很多类文件需要有效地管理。

##### 创建JFrame

*    直接实例化JFrame对象，然后设置JFrame属性，添加窗口所需要的组件。
*    默认情况下JFrame是没有大小且不可见的，因此创建JFrame对象后还需要设置大小和可见
*    设置JFrame窗口大小和可见这两条语句，应该在添加完成所有组件之后调用。否则在多个组件情况下，会导致有些组件没有显示。
*    在Swing中添加到JFrame上的所有可见组件，除菜单栏外，全部添加到内容面板上，而不要直接添加到JFrame上，这是Swing绘制系统所要求的。

```java
JFrame name = new JFrame("Framename");
Container contentPane=frame.getContentPane();
contentPane.add();
```

##### 继承JFrame方式

*    继承JFrame方式就是编写一个继承JFrame的子类，在构造方法中初始化窗口，添加窗口所需要的组件。

```java
public class name extends JFrame{
    
    public name(String title){
        
        super(title);
    }
}
```

### 事件处理模型

*    事件：是用户对界面的操作，在Java中事件被封装称为事件类java.awt.AWTEvent及其子类，例如按钮单击事件类是java.awt.event.ActionEvent。
02.	事件源：是事件发生的场所，就是各个组件。
*    事件处理者：是事件处理程序，在Java中事件处理者是实现特定接口的事件对象。

#### 事件类型和事件监听器接口

<table>
	<tr>
			<th>事件类型</th>
            <th>相应监听器接口</th>
            <th>监听器接口中的方法</th>
		</tr>
		<tr>
			<th>Action</th>
			<th>ActionListener</th>
            <th> actionPerformed(ActionEvent)</th>
		</tr>
		<tr>
			<th rowspan="5">Mouse</th>
			<th rowspan="5">MouseListener</th>
			<th>mousePressed(MouseEvent)</th>
		</tr>
    <tr><th>mouseReleased(MouseEvent)</th></tr>
    <tr><th>mouseEntered(MouseEvent)</th></tr>
    <tr><th>mouseExited(MouseEvent)</th></tr>
    <tr><th>mouseClicked(MouseEvent)</th></tr>
    <tr><th rowspan="2">Mouse Motion</th><th rowspan="2">MouseMotionListener</th><th>mouseDragged</th></tr>
    <tr><th>mouseMoved(MouseEvent)</th></tr>
    <tr><th rowspan="3">Key</th><th rowspan="3">KeyListener</th><th>keyPressed(KeyEvent)</th></tr>
    <tr><th>keyReleased(KeyEvent)</th></tr>
    <tr><th>keyTyped(KeyEvent)</th></tr>
    <tr><th rowspan="2">Focus</th><th rowspan="2">FocusListener</th><th>focusGained(FocusEvent)</th></tr>
    <tr><th>focusLost(FocusEvent)</th></tr>
    <tr><th>Adjustment</th><th>AdjustmentListener</th><th>adjustmentValueChanged(AdjustmentEvent)</th></tr>
    <tr><th rowspan="4">Componet</th><th rowspan="4">ComponentListener</th><th>componentMoved(ComponentEvent)</th></tr>
    <tr><th>componentHidden(ComponentEvent)</th></tr>
    <tr><th>componentShown(ComponentEvent)</th></tr>
    <tr><th>componentShown(ComponentEvent)</th></tr>
    <tr><th rowspan="7">Window</th><th rowspan="7">WindowListener</th><th>windowClosing(WindowEvent)</th></tr>
    <tr><th>windowOpened(WindowEvent)</th></tr>
    <tr><th>windowIconified(WindowEvent)</th></tr>
    <tr><th>windowDeiconified(WindowEvent)</th></tr>
    <tr><th>windowClosed(WindowEvent)</th></tr>
    <tr><th>windowActivated(WindowEvent)</th></tr>
    <tr><th>windowDeactivated(WindowEvent)</th></tr>
    <tr><th rowspan="2">Container</th><th rowspan="2">ContainerListener</th><th>componentAdded(ContainerEvent)</th></tr>
    <tr><th>componentRemoved(ContainerEvent)</th></tr>
    <tr><th>Text</th><th>TextListener</th><th>textValueChanged(TextEvent)</th></tr>
</table>

#### 采用内部类处理事件

```java
public class name extends JFrame{ 
    
    public name(title){
        
        super(title);
        button1.addActionListener(new ActionEventHandler());
        button2.addActionListener(new ActionListener(){
            
            // TODO
        )};
    }
    
    class  ActionEventHandler implements ActionListener{
        
        public void actionPerformed(ActionEvent e){
            
            // TODO
        }
    }
}
```

#### 采用Lambda表达式处理事件

```java
public class name extends JFrame{ 
    
    public name(title){
        
        super(title);
        button1.addActionListener((event)-{// TODO});
    }
}
```

#### 使用适配器

*    事件监听器都是接口，在Java中接口中定义的抽象方法必须全部是实现，哪怕你对某些方法并不关心，你也要给一对空的大括号表示实现。
*    在使用时通过继承事件所对应的适配器类，覆盖所需要的方法，无关方法不用实现。

```java
this.addWindowListener(new WindowAdapter(){
    
    public void windowClosing(WindowEvent e){
        // TODO
    }
})
```

*    事件适配器提供了一种简单的实现监听器的手段，可以缩短程序代码。但是，由于Java的单一继承机制，当需要多种监听器或此类已有父类时，就无法采用事件适配器了。

##### 适配器种类

*    ComponentAdapter：组件适配器。
*    ContainerAdapter：容器适配器。
*    FocusAdapter：焦点适配器。
*    KeyAdapter：键盘适配器。
*    MouseAdapter：鼠标适配器。
*    MouseMotionAdapter：鼠标运动适配器。
*    WindowAdapter：窗口适配器。

### 布局管理

*    Java为了实现图形用户界面的跨平台，并实现动态布局等效果，Java将容器内的所有组件布局交给布局管理器管理。布局管理器负责，如组件的排列顺序、大小、位置，当窗口移动或调整大小后组件如何
     变化等。

#### FlowLayout布局

*    FlowLayout布局摆放组件的规律是：从上到下、从左到右进行摆放，如果容器足够宽，第一个组件先添加到容器中第一行的最左边，后续的组件依次添加到上一个组件的右边，如果当前行已摆放不下该
     组件，则摆放到下一行的最左边。

##### 构造方法

*    FlowLayout(int align, int hgap, int vgap)：创建一个FlowLayout对象，它具有指定的对齐方式以及指定的水平和垂直间隙，hgap参数是组件之间的水平间隙，vgap参数是组件之间的垂直间隙，单位是像素。
*    FlowLayout(int align)：创建一个FlowLayout对象，指定的对齐方式，默认的水平和垂直间隙是5个单位。
*    FlowLayout()：创建一个FlowLayout对象，它是居中对齐的，默认的水平和垂直间隙是5个单位。

##### 对齐方式align

*    FlowLayout.CENTER：指示每一行组件都应该是居中的。
*    FlowLayout.LEADING：指示每一行组件都应该与容器方向的开始边对齐，例如，对于从左到右的方向，则与左边对齐。
*    FlowLayout.LEFT：指示每一行组件都应该是左对齐的。
*    FlowLayout.RIGHT：指示每一行组件都应该是右对齐的。
*    FlowLayout.TRAILING：指示每行组件都应该与容器方向的结束边对齐，例如，对于从左到右的方向，则与右边对齐。

#### BorderLayout布局

*    BorderLayout布局是窗口的默认布局管理器
*    orderLayout布局管理器把容器分成5个区域：North、South、East、West和Center

##### 构造方法

*    BorderLayout(int hgap, int vgap)：创建一个BorderLayout对象，指定水平和垂直间隙，hgap参数是组件之间的水平间隙，vgap参数是组件之间的垂直间隙，单位是像素。
*    BorderLayout()：创建一个BorderLayout对象，组件之间没有间隙。

##### 对齐方式align

*    BorderLayout.CENTER：中间区域的布局约束（容器中央）。 
*    BorderLayout.EAST：东区域的布局约束（容器右边）。
*    BorderLayout.NORTH：北区域的布局约束（容器顶部）。 
*    BorderLayout.SOUTH：南区域的布局约束（容器底部）。
*    BorderLayout.WEST：西区域的布局约束（容器左边）。
*    在5个区域中不一定都放置了组件，如果某个区域缺少组件，界面布局会有比较大的影响

#### GridLayout布局

*    GridLayout布局以网格形式对组件进行摆放，容器被分成大小相等的矩形，一个矩形中放置一个组件。

##### 构造方法

*    GridLayout()：创建具有默认值的GridLayout对象，即每个组件占据一行一列。

*    GridLayout(int rows, int cols)：创建具有指定行数和列数的GridLayout对象。

*    GridLayout(int rows, int cols, int hgap, int vgap)：创建具有指定行数和列数的

     GridLayout对象，并指定水平和垂直间隙。

#### 不使用布局管理器

*    如果要开发的图形用户界面应用不考虑跨平台，不考虑动态布局，窗口大小不变的，那么布局管理器就失去使用的意义。容器也可以不设置布局管理器，那么此时的布局是由开发人员自己管理的。

##### 方法

*    void setLocation(int x, int y)：方法是设置组件的位置。
*    void setSize(int width, int height)：方法是设置组件的大小。
*    void setBounds(int x, int y, int width, int height)：方法是设置组件的大小和位置。

### JLabel

*    Swing中标签类是JLabel，它不仅可以显示文本还可以显示图标

#### 构造方法

*    JLabel()：创建一个无图标无标题标签对象。
*    JLabel(Icon image)：创建一个具有图标的标签对象。
*    JLabel(Icon image, int horizontalAlignment)：通过指定图标和水平对齐方式创建标签对象。 JLabel(String text)：创建一个标签对象，并指定显示的文本。
*    JLabel(String text, Icon icon, int horizontalAlignment)：通过指定显示的文本、图标和水平对齐方式创建标签对象。
*    JLabel(String text, int horizontalAlignment)：通过指定显示的文本和水平对齐方式创建标签对象。

### JButton

*    Swing中的按钮类是JButton，JButton不仅可以显示文本还可以显示图标。

#### 构造方法

*    JButton()：创建不带文本或图标的按钮对象。
*    JButton(Icon icon)：创建一个带图标的按钮对象。
*    JButton(String text)：创建一个带文本的按钮对象。
*    JButton(String text, Icon icon)：创建一个带初始文本和图标的按钮对象。

### JTextField

#### 构造方法

*    JTextField()：创建一个空的文本框对象。
*    JTextField(int columns)：指定列数，创建一个空的文本框对象，列数是文本框显示的宽度，列数主要用于FlowLayout布局。
*    JTextField(String text)：创建文本框对象，并指定初始化文本。
*    JTextField(String text, int columns)：创建文本框对象，并指定初始化文本和列数。

### JTextArea

#### 构造方法

*    JTextArea()：创建一个空的文本区对象。
*    JTextArea(int rows, int columns)：创建文本区对象，并指定行数和列数。
*    JTextArea(String text)：创建文本区对象，并指定初始化文本。
*    JTextArea(String text, int rows, int columns)：创建文本区对象，并指定初始化文本、行数和列数。

### JCheckBox/JCheckBox

*    多选组件是复选框（JCheckBox），复选框（JCheckBox）有时也单独使用，能提供两种状态的开和关。

#### JCheckBox

*    单选组件是单选按钮（JRadioButton），同一组的多个单选按钮应该具有互斥特性，这也是为什么单选按钮也叫做收音机按钮（RadioButton），就是当一个按钮按下时，其他按钮一定抬起。
*    同一组多个单选按钮应该放到同一个ButtonGroup对象，ButtonGroup对象不属于容器，它会创建一个互斥作用范围。

```cpp
ButtonGroup buttonGroup = new ButtonGroup();
buttonGrop.add(r);
```

##### 构造方法

*    JCheckBox()：创建一个没有文本、没有图标并且最初未被选定的复选框对象。
*    JCheckBox(Icon icon)：创建有一个图标、最初未被选定的复选框对象。
*    JCheckBox(Icon icon, boolean selected)：创建一个带图标的复选框对象，并指定其最初是否处于选定状态。
*    JCheckBox(String text)：创建一个带文本的、最初未被选定的复选框对象。
*    JCheckBox(String text, boolean selected)：创建一个带文本的复选框对象，并指定其最初是否处于选定状态。
*    JCheckBox(String text, Icon icon)：创建带有指定文本和图标的、最初未被选定的复选框对象。
*    JCheckBox(String text, Icon icon, boolean selected)：创建一个带文本和图标的复选框对象，并指定其最初是否处于选定状态。

### JComboBox

#### 构造方法

*    JComboBox()：创建一个下拉列表对象。
*    JComboBox(Object [] items)：创建一个下拉列表对象，items设置下拉列表中选项。下拉列表中选项内容可以是任意类，而不再局限于String。

### JList

*    Swing中提供了列表（JList）组件，可以单选或多选。

#### 构造方法

*    JList()：创建一个列表对象。
*    JList(Object [] listData)：创建一个列表对象，listData设置列表中选项。列表中选项内容可以是任意类，而不再局限于String。

### JSplitPane

*    Swing中提供了一种分隔面板（JSplitPane）组件，可以将屏幕分成左右或上下两部分。

#### 构造方法

*    JSplitPane(int newOrientation)：创建一个分隔面板，参数newOrientation指定布局方向，newOrientation取值是JSplitPane.HORIZONTAL_SPLIT水平或JSplitPane.VERTICAL_SPLIT垂直。
*    JSplitPane(int newOrientation, Component newLeftComponent, Component newRightComponent)：创建一个分隔面板，参数newOrientation指定布局方向，newLeftComponent左侧面板组件， newRightComponent右侧面板组件。

### JTable

*    Swing提供了表格组件JTable类，但是表格组件比较复杂，它的表现形式与数据分离的。

#### 构造方法

*    JTable(TableModel dm) ：通过模型创建表格，dm是模型对象，其中包含了表格要显示的数据。
*    JTable(Object[][] rowData, Object[] columnNames)：通过二维数组和指定列名，创建一个表格对象，rowData是表格中的数据，columnNames是列名。
*    JTable(int numRows, int numColumns)：指定行和列数创建一个空的表格对象。

### 生成Swing窗口

* 调用类中的main方法

```java
public static void main(String[] args) {    
    new MainGUI().main(null);
}
```

## JavaFX

*    JavaFX是开发丰富互联网应用程序（Rich Internet Application，缩写RIA）的图形用户界面技术，JavaFX期望能够在桌面应用的开发领域与Adobe公司的AIR、微软公司的Silverlight相竞争。
*    传统的互联网应用程序基于Web的，客户端是浏览器。而丰富互联网应用程序试图打造自己的客户端，替代浏览器。

# 注解

*    Java 5之后可以在源代码中嵌入一些补充信息，这种补充信息称为注解（Annotation），例如在方法覆盖中使用过的@Override注解，注解都是@符号开头的
*    注解并不能改变程序运行的结果，不会影响程序运行的性能。有些注解可以在编译时给用户提示或警告，有的注解可以在运行时读写字节码文件信息。



## 基本注解

### @Override

*    @Override只能用于方法，子类覆盖父类方法（或者实现接口的方法）时可以@Override注解。编译器会检查被@Override注解的方法，确保该方法父类中存在的方法，否则会有编译错误。
*    当然如果该方法前面不加@Override注解，即便是方法写错误了，也不会有编译错误，但是Object父类的toString()方法并没有被覆盖。这会引起程序出现Bug（缺陷）。

### @Deprecated

*    @Deprecated用来指示API已经过时了，@Deprecated可以用来注解类、接口、成员方法和成员变量。
*    在Eclipse中这些被注解的API都画上删除线。

### @SuppressWarnings

*    @SuppressWarnings注解用来抑制编译器警告，如果你确认程序中的警告没有问题，可以不用理会。但是就是不想看到这些警告，可以使用@SuppressWarnings注解消除这些警告。

### @SafeVarargs

*    抑制编译器警告将非泛型变量赋值给泛型变量

### @FunctionalInterface

*    @FunctionalInterface注解是Java 8增加的，用于接口的注解，声明接口是函数式接口。

## 元注解

### @Documented

*    如果在一个自定义注解中引用@Documented注解，那么该注解可以修饰代码元素（类、接口、成员变量和成员方法等），javadoc等工具可以提取这些注解信息。

### @Target

*    @Target注解用来指定一个新注解的适用目标。@Target注解有一个成员（value）用来设置适用目标，value是java.lang.annotation.ElementType枚举类型的数组，ElementType描述Java程序元素类型，它有10个枚举常量。

#### ElementType枚举类型中的枚举常量

<table>
    <tr><th>枚举常量</th><th>说明</th></tr>
    <tr><th>ANNOTATION_TYPE</th><th>其他注解类型声明</th></tr>
    <tr><th>CONSTRUCTOR</th><th>构造方法声明</th></tr>
    <tr><th>FIELD</th><th>成员变量或常量声明</th></tr>
    <tr><th>LOCAL_VATIABLE</th><th>局部变量声明</th></tr>
    <tr><th>METHOD</th><th>方法声明</th></tr>
    <tr><th>PACKAGE</th><th>包声明</th></tr>
    <tr><th>PARAMETER</th><th>参数声明</th></tr>
    <tr><th>TYPE</th><th>类、接口声明</th></tr>
    <tr><th>TYPE_PARAMETER</th><th>用于泛型中类型参数声明</th></tr>
    <tr><th>TYPE_USE</th><th>用于任何类型的声明</th></tr>
</table>

### @Retention

*    @Retention注解用来指定一个新注解的有效范围，@Retention注解有一个成员（value）用来设置保留策略，value是java.lang.annotation.RetentionPolicy枚举类型，RetentionPolicy描述注解保留策略，它有3个枚举常量。

#### 枚举常量

<table>
    <tr><th>枚举常量</th><th>说明</th></tr>
    <tr><th>SOURCE</th><th>只适用于java源代码文件中，此范围最小</th></tr>
    <tr><th>CLASS</th><th>编译器把注解信息记录在字节码文件中，此范围居中</th></tr>
    <tr><th>RUNTIME</th><th>编译器把注解信息记录在字节码文件中，并在运行时可以读取这些信息，此范围最大</th></tr>
</table>

#### @Inherited

*    @Inherited注解用来指定一个新注解可以被继承。假定一个类A被该新注解修饰，那么这个A类的子类会继承该新注解。

#### @Repeatable

*    @Repeatable注解是Java 8新增加的，它允许在相同的程序元素中重复注释，可重复的注释必须使用@Repeatable进行注释。

#### @Native

*    @Native注解一个成员变量，指示这个变量可以被本地代码引用。常常被代码生成工具使用。

## 自定义注解

*    如果前面的Java SE提供的11内置注解不能满足你的需求，可以自定义注解，注解本质是一种接口，它是java.lang.annotation.Annotation接口的子接口，是引用数据类型。

### 声明注解

*    声明自定义注解可以使用@interface关键字实现

```java
// Marker.java文件
public @interface Marker{
    // TODO
}
```

*    @interface声明一个注解类型，它前面的访问限定修饰符与类一样有两种：公有访问权限和默认访问权限。

# 数据库

*    数据必须以某种方式来存储才可以有用，数据库实际上是一组相关数据的集合。

## 数据持久技术

*    把数据保存到数据库中只是一种数据持久化方式。凡是将数据保存到存储介质中，需要的时候能够找到它们，并能够对数据进行修改，这些就属于数据持久化。

### 技术

#### 文本文件

*    通过Java I/O流技术将数据保存到文本文件中，然后进行读写操作，这些文件一般是结构化的文档，如XML、JSON和CSV等文件。结构化文档就是文件内部采取某种方式将数据组织起来。

#### 对象序列化

*    序列化用于将某个对象以及它的状态写到文件中，它保证了被写入的对象之间的关系，当需要这个对象时，可以完整地从文件重新构造出来，并保持原来的状态。在Java中实现
     java.io.Serilizable接口的对象才能被序列化和反序列化。Java还提供了两个流：ObjectInputStream和ObjectOutputStream。但序列化不支持事务处理、查询或者向不同的用户共享数据。序列化只适用于最简单的应用，或者在某些无法有效地支持数据库的嵌入式系统中。

#### 数据库

*    将数据保存数据库中是不错的选择，数据库的后面是一个数据库管理系统，它支持事务处理、并发 问、高级查询和SQL语言。Java对象保存到数据库中主要的技术有：JDBC1、EJB2和ORM框架等。

https://dev.mysql.com/downloads/

# 参考

*    java从小白到大牛 关东升
*    java实战宝典


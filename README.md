# kotlin-note
写kotlin有一段时间了，整理下常用的知识点，方便复习。

**1、基本数据类型**</br>
 Kotlin中使用的基本数据类型包括：数字、字符、布尔值、数组与字符串。

**2、类的继承**</br>
在Kotlin中，所有类在默认情况下都是无法被继承的，即所有类在默认情况下都是final的。想要开放继承，需要添加关键字open，只有被open修饰的类才能被继承，否则编译器会报错。

**3、类方法重写**</br>
在kotlin中，类中的方法默认是不能被重写的，需要在方法前面加上open关键字后才可以重写；子类要重写父类中open修饰的方法，需在子类的方法前面加上override关键字。

**4、类属性重写**</br>
类属性和类方法差不多，类属性前加open关键字表示方法可以被重写，子类想要重写父类中open修饰的属性，子类属性前同样需要加上override关键字。</br>
* val属性可以被val属性override
* val属性可以被var属性override
* var属性只可以被var属性override
* 本质上val相当于get方法，var相当于set与get方法

**5、内部类**</br>
- kotlin默认的内部类是静态内部类，不能持有外部类的状态（属性、方法等）</br>
- 给内部类加上inner关键词之后，就会变成非静态内部类，可以访问外部类的属性和方法</br>
- 非静态内部类想访问外部类的属性，可以使用 this@外部类名.外部类属性名 的形式访问</br>

**6、延迟初始化**</br>
- lateinit</br>
一般地，属性声明为非空类型的必须在声明时进行初始化，否则编译会报错，但想要延迟初始化的时机，可以使用lateinit关键字进行修饰，在使用的时候才进行实例化。</br>
但是lateinit只能修饰非kotlin原生类型（数字、字符以及布尔值），因为kotlin会使用null对每一个用lateinit修饰的属性做初始化，而原生类型是没有null类型，所以无法使用lateinit进行修饰。</br>
`lateinit var lazyValue: String`
- by lazy</br>
lazy()是接受一个lambda表达式并返回一个`Lazy<T>`实例的函数，lazy应用于单例模式(if-null-then-init-else-return)，当且仅当变量被第一次调用的时候，委托方法才会执行。</br>
`val lazyValue: String by lazy { println("HaHaHa!") "Hello" }`</br>
即第一次调用会执行lambda表达式并记录结果返回，输出HaHaHa和Hello；而第二次调用只会返回记录的结果数据，输出Hello。

**PS：lateinit 只用于变量var，而lazy只用于常量val**

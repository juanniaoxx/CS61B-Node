
----
### 1. Reading  --理解这个Dog类可以试试使用String类来代替【毕竟中文书理解起来更好一些】
> All code in Java must be part of a class (or something similar to a class, which we'll learn about later)
>Dog 类
```java
public class Dog {
	public int weightInpounds;

	public void makeNoise() {
		if (weightInpounds < 10){
			System.out.println("yipyipyip");
		}else if (weightInpounds < 30) {
			System.out.println("bark.bark");
		}else{
			System.out.println("woof!");
		}
	}
}

```
> Dog 是**non-static or instance methods**
> 使用Dog类

```python
public class DogLauncher {
	public static void main(String[] args){
		Dog d;
		d = new Dog();
		d.weightInpounds = 20;
		d.makeNoise();
	}
}
```

>回想一下C++ 
>对象是类的实例--[String类]
>使用`new`关键字，实例化一个`Dog` - variable 
>arrary also instantiated in java using the new keyword.

```java
public class ArrarDemo{
	public static void main(String[] args){
	int[] someArray = new int[5];
	someArray[0] = 3;
	someArray[1] = 4;
	}
}
```

<font color = "red" size = "5">Constructors in Java</font>

```
	Dog d = new Dog(20);
```
```java
	in Dog class
	public Dog(int w){
		weightInPounds = w; // Constructors in Java
	}
```
> 可以省去一些赋值和说明


<font color = "red" size = "5">Class Mehods vs. Instance</font>
>a.k.a 又名,别名
-   Class methods, a.k.a. static methods.
-   Instance methods, a.k.a. non-static methods.

> Instance methods are actions that can be taken only by a specific instance of a class. Static methods are actions that are taken by the class itself.

>人话：如果是一个静态的方法，那么他通过类本身调用，【而不可以被类的实例调用】<font color = 'pink' size = 6>虽然在规范中，应该是不允许实例引用`static`成员函数，但在实际操作中，因为各种原因总是存在实例引用（也就是会被转换类名调用）</font>。而实例方法，就是常见的成员函数，可以被这个类实例化的任何实例所调用。

>举一个简单的例子

```java
//在Math类里面有sqrt（）方法，是一个static方法
那么我们可以这样调用它
x = Math.sqrt(100);
如果它不是static method,我们就只能
Math m = new Math();
x = m.sqrt(100);
```

<font color = "pink" size = 5>static variables </font>
> 和static method 一样呢，只能被类名调用
> But 在Java中其实可以使用类的实例调用，但强烈反对！非常不好的Sytle


```java
public static void main(String[]) args)
```
`void` : no return type.
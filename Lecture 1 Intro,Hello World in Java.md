> 参考书籍 A Java Reference: Assorted Java Reference Material
### 1. reading
> 经典Hello Wrold

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello world!");
    }
}
```

> 1. 所有的程序必须在< public class XXXX >中并且XXXX必须是该文件的名字  --也就是所谓的 `类声明`
> 2. 并且每一个文件必须包含一个`方法`main
> 3. 特别需要注意 在Java中`方法[method]` 和 `函数[fucntion]` 通常具有相同的意思(c++中的成员函数)
> 4. 每一句语句后面需要包含一个`;[semi-colons]`
> 
```cmd
javac HelloWorld.java ---编译Java文件--生成.class文件
java HelloWorld,java --运行编译好的java文件
```

 
> 变量与循环(variables and Loops )

```java
public class HelloNumber{
	public static void main(String []  args){
		int x = 8;
		while (x < 10){
			System.out.println(x + " " );
			x = x + 1;
		}
	}
}
```

> 1. 变量必须在使用前被声明（区别于Python）
> 2. while循环和C/C++是一致的
> 3. System.out.println or System.out.print  ,是否换行"\\n"

> 静态类型语言

```java
public class HelloNumber{
	public static void main(String []  args){
		int x = 8;
		while (x < 10){
			System.out.println(x + " " );
			x = x + 1;
		}
		x = "hours";
	}
}
```

> 如果是python上述内容不会有任何问题，因为python is not static ，而Java是。所以在`编译`过程中上述，内容就会报错！(error :  incompatible types:String cannot be converted to int）

> 强类型语言 （不接受不能被强制类型转换而产生的运算）

```java
String h  = 5 + "horse" ; (get)
int h = 6=5 + "horse" ; (error) //stirng 类型是不可以被强制类型转换为int ，而int 是可以被转换为String的
```

```java
/*System.out.println(5 + "10") what is ?*/
System.out.println(5 + "10");//15 or 510?
```

-----
###  Mission
- [x] Reading + slides
- [x] video
- [x] guide
- [x] dicussion --- Introduction to java
- [x] lab2


----
### Reading
>chapter 2.1Lists
>**While Java does have a built-in List type, we're going to eschew using it for now. In this chapter, we'll build our own list from scratch, along the way learning some key features of Java.**


>KeyWord `new` 可以认为其返回值是返回一个`address` !

>单词
>1. simulation [模拟]
>2. eschew[回避]
>3. ponder [v.思考]
>4. profound [adj.深刻的，深厚的]  [n.海洋]
>5. hint [n.v 暗示]
>6. underlie [n.底层]
>7. <font color = "red" size = 3>binary 二进制</font>
>8. interpret [v.解释，阐述]
>9. primitive [adj.原始的,最初的]
>10. contiguous [adj.连续的]
>11. terribly [ad.可怕，要命]
>12. for the sake of having a convenient metaphor [打个比喻]
>13. metaphor [n.比喻,隐喻] || analogy [n.比喻]
>14. omit [v.省略]
>15. tradeoff [n.权衡，平衡]
>16. bizarre [adj.奇怪的]
>17. as an analogy .打个比方
-----
>The Mystery of the Walrus[海象之谜]
>Try to predict what happens when we run the code below. Does the change to b affect a?

```java
walrus a = new walrus(1000,8.3);
walrs b;
b = a;
b.weight = 5;
System.out.println(a);
System.out.println(b);
```

>In java, there are <font color = "red" size = 3>8</font> primitive types:byte,short,int ,long ,float,double,boolean,and char.

----
>Declaring a Variable (Simplified)


>The Java language provides no way for you to know the location of the box In other words, the exact memory address is below the level of abstraction accessible to us in Java. This is unlike languages like C where you can ask the language for the exact address of a piece of data.

>Java does not write anything into the reserved box when a variable is declared. In other words, there are no default values. As a result, the Java compiler prevents you from using a variable until after the box has been filled with bits using the `=` operator.

----
>Reference Types

>Arrays, is not a primitive type but rather a `reference type`.

>When we _instantiate_ an Object using `new` (e.g. Dog, Walrus, Planet), Java first allocates a box for each instance variable of the class, and fills them with a default  [默认的] value.


>When we declare a varible of any reference type(Walrus,Dog,Planet,array,etc.),Java allocates a box of 64bits,no matter what type of object.
>It may seem bizarre that no matter the type of object,we only get 64 bits to  store it.
>Now,this problem is easily resolved with the follwing piece of information:<font color = "pink" size = 4>the 64 bit box contains bot the data about the walrus,but instead the address of the Walrus in memoy.</font>
[64bite空间b并不是储存Reference Type 的data部分，而是储存内存地址！]


-----
>Parameter Passing [参数传递]

>"pass by value" -- we always pass by value

```java
public static double average(double a , double b){
	return (a + b) / 2;
}
public class void main(String args){
	double x = 5.5;
	doubley y = 10.5;
	double avg = average(x,y);
}
```

>If the average function were to chage a the x in main would be unchaged,since the GRoE tells us that we'd simply be filling in the box labelde a with <font color = "red" size = 4> new bits </font>


----
>Instantiation of Arrays

```java
int[] x;
Planet[] planets;
```
<font color = "pink" size = 4>Both of these declarations create memory boxes of 64 bits.</font>

```java
x = new int[]{0,1,2,3,4};
```
<font color = "pink" size = 4>Then the `new` keyword creates 5 boxes of 32 bits each and returns the address of the overall object for assignment to x.</font>

>"The Law of the Broken Futon" 是由约瑟夫·戈登-莱维特（Joseph Gordon-Levitt）首次提出的一个概念，用来形容在共享公寓或宿舍中，床垫或沙发床被损坏或破裂的现象。
>根据这个概念，如果你和其他人共享一个公寓或宿舍，而且你们有一个沙发床或折叠床作为客人住宿的选择，那么在某个时刻，这张床垫几乎一定会被损坏或破裂。"The Law of the Broken Futon" 的核心理论是：床垫比较容易坏，并且每个人都觉得不是自己造成的，因此很少有人会主动修理或替换它，最终导致床垫越来越糟糕。
>这个概念可以看做是“公地悲剧”（Tragedy of the Commons）在日常生活中的一种体现。它提示我们，在共享资源的环境中，每个人都应该对资源进行合理的使用和维护，否则就会导致资源的浪费和破坏。


-----
>IntLists "Linked List" [链表]

>OOP strategy---adding heper methods 

1.size and interativeSize
```java
public class IntList {  
    public int first;  
    public IntList rest;  
  
    public IntList(int f , IntList r){  
        first = f;  
        rest = r;  
    }  
  
    public int size(){  
        if (rest == null){  
            return 1;  
        }  
        return this.rest.size() + 1;  
    }  
  
    public int iterativeSize(){  
        int res = 0;  
        IntList p = this;  
        while(p != null){  
            res += 1;  
            p = p.rest;  
        }  
        return res;  
    }  
}
```

```java
/*
	最典型的错误
*/
	public int interiveSize(){
		int res = 0;
		while(this != null){
			res += 1;
			this = this.rest;
		}
	}
```

<font color = "pink" size = 5 >You need that pointer because you can't reassign "this" in Java.</font>
>There is a conceptual error in your code: basically you are not creating any new stack element with your push method.

>But the problem is that calling the class listStack becomes misleading, because actually what you want to create are new elements of the stack, so you should create a class node maybe. Moreover you can't ovveride "this" because it is a java keyword and it always refers to the current object.

>To give you a hint of what to do to implement a stack as a linked list you should create `class Node` with a value field `value` and a reference to the previous `Node` (the first node will just have a null pointer) .

>In the class `ListStack`you should have a reference to the last node and its `push()` method should create a new Node and set this one as the new last node.


2.Get

>Exercise: Write a method `get(int i)` that returns the ith item of the list. For example, if `L` is 5 -> 10 -> 15, then `L.get(0)` should return 5, `L.get(1)` should return 10, and `L.get(2)` should return 15. It doesn't matter how your code behaves for invalid `i`, either too big or too small.


```java
/*No-Recusion*/
public int get(int i){
	int j = 0;
	IntList p = this;
	while(j < i){
		j +=1;
		p = p.rest;
	}
	return p.first;
}

/*recusion*/
public int get(int i ){
	if (i  == 0){
		return first;
	}
	return rest.get(i-1);
}

```
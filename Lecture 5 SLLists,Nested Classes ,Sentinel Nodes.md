- [x]  video
- [x] Reading
- [x] Scope,Pass by Value,Static
- [ ] Project 0
----
Video

----
### Chapter 2.2  SLLists, Nested Classes, Sentinel Nodes

>public & private 

>Private variables and methods can only be accessed by code inside the same `.java` file[只能在被创建的类中使用

>nested class[嵌套类]

```java
public class SLList {  
  
    /*嵌套类 (nested class)*/    public static class IntNode {  
        public int item;  
        public IntNode next;  
  
        public IntNode(int i , IntNode n){  
            item = i;  
            next = n;  
        }  
    }
}
```
>`static`+ class 表明这个类不会范围外部非静态类的任何东西，包括方法，变量等....
>Having a nested class has <font color = 'red' size = 4>no meaningful effect</font> on code performance, and is simply a tool for keeping code organized.[非静态嵌套类（即普通内部类）可以访问外部类的所有成员变量和方法，包括静态成员变量和方法。与静态内部类不同，普通内部类是依赖于外部类对象存在的，因此它们可以访问外部类对象的所有成员。]

```java
public class SLList {  
  
    /*嵌套类 (nested class)*/    public static class IntNode {  
        public int item;  
        public IntNode next;  
  
        public IntNode(int i , IntNode n){  
            item = i;  
            next = n;  
        }  
    }  
  
    private IntNode sentinel;  
    private int size;  
    public SLList(){  
        sentinel = new IntNode(63,null);  
        size = 0;  
    }  
  
    public SLList(int x){  
        sentinel = new IntNode(63,null);  
        sentinel.next = new IntNode(x,null);  
        size = 1;  
    }  
  
    public void addFirst(int x){  
        sentinel.next = new IntNode(x ,sentinel.next);  
        size += 1;  
    }  
  
    public int getFirst(){  
        return sentinel.next.item;  
    }  
  
    public void addLast(int x){  
        IntNode p = sentinel;  
        while (p.next != null){  
            p = p.next;  
        }  
        p.next = new IntNode(x, p.next);  
        size += 1;  
    }  
/*  
*   private static int size(IntNode p) {  
    if (p.next == null) {        return 1;    }  
    return 1 + size(p.next);}  
*   public int size(){  
*       return size(first);  
* }  
*   一种更为普遍的解决办法。解决一些需要递归但缺少某些变量的情况尤其有用.  
*   overloaded 重载：两种相同名字不同用途  
*   在Java中是被允许的，只要这两个函数具有相对明显的参数差异.  
* */  
    public int size(){  
        return size;  
    }  
    public static void main(String[] args){  
        SLList L = new SLList(3);  
        L.addFirst(5);  
        L.addFirst(10);  
        L.addLast(20);  
        System.out.println(L.getFirst());  
        System.out.println(L.size());  
    }  
}
```

>主要是编码课，实际内容好像不太多，整理一下.
>1. 对比于上一届的Intlist，SLList更容易被使用，因为它不需要被显示的表明pointer.
>2. public、static、private的用法
>3. 使用哨兵节点(sentinel) 也就是使用不变量(invariable)
- [x]  Lecture 3
- [x] Reading chaptert 3.1
- [ ] Project 0 [2048]
- [x] Selection Sort[第一个算法---选择排序] && Algs4
- [x] lab 2
-----
#### 1.Reading && lecture
>关于Juint

```java
if (input != expected) //为什么不行！
<记忆一下，数组相同是啥东西呢>
```

```java
public class TestSort {
    /** Tests the sort method of the Sort class. */
    public static void testSort() {
        String[] input = {"beware" , "of", "falling", "rocks"};
        String[] expected = {"beware" , "falling", "of", "rocks"};
        Sort.sort(input);
        for (int i = 0; i < input.length; i += 1) {
           if (!input[i].equals(expected[i])) {
               System.out.println("Mismatch at position " + i + ", expected: '" + expected[i] + 
                             "', but got '" + input[i] + "'");
               return;
         }
        }
    }
    public static void main(String[] args) {
		testSort();
    }
}
```

```java
//Juint优化上面代码!
**
public class TestSort {
  /** Tests the sort method of the Sort class. */  
  public static testSort() {
    String[] input = {"cows", "dwell", "above", "clouds"};
    String[] expected = {"above", "clouds", "cows", "dwell"};
    Sort.sort(input);
    org.junit.Assert.assertArrayEquals(expected, input);//需要代入第三方包Junit库
  }
  public static void main(String[] args) {
    testSort();
  }
}

**
```

----
#### 5. Lab 2 Test
>BreakPoint and set-up 断点和步入

![[Pasted image 20230517102706.png]]
> 粉红色底：断电位置
> 突出显示：即将进行的一步【特别注意！是下一步，而不是上一步】\

>Juint语法 --Java

JUnit是一个Java语言的单元测试框架。它由肯特·贝克和埃里希·伽玛建立，逐渐成为源于Kent Beck的sUnit的xUnit家族中为最成功的一个。 JUnit有它自己的JUnit扩展生态圈

```java
@Test
public void testMethod(){
	assertEquals(<expected>,<actual>);
	//注意位置，前面是期待后面是实际
}
```

![[Pasted image 20230517105245.png]]

![[Pasted image 20230517105304.png]]> 注意点
> 1. 每个测试方法的前面必须加上@Test
> 2. 所有测试方法必须都是非静态的（non-static）--需要被实例调用的方法
> 3. 短路测试--只要 有一个assert为false那么测试会直接终止


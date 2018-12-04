---
title: Java基础类型的自动拆装箱机制
date: 2018-09-20 11:28:08
tags: java
---

## What?

如下面的例子,在Java语言中,我可以为用包装后的类型直接为基础类型赋值,反之亦然.

```Java
public class Unboxing {
    public void test() {
        //自动装箱
        Integer count = 99;
        //自定拆箱
        int sum = count;
    }
}
```

# Why?

通过字节码,看看编译器默默为我们做了什么.

```text
Code:
  stack=1, locals=3, args_size=1
      0: bipush        99
      2: invokestatic  #2      // Method java/lang/Integer.valueOf:(I)Ljava/lang/Integer;
      5: astore_1
      6: aload_1
      7: invokevirtual #3      // Method java/lang/Integer.intValue:()I
    10: istore_2
    11: return
```

通过分析字节码,可以很清楚的看到,自动装箱过程中,编译器帮我们自动调用了`Integer.valueOf:(I)`[^1]和`Integer.intValue:()`方法来进行装箱和拆箱操作.

示例中的代码等价于

```Java
public class Unboxing {
    public void test() {
        //自动装箱
        Integer count = Integer.valueOf(99);
        //自定拆箱
        int sum = count.intValue();
    }
}
```

`Integer.valueOf(I)`方法具体实现见[Java中Integer实现](java-Interger)

# How?
通过上面的等价代码,很容易理解为什么拆箱过程中,可能出现的空指针异常的原因.


[^2]
[^3]
[^1]: **I** 表示**int**类型
[^2]: http://www.google.com
[^3]: http://www.google.com
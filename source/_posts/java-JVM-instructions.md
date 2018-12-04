---
title: JVM指令学习(1) aaload && aastore
date: 2018-09-26 10:00:57
tags:
---

## aa操作 array reference相关的操作

### aaload

`从array中载入一个reference, 参数都在操作数栈上`

```text
..., arrayref, index ->
..., value(reference)
```

arrayref 必须是一个指向成员是reference的引用(reference)
index 必须是一个**int**类型
value 是aaload操作取回来,并放在opstack顶部

### aastore

`存储一个reference值到数组的相应位置中`

```text
..., arrayref, index, value ->
...,
```

arrayref 必须是一个指向成员是reference的引用(reference)
index 必须是一个**int**类型
操作结束后三个参数都从opstack中弹出

## 总结

* 这个两个aa型的opcode参数全部由opstack栈顶给出

* index必须为**int**型,从JVM层面上限制了JVM语言中数组的最大长度为**Integer.MAX_VALUE** (2<sup>31</sup>-1)
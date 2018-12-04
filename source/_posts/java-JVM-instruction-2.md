---
title: JVM指令学习(2) aload_<n> & astore_<n>
date: 2018-09-28 16:01:44
tags:
---

# 1. aload index, aload_\<n>

`Load reference from local variable`

## forms

```text
aload = 25 (0x19)
aload_0 = 42 (0x2a)
aload_1 = 43 (0x2b)
aload_2 = 44 (0x2c)
aload_3 = 45 (0x2d)
```

## opstack

```text
... →
..., objectref
```

# 2. astore index, astore_\<n>

`Store reference into local variable`

## forms

```text
astore = 58 (0x3a)
astore_0 = 75 (0x4b)
astore_1 = 76 (0x4c)
astore_2 = 77 (0x4d)
astore_3 = 78 (0x4e)
```

## opstack

```text
..., objectref →
...
```

## Description

`
The <n> must be an index into the local variable array of the current frame (§2.6). The objectref on the top of the operand stack must be of type returnAddress or of type reference. It is popped from the operand stack, and the value of the local variable at <n> is set to objectref.
`

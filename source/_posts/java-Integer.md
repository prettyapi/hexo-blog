---
title: java_Integer
date: 2018-09-25 11:06:45
tags:
---

```Java
    public static Integer valueOf(int i) {
        //处于缓存区间的值 直接取缓存
        if (i >= IntegerCache.low && i <= IntegerCache.high)
            return IntegerCache.cache[i + (-IntegerCache.low)];
        return new Integer(i);
    }
```
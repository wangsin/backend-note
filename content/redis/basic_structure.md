---
title: "基础数据结构"
date: 2021-08-18T22:58:36+08:00
draft: true
---

# 字符串

Redis的字符串是动态字符串，是可以修改的字符串，内部结构类似于ArrayList，采用预分配冗余空间的方式来减少内共存的分配。

小于1M时，扩容空间翻倍。

大于1M时，每次多扩1M的空间。

字符串最大长度512M。

## 基础命令

```
-- 单独get/set

set name codehole

get name

exist name

del name


-- 批量get/set

mget name1 name2 name3

mset name1 boy name2 girl name3 duck

-- 过期时间

expire name 5

setex name 5 codehole

setnx name codehole

-- 自增
incr age

incrby age 5

incrby age -5

set codehole {Long.Max}

incr codehole
> ERR increment or decrement would overflow
```
## Simple Dynamic String

### 原理

### API

### 源码

TODO


# 列表

Redis的列表底层类似于链表的结构，插入和删除速度非常快O(1)，索引定位速度比较慢O(n)。

每个元素之间使用双向指针顺序，支持双向遍历。

列表弹出最后一个元素时，数据结构会被自动删除。
---
title: golang笔记-2-指针
date: 2016-11-17 02:42:55
tags: [golang, 存疑]
categories: golang
---
### 指针与内存
不能将指针与内存地址混为一谈。
- 内存地址：每个内存字节单元的唯一编号。
- 指针：专门用来保存地址的整形（整形？因为一切皆可用数字表示吗）变量。
<!--more-->
###### 如图：

表达式| p := &x | x := 100
---|---|---
memory | 0x1200| 100
address | 0x800|0x1200

###### &与*：
- 取址运算符：& ， 用于获取对象地址。
- 指针运算符：* ， 用于间接引用目标对象。

```
func main(){
    x := 10
    p := &x
    fmt.Println(p)  //  0xc42000a298
    fmt.Println(*p) //  10
}
```

### 指针运算
- 支持相等运算。
- 不支持加减运算、类型转换。
- 如果两个指针指向同一个地址，则二指针相等



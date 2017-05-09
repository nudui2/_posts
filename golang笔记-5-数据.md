---
title: golang笔记-5-数据
date: 2016-11-18 10:22:41
tags: golang
categories: golang
toc: true
---
### 字符串
字符串为不可变字节（byte）序列，是符合结构。

```
type stringStruct struct{
    str unsafe.Pointer
    len int
}
```
头部指针指向数组，无NULL结尾，默认为UTF-8存储Unicode字符。

len返回的是数组的字节长度。


```
func main(){
    s := "a"
    fmt.Println(s[0])   //  97
    
    fmt.Println(&s[0])   //  报错：cannot take the address of s[0]
    
    s = s + "b"
    fmt.Println(s > "aa")   //true
}

```

字符串遍历
```
func main(){
    s := "受命于天"
    for i := 0; i < len(s); i++ {
        fmt.Println(s[i])       //输出其byte ， 4 * 3 = 12 个字节
    }
    
    for index, val := range s {
        fmt.Println(index, val)        //输出每个汉字
    }
}
```
修改字符串
要求改字符串，须将其转换为可变类型（[ ]rune 或者 [ ]byte），修改之后再转回来。但，不管如何转换，都必定重新分配内存并复制数据。



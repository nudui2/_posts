---
title: golang笔记-3-表达式
date: 2016-11-17 19:06:22
tags: golang
categories: golang
---
### 关键字
##### 25个关键字
```
break continue, if else , go chan , var const type 

for range , go goto defer , switch case default fallthrough

package import , func struct return map select
```
### 流程控制
#### if .. else ..

- 表达式的值必须是bool类型。

- 表达式可以执行初始化语句。如下 :

```
var x int 

func xinit(){
    x = 1000
}

func main(){
    if xinit(); x > 100{
        ... //  可以执行
    }
    ...
}
```

#### switch case
无须break，自动在相应的case处执行完毕中断

- 一般形式 

```
func main(){
    a , b , c := 0 , 1 , 2
    
    switch x {
        case a , b : 
            fmt.Println("0 或者 1")
        case 4 : 
            fmt.Println("值为4")
        default : 
            fmt.Println("default value")
    }
}
```
- 表达式形式

```
func main(){
    a , b , c := 0 , 1 , 2
    
    switch x := 100 ; x {
        case a , b : 
            fmt.Println("0 或者 1")
        case 4 : 
            fmt.Println("值为4")
        default : 
            fmt.Println("default value")
    }
}
```
- fallthrough   必须放在case块的末尾

```
func main(){
    
    switch x := 100 ; x {
        case a , b : 
            fmt.Println("0 或者 1")
        case 100 : 
            x += 10
            fmt.Println(x)
            
            fallthrough     //无条件执行下一个case，default除外。
        case 101 :
            x += 10
            fmt.Println(x)
                            //如果还有fallthrough，则继续执行下一个非default的case
        default : 
            fmt.Println("default value")
    }
}
```

注意：
1. 不能出现重复的case。
2. 有时switch可代替if语句。

#### for
- golang中只有for这一种循环。
- for循环完成了java中的while循环、for..each循环。

```
//普通for循环
for i := 0 ; i < 100 ; i ++ {
    ...
}
```

```
//相当于while循环
for x < 10 {
   ... 
}
```

```
//相当于while true
for {
    ...
}
```
- **for range** 用于数据迭代，支持字符串、数组、数组指针、切片、字典、通道类型、键值数据

```
func main(){
    data := [10]int{1, 2, 3, 4 }
    
    for index , v := range data{
        fmt.Print("index is " + index)
        fmt.Println("value is " + v)
    }
}

```





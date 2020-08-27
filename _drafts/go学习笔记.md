title: go学习笔记
tags:
    - GO
    - Golang
---

# go []byte转化为字符串
描述：将一个[4]byte数组转化为ip地址
使用如下数据
data := []byte{127, 0, 0, 1}
得到 127.0.0.1
**思考**，这里需要将单个的字符转换为数字字符串，然后加上"."，这样，就组合成了

ASCII编码不是都可见的。
```go
package main

import (
    "fmt"
)

func main() {
    data := [4]byte{0x31, 0x32, 0x33, 0x34}
    str := string(data[:])
    fmt.Println(str)
}
```
这样做是不高效的,但是可以简写如下：
```go
func convert( b []byte ) string {
    s := make([]string,len(b))
    for i := range b {
        s[i] = strconv.Itoa(int(b[i]))
    }
    return strings.Join(s,",")
}
```
调用

bytes := [4]byte{1,2,3,4}
str := convert(bytes[:])

title: python函数参数理解
tags:
    - python
---

## python 函数参数参数

以下是调用函数时可使用的正式参数类型：

- 必备参数
- 命名参数
- 缺省参数
- 不定长参数

### 必备参数

必备参数须以正确的顺序传入函数。调用时的数量必须和声明时的一样。

调用printme()函数，你必须传入一个参数，不然会出现语法错误：
```
#coding=utf-8
#!/usr/bin/python

#可写函数说明
def printme( str ):
   "打印任何传入的字符串"
   print str;
   return;

#调用printme函数
printme();
```
以上实例输出结果：
```
Traceback (most recent call last):
  File "test.py", line 11, in <module>
    printme();
TypeError: printme() takes exactly 1 argument (0 given)
```
关键字参数

关键字参数和函数调用关系紧密，函数调用使用关键字参数来确定传入的参数值。

使用关键字参数允许函数调用时参数的顺序与声明时不一致，因为 Python 解释器能够用参数名匹配参数值。

以下实例在函数 printme() 调用时使用参数名：

#!/usr/bin/python
# -*- coding: UTF-8 -*-

#可写函数说明
def printme( str ):
   "打印任何传入的字符串"
   print str;
   return;

#调用printme函数
printme( str = "My string");

以上实例输出结果：

My string

下例能将关键字参数顺序不重要展示得更清楚：

#!/usr/bin/python
# -*- coding: UTF-8 -*-

#可写函数说明
def printinfo( name, age ):
   "打印任何传入的字符串"
   print "Name: ", name;
   print "Age ", age;
   return;

#调用printinfo函数
printinfo( age=50, name="miki" );

以上实例输出结果：

Name:  miki
Age  50

命名参数

命名参数和函数调用关系紧密，调用方用参数的命名确定传入的参数值。你可以跳过不传的参数或者乱序传参，因为Python解释器能够用参数名匹配参数值。用命名参数调用printme()函数：

#coding=utf-8
#!/usr/bin/python

#可写函数说明
def printme( str ):
   "打印任何传入的字符串"
   print str;
   return;

#调用printme函数
printme( str = "My string");

以上实例输出结果：

My string

下例能将命名参数顺序不重要展示得更清楚：

#coding=utf-8
#!/usr/bin/python

#可写函数说明
def printinfo( name, age ):
   "打印任何传入的字符串"
   print "Name: ", name;
   print "Age ", age;
   return;

#调用printinfo函数
printinfo( age=50, name="miki" );

以上实例输出结果：

Name:  miki
Age  50

缺省参数

调用函数时，缺省参数的值如果没有传入，则被认为是默认值。下例会打印默认的age，如果age没有被传入：

#coding=utf-8
#!/usr/bin/python

#可写函数说明
def printinfo( name, age = 35 ):
   "打印任何传入的字符串"
   print "Name: ", name;
   print "Age ", age;
   return;

#调用printinfo函数
printinfo( age=50, name="miki" );
printinfo( name="miki" );

以上实例输出结果：

Name:  miki
Age  50
Name:  miki
Age  35

不定长参数

你可能需要一个函数能处理比当初声明时更多的参数。这些参数叫做不定长参数，和上述2种参数不同，声明时不会命名。基本语法如下：

def functionname([formal_args,] *var_args_tuple ):
   "函数_文档字符串"
   function_suite
   return [expression]

加了星号（*）的变量名会存放所有未命名的变量参数。选择不多传参数也可。如下实例：

#coding=utf-8
#!/usr/bin/python

# 可写函数说明
def printinfo( arg1, *vartuple ):
   "打印任何传入的参数"
   print "输出: "
   print arg1
   for var in vartuple:
      print var
   return;

# 调用printinfo 函数
printinfo( 10 );
printinfo( 70, 60, 50 );

以上实例输出结果：

输出:
10
输出:
70
60
50

匿名函数

用lambda关键词能创建小型匿名函数。这种函数得名于省略了用def声明函数的标准步骤。

    Lambda函数能接收任何数量的参数但只能返回一个表达式的值，同时只能不能包含命令或多个表达式。
    匿名函数不能直接调用print，因为lambda需要一个表达式。
    lambda函数拥有自己的名字空间，且不能访问自有参数列表之外或全局名字空间里的参数。
    虽然lambda函数看起来只能写一行，却不等同于C或C++的内联函数，后者的目的是调用小函数时不占用栈内存从而增加运行效率。

语法

lambda函数的语法只包含一个语句，如下：

lambda [arg1 [,arg2,.....argn]]:expression

如下实例：

#coding=utf-8
#!/usr/bin/python

#可写函数说明
sum = lambda arg1, arg2: arg1 + arg2;

#调用sum函数
print "Value of total : ", sum( 10, 20 )
print "Value of total : ", sum( 20, 20 )

以上实例输出结果：

Value of total :  30
Value of total :  40

return语句

return语句[表达式]退出函数，选择性地向调用方返回一个表达式。不带参数值的return语句返回None。之前的例子都没有示范如何返回数值，下例便告诉你怎么做：

#coding=utf-8
#!/usr/bin/python

# 可写函数说明
def sum( arg1, arg2 ):
   # 返回2个参数的和."
   total = arg1 + arg2
   print "Inside the function : ", total
   return total;

# 调用sum函数
total = sum( 10, 20 );
print "Outside the function : ", total

以上实例输出结果：

Inside the function :  30
Outside the function :  30

变量作用域

一个程序的所有的变量并不是在哪个位置都可以访问的。访问权限决定于这个变量是在哪里赋值的。
变量的作用域决定了在哪一部分程序你可以访问哪个特定的变量名称。两种最基本的变量作用域如下：

    全局变量
    局部变量

变量和局部变量

定义在函数内部的变量拥有一个局部作用域，定义在函数外的拥有全局作用域。

局部变量只能在其被声明的函数内部访问，而全局变量可以在整个程序范围内访问。调用函数时，所有在函数内声明的变量名称都将被加入到作用域中。如下实例：

#coding=utf-8
#!/usr/bin/python

total = 0; # This is global variable.
# 可写函数说明
def sum( arg1, arg2 ):
   #返回2个参数的和."
   total = arg1 + arg2; # total在这里是局部变量.
   print "Inside the function local total : ", total
   return total;

#调用sum函数
sum( 10, 20 );
print "Outside the function global total : ", total

以上实例输出结果：

Inside the function local total :  30
Outside the function global total :  0

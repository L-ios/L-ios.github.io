title: sql模糊查询
tags:
---



SQL模糊查询，使用like比较字，加上SQL里的通配符，请参考以下：
1、LIKE'Mc%' 将搜索以字母 Mc 开头的所有字符串（如 McBadden）。
2、LIKE'%inger' 将搜索以字母 inger 结尾的所有字符串（如 Ringer、Stringer）。
3、LIKE'%en%' 将搜索在任何位置包含字母 en 的所有字符串（如 Bennet、Green、McBadden）。
4、LIKE'_heryl' 将搜索以字母 heryl 结尾的所有六个字母的名称（如 Cheryl、Sheryl）。
5、LIKE'[CK]ars[eo]n' 将搜索下列字符串：Carsen、Karsen、Carson 和 Karson（如 Carson）。
6、LIKE'[M-Z]inger' 将搜索以字符串 inger 结尾、以从 M 到 Z 的任何单个字母开头的所有名称（如 Ringer）。
7、LIKE'M[^c]%' 将搜索以字母 M 开头，并且第二个字母不是 c 的所有名称（如MacFeather）。

下面这句查询字符串，根据变量 zipcode_key 在邮政编码表 zipcode 中查询对应的数据，这句是判断变量 zipcode_key 为非数字时的查询语句，用 % 来匹配任意长度的字符串，从表中地址、市、省三列中查询包含关键字的所有数据项，并按省、市、地址排序。这个例子比较简单，只要你理解了方法就可以写出更复杂的查询语句。

sql = "select * from zipcode where (address like'%" & zipcode_key & "%') or (city like'%" & zipcode_key & "%') or (province like'%" & zipcode_key & "%') order by province,city,address

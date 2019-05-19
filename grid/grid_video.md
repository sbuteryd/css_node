
* * *
### lesson 3

`  grid-template-columns: repeat(3, 1fr)` 

repeat两个参数，重复的次数，重复的值

`  grid-template-columns: repeat(2, 1fr 2fr)`  

可以赋值多个

`  grid-template-columns: 400px repeat(2, 1fr 2fr)` 。

 固定值然后面重复值
 
```
.wrap {
  display: grid;
  /* grid-template-columns: 1fr 1fr 1fr; */
  grid-template-columns: repeat(3, 1fr)
}
```

我的理解；就是一个函数，两个参数 第一个是重复次数，第二个参数可以多个值。repeat前面也可以指定值把它想成一个值的另一种形式。



* * *
### lesson 2

fraction units：分数单位

`grid-template-columns: 1fr 1fr 1fr;`

自适应，平均分配的盒子的大小，而且是自适应

`grid-template-columns: 3fr 1fr 1fr;`  

设置占有的范围

`grid-template-columns: 3fr 1fr 300px;`

也可以固定一个盒子。

```
.wrap {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 200px 100px;
  grid-auto-rows: 200px;
  grid-gap: 10px 20px;
}
```
我的理解：就是盒子的百分比，和固定设置盒子的大小（width ：100%）。


* * *
### lesson 1 


` grid-template-columns  200px 200px 200px `
 
 用与创建三个宽200的列。相当于三盒子宽度为200px；

`  grid-template-rows: 200px 100px` 

用与创建行的高度是多少。

`  grid-auto-rows: 200px;` 

如果没有使用这个参数，9-10的格子，默认一个高度，因为我们没有设置第三行的高度是多少。使用这个参数那么接下来第三行第四行..都是200px这个宽度。

 ` grid-column-gap: 10px;` 
 
 1和2 用与列中间的距离。
 
`  grid-row-gap: 10px;`：
 
 用与第一行第二行之间的距离。
 
`grid-gap` 

距离简写 一个数字 就是行和列。 如果两个数字：第一是行、第二个是列。
```
.wrap {
  display: grid;
  grid-template-columns: 200px 200px 200px;
  grid-template-rows: 200px 100px;
  grid-auto-rows: 200px;
  grid-column-gap: 10px;
  grid-row-gap: 10px;
  grid-gap: 10px 200px;
}
```


| 第一行 | 1 | 2 |3  | 4 |
| --- | --- | --- | --- | --- |
| 第二行 |5  | 6 | 7 | 8 |
| 第三行 | 9 | 10 |11  | 12 

我的理解：一次创建多个盒子。

columns:创建盒子的宽度
row：就是创建盒子的长度。
gap:盒子之间的距离。
grid-auto-row：设置非指定长度是多少,改变默认的值是多少。


# 函数
## 对线性数组建堆并使用
* 比优先队列快
* 堆的操作中规则必须一致
* 第三个参数都可以省略,默认大根堆,可以用来指定堆的规则,例如用 greater\<tint\>() 指定小根堆
```c++

make_heap( begin(),end() ) //建堆

push_heap( begin(),end() ) //把容器最后一个元素放入堆中,(提前在容器末尾放一个新元素)

pop_heap( begin(),end() ) //把堆顶元素放到容器末尾，完全删除需要操作容器

sort_heap( begin(),end() ) //将堆变成有序数组,注意规则必须和堆规则相同

is_heap( begin(),end() ) //判断是否是堆

```
## 对容器的各种操作
* 凡是涉及对容器分段操作,需要三个迭代器的参数的,第二个参数都是第二段的第一个元素
### 查找
```c++

find( begin(),end(),value ) //返回迭代器或者地址,如果不存在,返回最后一个元素的下一个,也就是结束()或者数组末尾下一位

search( begin(),end(),sub.begin(),sub.end() ) //返回子串开头的迭代器或者地址,如果不存在,返回最后一个元素的下一个,也就是结束()或者数组末尾下一位

lower_bound( begin(),end(),value ) //大于等于value的第一个值的迭代器或地址，没有则返回容器末尾的下一个

upper_bound( begin(),end(),value ) //大于value的第一个值的迭代器或地址，没有则返回容器末尾的下一个

binary_search( begin(),end(),value,cmp ) //二分查找是否存在，返回bool值

minmax_element( begin(),end() ) //返回一个pair对，第一个元素是最小值的迭代器或地址，第二个是最大值的

min( begin(),end() ) //同上
max( begin(),end() ) //同上

```
### 奇怪的操作
```c++

fill( begin(),end(),value ) //对范围填充，开始到结束-1

reverse( begin(),end() ) //反转开始()到结束-1

rotate( begin(),begin()+cnt,end() ) //轮转，将两段元素调换顺序，如123 456变成456 123

next_permutation( begin(),end() ) //按字典序升序，把数据变成下一个排列，已经是最大时返回false，并变成最小的排列

prev_permutation( begin(),end() ) //按字典序升序，把数据变成上一个排列，已经是最小时返回false，并变成最大的排列

accumulate( begin(),end(),init,function ) //把容器内数据做聚合操作，例如求和，init为初始值，默认是求和，返回值类型为初始值类型，使用场景例如求数据总和或者将vector<string>中元素拼接起来

partial_sum( begin(),end(),dest.begin(),function ) //对容器内数据做操作并保存到dest中，默认求前缀和，注意目标容器大小

```
### 排序相关
```c++
stable_sort( begin(),end(),cmp ) //稳定排序

unique( begin(),end() ) //对有序数组(只要重复元素相邻即可)使用，将重复元素多余的移到数据末尾，返回第一个重复元素的迭代器或地址

partition( begin(),end(),function ) //把数据分成两组，第三个参数接受一个元素类型的形参，返回bool值，作为分组依据，注意，不保证原来数据的相对位置

stable_partition( begin(),end(),function ) //同上，但保证组内相对位置

partition_copy( src.begin(),src.end(),true.begin(),true.end(),false,begin(),false.end(),function ) //保证组内相对位置，分到另外两个容器中

partition_point( begin(),end(),function ) //已分组后返回第二组的第一个元素的迭代器或地址

partial_sort( begin(),begin()+cnt,end(),cmp ) //排好前cnt个数，默认是前cnt小的数

nth_element( begin(),begin()+n,end(),cmp ) //把第n个元素放好，并且小于等于它的放前面，大于等于放后面，快排基础

merge( begin(),end(),begin(),end(),dest.begin(),cmp ) //归并两个有序的的容器的数据到第三个容器，注意第三个容器的大小要事先足够，而且只覆盖相应位置数据，不会清空第三个容器原来的数据

inplace_merge( begin(),begin()+cnt,end(),cmp ) //将前后分别有序的两部分归并

```
### 集合相关
```c++

set_difference( a.begin(),a.end(),b.begin(),b.end() ) //A-B

set_intersection( a.begin(),a.end(),b.begin(),b.end() ) //A交B

set_symmertric_difference( a.begin(),a.end(),b.begin(),b.end() ) //对称差集

set_union( a.begin(),a.end(),b.begin(),b.end() ) //A并B

```

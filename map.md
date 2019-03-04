#### map 和 foreach 区别

+ 如果你习惯使用函数是编程，那么肯定喜欢使用map()。因为forEach()会改变原始的数组的值，而map()会返回一个全新的数组，原本的数组不受到影响。

> 核心要点
+ 能用forEach()做到的，map()同样可以。反过来也是如此。
+ map()会分配内存空间存储新数组并返回，forEach()不会返回数据。
+ forEach()允许callback更改原始数组的元素。map()返回新的数组。


```
let arr = [1, 2, 3, 4, 5];

var bb = arr.forEach((num, index) => {
    return arr[index] = num * 2;
}); // undefined

let doubled = arr.map(num => {
    return num * 2;
});  // [4, 8, 12, 16, 20]

```


[操作数据方法对比](./images/map.jpeg)
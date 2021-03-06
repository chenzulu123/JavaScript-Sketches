- 常规
  + .length
  + Array.isArray(arr)
  + .toString()
- 格式转换
  + .join(divider)
  + Array.from()
- 栈与队列
  + .push()
  + .pop()
  + .shift()
  + .unshift()
- 排序
  + .reverse()
  + .sort()
- 分割与组合
  + .concat()
  + .slice(start, end)
- 删除/替换
  + .splice(start, n, value)
- 查询
  + .indexOf(value,start)
  + .lastIndexOf()
  + .includes(value)
  + .find(function(val, index, arr) {}, thisArg) 返回满足函数的值，如无则返回 undefined
  + .findIndex(function(val, index, arr) {}, thisArg) 返回满足函数的值的索引，如无则返回 -1
- 迭代
  + .every()
  + .some()
  + .filter()
  + .forEach()
  + .map()
  + .entries()
- 归并
  + .reduce(function (prev, cur, index, array) {}, init)
  + .reduceRight()
- 填充
  + .fill(value, start, end)
- 创建
  + Array.of()
- 复制
  + .copyWithin(target, start, end)


### 比较函数的基本格式
```js
function compare (v1, v2) {
  if (v1 < v2) {
    return -1; // v1 和 v2 位置不变
  } else if (v1 > v2) {
    return 1; // v1 和 v2 交换位置
  } else {
    return 0; // v1 和 v2 位置不变
  }
}
// 数组排序
var numbers = [4, 2, 5, 1, 3];
numbers.sort(function(a, b) {
  console.log(`a=${a}, b=${b}, ${numbers}`)
  return a - b;
});
// a=4, b=2, [4,2,5,1,3]
// a=4, b=5, [2,4,5,1,3]
// a=5, b=1, [2,4,5,1,3]
// a=4, b=1, [2,4,5,5,3]
// a=2, b=1, [2,4,4,5,3]
// a=5, b=3, [1,2,4,5,3]
// a=4, b=3, [1,2,4,5,5]
// a=2, b=3, [1,2,4,4,5]
```


### 迭代方法的函数参数
```js
function (item, index, array) {
  return sth;
}

// 迭代方法除接收一个迭代器函数外，还接受第二个参数，表示迭代器函数的 this 指向的对象
```


### 数组操作的一些技巧
```js
// 复制数组（浅复制）
var copies = someArray.slice(0);

// 生成自然数列
var arr = Array(9).fill().map((_, i) => i);
Array.from({length: 5}, (_, index) => index);

// 计算数组中某一个值出现的次数
var countOccurrences = (arr, value) => arr.reduce((pre, next) => next === value ? pre + 1 : pre, 0)

// 找出数组中唯一的值
arr.filter(i => arr.indexOf(i) === arr.lastIndexOf(i))

// 乱序
var shuffle = arr => arr.sort(() => Math.random() - 0.5);

// 解析 query
var query = 'name=Peter&age=12';
query.split('&').reduce(function (pre, next) {
  next = next.split('=');
  pre[next[0]] = next[1];
  return pre
}, {})
```
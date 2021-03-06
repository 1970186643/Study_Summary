# 复杂度分析
问题&Q：如何分析、统计算法的执行效率和资源消耗？

- 复杂度分析是算法的精髓
1. 时间复杂度
2. 空间复杂度

## 大 O 复杂度表示法
```js
function sum(n) {
  let sum = 0;
  for(let i = 0; i < n; i++) {
    sum = sum + i;
  }
  return sum;
}
```
假设每一行读取代码的时间为time，则第二行代码读取为time，第三第四为2*n*time的时间，则总时间为：(2n+1)*time的时间。

+ 结论：所有代码的执行时间 T(n) 与每行代码的执行次数 n 成正比。
这时候大O公式就可以表示为：   **T(n) = O(f(n))**
其中**T(n)**表示代码的执行时间，**n**表示为数据规模大小，**f(n)**每行代码执行的次数总和。而**大O**表示代码执行时间随数据规模增长的变化趋势，所有也叫**渐进时间复杂度**，简称**时间复杂度**

### 时间复杂度分析

1. 只关注循环执行次数最多的一段代码
```js
function sum(n) {
  let sum = 0;
  for(let i = 0; i < n; i++) {
    sum = sum + i;
  }
  return sum;
}
```
就比如这一段代码，我们值需要关心for循环中的代码即可，它和n的量级相关，其他的都可以忽略。
2. 加法法则：总复杂度等于量级最大的那段代码的复杂度
```js
function sum(n) {
  let sum = 0;
  for(let i = 0; i < n; i++) {
    sum1 = sum + i;
  }
  for(let i = 0; i < n; i++) {
    for(let j = 0; j < n; j++) {
      sum2 = sum + i*j;
    }
  }
  return sum1 + sum2;
}
```
就比如这一段代码ji，可以很轻松分析出两次for循环中的时间复杂度O(n)和O(n*2)，那么O(n)就会取两者的更大值作为时间复杂度。
3. 乘法法则：嵌套代码的复杂度等于嵌套内外代码复杂度的乘积
```js
function sum(n) {
  let sum = 0;
  for(let i = 0; i < n; i++) {
    sum = sum + i;
  }
  return sum;
}
function sum1(n) {
  let sum1 = 0;
  for(let i = 0; i < n; i++) {
    sum = sum + sum(i);
  }
  return sum1;
}
```
就比如这一段代码,这是嵌套的循环，就是O(n)*O(n)了

### 空间复杂度
空间复杂度全称就是渐进空间复杂度，表示算法的存储空间与数据规模之间的增长关系。

- 常用的复杂度级别？
1. 多项式阶：随着数据规模的增长，算法的执行时间和空间占用，按照多项式的比例增长。包括，
O(1)（常数阶）、O(logn)（对数阶）、O(n)（线性阶）、O(nlogn)（线性对数阶）、O(n^2)（平方阶）、O(n^3)（立方阶）
2. 非多项式阶：随着数据规模的增长，算法的执行时间和空间占用暴增，这类算法性能极差。包括，
O(2^n)（指数阶）、O(n!)（阶乘阶）




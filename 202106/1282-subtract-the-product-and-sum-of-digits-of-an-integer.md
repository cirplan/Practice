### 1281. 整数的各位积和之差

> 题目

[链接](https://leetcode-cn.com/problems/subtract-the-product-and-sum-of-digits-of-an-integer/)

> 思路

循环

> 代码

```js
/**
 * @param {number} n
 * @return {number}
 */
var subtractProductAndSum = function (n) {
    const arr = n.toString().split('');
    let product = 1;
    let sum = 0;

    for (let i = 0; i < arr.length; i++) {
        product *= arr[i];
        sum += +arr[i];
    }

    return product - sum;
};
```

> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(1)。

> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了30.19%的用户

内存消耗：38.2 MB, 在所有 JavaScript 提交中击败了15.19%的用户
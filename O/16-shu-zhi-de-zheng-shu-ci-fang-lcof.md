### 剑指 Offer 16. 数值的整数次方

> 题目

实现函数double Power(double base, int exponent)，求base的exponent次方。不得使用库函数，同时不需要考虑大数问题。

 

示例 1:
```
输入: 2.00000, 10
输出: 1024.00000
```

示例 2:
```
输入: 2.10000, 3
输出: 9.26100
```

示例 3:
```
输入: 2.00000, -2
输出: 0.25000
解释: 2-2 = 1/22 = 1/4 = 0.25
```

说明:

-100.0 < x < 100.0
n 是 32 位有符号整数，其数值范围是 [−231, 231 − 1] 。

> 思路

二分法：

* 当 n 为偶数： x^n = (x^2)^{n/2}
* 当 n 为奇数： x^n = x(x^2)^{n/2}，即会多出一项 xx ；

> 代码

```js
/**
 * @param {number} x
 * @param {number} n
 * @return {number}
 */
var myPow = function(x, n) {
    const isNegative = n < 0;
    const result = absMyPow(x, Math.abs(n));
    return isNegative ? 1 / result : result;
};

function absMyPow(base, exponent) {
    if (exponent === 0) {
        return 1;
    }

    if (exponent === 1) {
        return base;
    }

    const subResult = absMyPow(base, Math.floor(exponent / 2));
    return exponent % 2 ? subResult * subResult * base : subResult * subResult;
}
```

> 复杂度分析

时间复杂度 : O(log2n)。

空间复杂度 : O(1)。

> 执行

执行用时：136 ms, 在所有 JavaScript 提交中击败了5.07%的用户

内存消耗：38.9 MB, 在所有 JavaScript 提交中击败了66.57%的用户
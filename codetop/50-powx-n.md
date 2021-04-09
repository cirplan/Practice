### 50. Pow(x, n)

> 题目

[链接](https://leetcode-cn.com/problems/powx-n/)

> 思路

使用递归

> 代码

```js
/**
 * @param {number} x
 * @param {number} n
 * @return {number}
 */
var myPow = function (x, n) {
    return n >= 0 ? quickMul(x, n) : 1.0 / quickMul(x, -n);

    function quickMul(x, N) {
        if (N == 0) {
            return 1.0;
        }
        let y = quickMul(x, Math.floor(N / 2));
        return N % 2 == 0 ? y * y : y * y * x;
    }
};
```

> 复杂度分析

时间复杂度：O(logn)。

空间复杂度：O(logn)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了90.42%的用户

内存消耗：38.8 MB, 在所有 JavaScript 提交中击败了87.18%的用户
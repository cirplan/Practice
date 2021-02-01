### 剑指 Offer 10- II. 青蛙跳台阶问题

> 题目

一只青蛙一次可以跳上1级台阶，也可以跳上2级台阶。求该青蛙跳上一个 n 级的台阶总共有多少种跳法。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

示例 1：
```
输入：n = 2
输出：2
```

示例 2：
```
输入：n = 7
输出：21
```

示例 3：
```
输入：n = 0
输出：1
```

提示：

0 <= n <= 100

> 思路

斐波那契数列

> 代码

```js
/**
 * @param {number} n
 * @return {number}
 */
var numWays = function (n) {
    if (n <= 1) return 1
    else if (n === 2) return 2
    let res1 = 1
    let res2 = 2
    for (let i = 2; i < n; i++) {
        let t = res1
        res1 = res2
        res2 = (t + res2) % 1000000007
    }
    return res2
};
```

> 复杂度分析

时间复杂度 : O(n)。

空间复杂度 : O(1)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了70.89%的用户

内存消耗：37.9 MB, 在所有 JavaScript 提交中击败了20.75%的用户
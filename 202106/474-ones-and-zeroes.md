### 474. 一和零

> 题目

[链接](https://leetcode-cn.com/problems/ones-and-zeroes/)

> 思路

？？

> 代码

```js
/**
 * @param {string[]} strs
 * @param {number} m
 * @param {number} n
 * @return {number}
 */
var findMaxForm = function (strs, m, n) {
    const dp = new Array(m + 1).fill(0).map(() => new Array(n + 1).fill(0));
    const length = strs.length;
    for (let i = 0; i < length; i++) {
        const zerosOnes = getZerosOnes(strs[i]);
        const zeros = zerosOnes[0], ones = zerosOnes[1];
        for (let j = m; j >= zeros; j--) {
            for (let k = n; k >= ones; k--) {
                dp[j][k] = Math.max(dp[j][k], dp[j - zeros][k - ones] + 1);
            }
        }
    }
    return dp[m][n];
};

const getZerosOnes = (str) => {
    const zerosOnes = new Array(2).fill(0);
    const length = str.length;
    for (let i = 0; i < length; i++) {
        zerosOnes[str[i].charCodeAt() - '0'.charCodeAt()]++;
    }
    return zerosOnes;
}

```

> 复杂度分析

时间复杂度：O(lmn+L)。其中 l 是数组 strs 的长度，m 和 n 分别是 0 和 1 的容量，L 是数组 strs 中的所有字符串的长度之和。

空间复杂度：O(mn)。

> 执行

执行用时：192 ms, 在所有 JavaScript 提交中击败了54.05%的用户

内存消耗：39.3 MB, 在所有 JavaScript 提交中击败了95.50%的用户
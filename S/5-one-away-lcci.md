### 面试题 01.05. 一次编辑

> 题目

[链接](https://leetcode-cn.com/problems/one-away-lcci/)

> 思路

分别从头和尾设置指针，对比字符是否相同。

> 代码

```js
/**
 * @param {string} first
 * @param {string} second
 * @return {boolean}
 */
var oneEditAway = function (first, second) {
    let changeCount = 0;
    const fitst_len = first.length;
    const second_len = second.length;

    if (Math.abs(fitst_len - second_len) > 1) {
        return false;
    }

    let i = 0;
    let j = fitst_len - 1;
    let k = second_len - 1;

    while (i < fitst_len && i < second_len && first[i] === second[i]) {
        i++;
    }

    while (j >= 0 && k >= 0 && first[j] === second[k]) {
        j--;
        k--;
    }
    
    return j - i < 1 && k - i < 1;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：96 ms, 在所有 JavaScript 提交中击败了86.89%的用户

内存消耗：39.3 MB, 在所有 JavaScript 提交中击败了48.36%的用户
### 1869. 哪种连续子字符串更长

> 题目

[链接](https://leetcode-cn.com/problems/longer-contiguous-segments-of-ones-than-zeros/)

> 思路

循环

> 代码

```js
/**
 * @param {string} s
 * @return {boolean}
 */
var checkZeroOnes = function (s) {
    if (s.indexOf(1) === -1) return false;
    if (s.indexOf(0) === -1) return true;
    const len = [0, 0];
    for (let i = 0; i < s.length; i++) {
        let step = 0;
        let max = 0;
        while (s[i + step] === s[i]) {
            step++;
            max++;
        }
        len[s[i]] = Math.max(max, len[s[i]]);
        i += step - 1;
    }
    return len[1] > len[0];
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了54.76%的用户

内存消耗：38.1 MB, 在所有 JavaScript 提交中击败了80.61%的用户

### 面试题 01.04. 回文排列

> 题目

[链接](https://leetcode-cn.com/problems/palindrome-permutation-lcci/)

> 思路

回文的规律是，奇数的字母最多出现一次。

> 代码

```js
/**
 * @param {string} s
 * @return {boolean}
 */
var canPermutePalindrome = function (s) {
    let sMap = new Map();

    for (let i = 0; i < s.length; i++) {
        const _s = s[i];
        sMap.set(_s, (sMap.get(_s) || 0) + 1);
    }

    let odd = 0;
    for (let [key, val] of sMap) {
        if (val % 2 === 0) {
            continue;
        } else {
            if (odd) {
                return false;
            }

            odd++;
        }
    }

    return true;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了51.42%的用户

内存消耗：37.6 MB, 在所有 JavaScript 提交中击败了84.83%的用户


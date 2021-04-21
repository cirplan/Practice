### 387. 字符串中的第一个唯一字符

> 题目

[链接](https://leetcode-cn.com/problems/first-unique-character-in-a-string/)

> 思路

循环两次

> 代码

```js
/**
 * @param {string} s
 * @return {number}
 */
var firstUniqChar = function (s) {
    let cache = new Map();
    for (let i = 0, len = s.length; i < len; i++) {
        const _s = s.charAt(i);
        cache.set(_s, (cache.get(_s) || 0) + 1);
    }

    let _s;
    for (let [key, val] of cache) {
        if (val === 1) {
            _s = key;
            break;
        }
    }

    return s.indexOf(_s)
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：144 ms, 在所有 JavaScript 提交中击败了37.01%的用户

内存消耗：40.9 MB, 在所有 JavaScript 提交中击败了81.53%的用户

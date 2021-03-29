### 3. 无重复字符的最长子串

> 题目

[链接](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)

> 思路

使用滑动窗口

> 代码

```js
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function (s) {
    const len = s.length;
    if (!len) return 0;
    let map = new Map();
    let max = 0;
    let left = 0;
    for (let i = 0; i < len; i++) {
        if (map.has(s.charAt(i))) {
            left = Math.max(left, map.get(s.charAt(i)) + 1);
        }
        map.set(s.charAt(i), i);
        max = Math.max(max, i - left + 1);
    }
    return max;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：96 ms, 在所有 JavaScript 提交中击败了97.78%的用户

内存消耗：40.2 MB, 在所有 JavaScript 提交中击败了87.94%的用户

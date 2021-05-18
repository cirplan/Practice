### 557. 反转字符串中的单词 III

> 题目

[链接](https://leetcode-cn.com/problems/reverse-words-in-a-string-iii/)

> 思路

循环，使用额外空间

> 代码

```js
/**
 * @param {string} s
 * @return {string}
 */
var reverseWords = function (s) {
    const ret = [];
    const length = s.length;
    let i = 0;
    while (i < length) {
        let start = i;
        while (i < length && s.charAt(i) != ' ') {
            i++;
        }
        for (let p = start; p < i; p++) {
            ret.push(s.charAt(start + i - 1 - p));
        }
        while (i < length && s.charAt(i) == ' ') {
            i++;
            ret.push(' ');
        }
    }
    return ret.join('');
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：100 ms, 在所有 JavaScript 提交中击败了60.80%的用户

内存消耗：47.8 MB, 在所有 JavaScript 提交中击败了5.34%的用户

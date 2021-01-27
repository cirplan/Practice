### 剑指 Offer 05. 替换空格

> 题目

请实现一个函数，把字符串 s 中的每个空格替换成"%20"。

示例 1：
```
输入：s = "We are happy."
输出："We%20are%20happy."
```

限制：

0 <= s 的长度 <= 10000

> 思路

在js里，这道题没什么特别，遍历一次输出即可。但在内存严格控制的语言，从后到前遍历是最佳的。

> 代码

```js
/**
 * @param {string} s
 * @return {string}
 */
var replaceSpace = function(s) {
    let list = [];
    let i = 0;
    while (i < s.length) {
        const _s = s.charAt(i);
        if (_s === ' ') {
            list.push('%20');
        } else {
            list.push(_s);
        }
        i++;
    }

    return list.join('');
};
```

> 复杂度分析

时间复杂度 : O(n)。

空间复杂度 : O(n)。

> 执行

执行用时：72 ms, 在所有 JavaScript 提交中击败了94.97%的用户

内存消耗：37.7 MB, 在所有 JavaScript 提交中击败了33.13%的用户
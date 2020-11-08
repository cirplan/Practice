### 32. 最长有效括号

> 题目

给定一个只包含 '(' 和 ')' 的字符串，找出最长的包含有效括号的子串的长度。

示例 1:
```
输入: "(()"
输出: 2
解释: 最长有效括号子串为 "()"
```

示例 2:
```
输入: ")()())"
输出: 4
解释: 最长有效括号子串为 "()()"
```

> 思路

这一题解法很多，这里说通过栈的方式。先往栈里 push -1；然后遇到 （，把下标推到栈中；当遇到 ），则把栈 pop，再计算当前下标与栈顶下标的值，与最大值比较。

> 代码

```js
/**
 * @param {string} s
 * @return {number}
 */
var longestValidParentheses = function(s) {
    let stack = [];
    let maxLength = 0;
    let i = 0;
    stack.push(-1);
    while (i < s.length) {
        let str = s.charAt(i);
        if (str === '(') {
            stack.push(i);
        } else {
            stack.pop();
            if (!stack.length) {
                stack.push(i);
            }
            maxLength = Math.max(maxLength, i - stack[stack.length - 1]);
        }

        i++;
    }

    return maxLength;
};
```

> 复杂度分析

时间复杂度 : O(N)。

空间复杂度 : O(N)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了91.53%的用户。

内存消耗：40.3 MB, 在所有 JavaScript 提交中击败了22.76%的用户。

### 856. 括号的分数

> 题目

给定一个平衡括号字符串 S，按下述规则计算该字符串的分数：

() 得 1 分。
AB 得 A + B 分，其中 A 和 B 是平衡括号字符串。
(A) 得 2 * A 分，其中 A 是平衡括号字符串。

示例 1：
```
输入： "()"
输出： 1
```

示例 2：
```
输入： "(())"
输出： 2
```

示例 3：
```
输入： "()()"
输出： 2
```

示例 4：
```
输入： "(()(()))"
输出： 6
```

提示：

S 是平衡括号字符串，且只含有 ( 和 ) 。
2 <= S.length <= 50

> 思路

重点是记录深度，我们用栈来实现。当遇到 '(' ，往栈里 push 0，遇到 ')'，取出栈最后一项，取 Math.max(sum * 2, 1)。

> 代码

```js
/**
 * @param {string} S
 * @return {number}
 */
var scoreOfParentheses = function (S) {
    let sum = 0;
    let i = 0;
    let stackSum = [0];
    while (i < S.length) {
        let s = S.substr(i, 1);
        if (s === '(') {
           stackSum.push(0);
        } else {
           let sum = stackSum.pop();
           let num = stackSum.pop();
           stackSum.push(num + Math.max(sum * 2, 1));
        }
        i++;
    }

    return stackSum.pop();
};
```

> 复杂度分析

时间复杂度 : O(N)。

空间复杂度 : O(N)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了65.00%的用户。

内存消耗：37.9 MB, 在所有 JavaScript 提交中击败了10.00%的用户。

> 算法


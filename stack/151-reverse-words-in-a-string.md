### 151. 翻转字符串里的单词

> 题目

给定一个字符串，逐个翻转字符串中的每个单词。

说明：

无空格字符构成一个 单词 。
输入字符串可以在前面或者后面包含多余的空格，但是反转后的字符不能包括。
如果两个单词间有多余的空格，将反转后单词间的空格减少到只含一个。

示例 1：
```
输入："the sky is blue"
输出："blue is sky the"
```

示例 2：
```
输入："  hello world!  "
输出："world! hello"
解释：输入字符串可以在前面或者后面包含多余的空格，但是反转后的字符不能包括。
```

示例 3：
```
输入："a good   example"
输出："example good a"
解释：如果两个单词间有多余的空格，将反转后单词间的空格减少到只含一个。
```

示例 4：
```
输入：s = "  Bob    Loves  Alice   "
输出："Alice Loves Bob"
```

示例 5：
```
输入：s = "Alice does not even like bob"
输出："bob like even not does Alice"
```

提示：

1 <= s.length <= 104
s 包含英文大小写字母、数字和空格 ' '
s 中 至少存在一个 单词

进阶：

请尝试使用 O(1) 额外空间复杂度的原地解法。

> 思路

去掉头尾空白，然后读取每个单词，push到栈中，再pop。

> 代码

```js
/**
 * @param {string} s
 * @return {string}
 */
var reverseWords = function (s) {
    let stack = [];

    let i = 0;
    while (i < s.length) {
        const val = s[i]

        if (val === ' ') {
            const start = i;
            i++;
            while (i < s.length && s[i] === ' ') {
                i++;
            }

            if (start !== 0 && i !== s.length) {
                stack.push(val);
            }
        } else {
            let temp = val;
            i++;
            while (i < s.length && s[i] !== ' ') {
                temp += s[i];
                i++;
            }
            stack.push(temp);
        }
    }

    let str = '';
    while (stack.length) {
        str += stack.pop();
    }

    return str;
};
```

> 复杂度分析

时间复杂度 : O(N)。

空间复杂度 : O(N)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了84.47%的用户。

内存消耗：39.2 MB, 在所有 JavaScript 提交中击败了27.83%的用户。

> 算法


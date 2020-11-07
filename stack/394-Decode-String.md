### 394. 字符串解码

> 题目

给定一个经过编码的字符串，返回它解码后的字符串。

编码规则为: k[encoded_string]，表示其中方括号内部的 encoded_string 正好重复 k 次。注意 k 保证为正整数。

你可以认为输入字符串总是有效的；输入字符串中没有额外的空格，且输入的方括号总是符合格式要求的。

此外，你可以认为原始数据不包含数字，所有的数字只表示重复的次数 k ，例如不会出现像 3a 或 2[4] 的输入。

示例 1：
```
输入：s = "3[a]2[bc]"
输出："aaabcbc"
```

示例 2：
```
输入：s = "3[a2[c]]"
输出："accaccacc"
```

示例 3：
```
输入：s = "2[abc]3[cd]ef"
输出："abcabccdcdcdef"
```

示例 4：
```
输入：s = "abc3[cd]xyz"
输出："abccdcdcdxyz"
```

> 思路

使用栈，数字、[、字母都推到栈中，当遇到 ]，就取出栈中的数据，直到 [，这个时候再取出栈顶的数字，进行重复。最后把栈中的字符串拼起来。

> 代码

```js
/**
 * @param {string} s
 * @return {string}
 */
var decodeString = function (s) {
    if (!s.length) return s;

    let stack = [];
    let i = 0;
    let num = '';
    while (i < s.length) {
        const str = s.charAt(i);
        if (str == ']') {
            let _str = '';
            let _preStr = stack.pop();
            while (_preStr !== '[') {
                _str = _preStr + _str;
                _preStr = stack.pop();
            }
            let num = stack.pop();
            _str = repeat(_str, Number(num));
            stack.push(_str);
        } else if (/\d/.test(str)) {
            num += str;
        } else {
            if (str === '[') {
                num && stack.push(num);
                num = '';
            }
            stack.push(str);
        }
        i++;
    }

    let result = '';
    while (stack.length) {
        str = stack.pop();
        result = str + result;
    }

    return result;
}

function repeat(s, n) {
    let str = ''
    for (let i = 0; i < n; i++) {
        str += s;
    }
    return str;
}
```

> 复杂度分析

时间复杂度 : O(N)。

空间复杂度 : O(N)。

> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了22.96%的用户。

内存消耗：37.8 MB, 在所有 JavaScript 提交中击败了12.22%的用户。

> 算法


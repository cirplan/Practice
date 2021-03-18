### 面试题 01.01. 判定字符是否唯一

> 题目

[链接](https://leetcode-cn.com/problems/is-unique-lcci/)

> 思路

使用与 ，或运算

> 代码

```js
/**
 * @param {string} astr
 * @return {boolean}
 */
var isUnique = function (astr) {
    let mark = 0
    for (let i = 0; i < astr.length; i++) {
        const char = astr.charCodeAt(i);
        const move_bit = char - 'a'.charCodeAt();
        if ((mark & (1 << move_bit)) != 0) {
            return false;
        } else {
            mark |= (1 << move_bit)
        }
    }

    return true;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：72 ms, 在所有 JavaScript 提交中击败了94.06%的用户

内存消耗：37.6 MB, 在所有 JavaScript 提交中击败了51.91%的用户

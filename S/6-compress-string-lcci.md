### 面试题 01.06. 字符串压缩

> 题目

[链接](https://leetcode-cn.com/problems/compress-string-lcci/)

> 思路

循环一次

> 代码

```js
/**
 * @param {string} S
 * @return {string}
 */
var compressString = function (S) {
    let res = '';
    let preS = '';
    let count = 0;
    const len = S.length;
    for (let i = 0; i < len; i++) {
        const _s = S.charAt(i);
        if (i === 0) {
            preS = _s;
            count++;
        } else {
            if (preS === _s) {
                count++;
            } else {
                res += preS + count;
                count = 1;
                preS = _s;
            }
        }

        if (i === len - 1) {
            res += _s + count;
        }
    }

    return res.length < len ? res : S;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：96 ms, 在所有 JavaScript 提交中击败了49.07%的用户

内存消耗：39.6 MB, 在所有 JavaScript 提交中击败了87.73%的用户

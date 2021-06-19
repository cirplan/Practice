### 1239. 串联字符串的最大长度

> 题目

[链接](https://leetcode-cn.com/problems/maximum-length-of-a-concatenated-string-with-unique-characters/)

> 思路

回溯

> 代码

```js
/**
 * @param {string[]} arr
 * @return {number}
 */
var maxLength = function(arr) {
    let ans = 0;
    const masks = [];
    for (const s of arr) {
        let mask = 0;
        for (let i = 0; i < s.length; ++i) {
            const ch = s[i].charCodeAt() - 'a'.charCodeAt();
            if (((mask >> ch) & 1) !== 0) { // 若 mask 已有 ch，则说明 s 含有重复字母，无法构成可行解
                mask = 0;
                break;
            }
            mask |= 1 << ch; // 将 ch 加入 mask 中
        }
        if (mask > 0) {
            masks.push(mask);
        }
    }

    const backtrack = (masks, pos, mask) => {
        if (pos === masks.length) {
            ans = Math.max(ans, mask.toString(2).split('0').join('').length);
            return;
        }
        if ((mask & masks[pos]) === 0) { // mask 和 masks[pos] 无公共元素
            backtrack(masks, pos + 1, mask | masks[pos]);
        }
        backtrack(masks, pos + 1, mask);
    }

    backtrack(masks, 0, 0);
    return ans;
};
```

> 复杂度分析

时间复杂度：O(∣Σ∣+2 ^ n)。 ∣Σ∣ 是 arr 中所有字符串的长度之和，n 是 arr 的长度

空间复杂度：O(n)。

> 执行

执行用时：172 ms, 在所有 JavaScript 提交中击败了43.10%的用户

内存消耗：44.6 MB, 在所有 JavaScript 提交中击败了50.00%的用户

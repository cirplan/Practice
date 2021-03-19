### 面试题 01.02. 判定是否互为字符重排

> 题目

[链接](https://leetcode-cn.com/problems/check-permutation-lcci/)

> 思路

使用 Map 记录

> 代码

```js
/**
 * @param {string} s1
 * @param {string} s2
 * @return {boolean}
 */
var CheckPermutation = function (s1, s2) {
    let sMap = new Map()

    for (let i = 0; i < s1.length; i++) {
        const _s = s1[i];
        let val = sMap.get(_s);
        if (val) {
            sMap.set(_s, ++val);
        } else {
            sMap.set(_s, 1);
        }
    }

    for (let i = 0; i < s2.length; i++) {
        const _s = s2[i];
        let val = sMap.get(_s);
        if (val) {
            sMap.set(_s, --val);
        } else {
            return false;
        }
    }

    return true;
};
```


> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：76 ms, 在所有 JavaScript 提交中击败了88.47%的用户

内存消耗：37.6 MB, 在所有 JavaScript 提交中击败了63.92%的用户

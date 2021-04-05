### 165. 比较版本号

> 题目

[链接](https://leetcode-cn.com/problems/compare-version-numbers/)

> 思路

切割，对比。

> 代码

```js
/**
 * @param {string} version1
 * @param {string} version2
 * @return {number}
 */
var compareVersion = function (version1, version2) {
    const v1 = version1.split('.');
    const v2 = version2.split('.');
    const len1 = v1.length;
    const len2 = v2.length;

    let i = 0;
    let j = 0;

    while (i < len1 || j < len2) {
        const n1 = Number(i < len1 ? v1[i] : 0);
        const n2 = Number(j < len2 ? v2[j] : 0);

        if (n1 > n2) {
            return 1;
        } else if (n1 < n2) {
            return -1;
        } else {
            i++;
            j++;
        }
    }

    return 0;
};
```

> 复杂度分析

时间复杂度：O(max(N,M))。

空间复杂度：O(N+M)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了78.56%的用户

内存消耗：38 MB, 在所有 JavaScript 提交中击败了15.73%的用户

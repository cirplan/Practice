### 274. H 指数

> 题目

[链接](https://leetcode-cn.com/problems/h-index/)

> 思路

排序

> 代码

```js
/**
 * @param {number[]} citations
 * @return {number}
 */
var hIndex = function(citations) {
    citations.sort((a, b) => a - b);
    let h = 0, i = citations.length - 1; 
    while (i >= 0 && citations[i] > h) {
        h++; 
        i--;
    }
    return h;
};
```

> 复杂度分析

时间复杂度：O(logn)。

空间复杂度：O(1)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了88.74%的用户

内存消耗：38.3 MB, 在所有 JavaScript 提交中击败了35.07%的用户


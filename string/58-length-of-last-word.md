### 58. 最后一个单词的长度

> 题目

[链接](https://leetcode-cn.com/problems/length-of-last-word/)

> 思路

从后往前循环，先去掉空格。

> 代码

```js
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLastWord = function(s) {
    let end = s.length - 1;
    while(end >= 0 && s[end] == ' ') end--;
    if(end < 0) return 0;
    let start = end;
    while(start >= 0 && s[start] != ' ') start--;
    return end - start;
};
```

> 复杂度分析

时间复杂度：O(n)，n为结尾空格和结尾单词总体长度。

空间复杂度：O(1)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了76.49%的用户

内存消耗：38 MB, 在所有 JavaScript 提交中击败了27.70%的用户
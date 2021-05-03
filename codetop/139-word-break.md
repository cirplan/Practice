### 139. 单词拆分

> 题目

[链接](https://leetcode-cn.com/problems/word-break/)

> 思路

？？

> 代码

```js
/**
 * @param {string} s
 * @param {string[]} wordDict
 * @return {boolean}
 */
var wordBreak = function (s, wordDict) {
  const wordSet = new Set(wordDict);
  const len = s.length;
  const dp = new Array(len + 1).fill(false);
  dp[0] = true;
  for (let i = 1; i <= len; i++) {
    for (let j = i - 1; j >= 0; j--) {
      if (dp[i] == true) break;
      if (dp[j] == false) continue;
      const suffix = s.slice(j, i);
      if (wordSet.has(suffix) && dp[j] == true) {
        dp[i] = true;
        break;
      }
    }
  }
  return dp[s.length];
};
```

> 复杂度分析

时间复杂度：O(N ^ 2)。

空间复杂度：O(N)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了83.87%的用户

内存消耗：39.5 MB, 在所有 JavaScript 提交中击败了77.58%的用户

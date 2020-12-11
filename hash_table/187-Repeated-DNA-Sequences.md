### 187. 重复的DNA序列

> 题目

所有 DNA 都由一系列缩写为 'A'，'C'，'G' 和 'T' 的核苷酸组成，例如："ACGAATTCCG"。在研究 DNA 时，识别 DNA 中的重复序列有时会对研究非常有帮助。

编写一个函数来找出所有目标子串，目标子串的长度为 10，且在 DNA 字符串 s 中出现次数超过一次。

示例 1：
```
输入：s = "AAAAACCCCCAAAAACCCCCCAAAAAGGGTTT"
输出：["AAAAACCCCC","CCCCCAAAAA"]
```

示例 2：
```
输入：s = "AAAAAAAAAAAAA"
输出：["AAAAAAAAAA"]
```

提示：
0 <= s.length <= 105
s[i] 为 'A'、'C'、'G' 或 'T'

> 思路

使用滑动窗口，再用 Map 记录。

> 代码

```js
/**
 * @param {string} s
 * @return {string[]}
 */
var findRepeatedDnaSequences = function (s) {
  let len = s.length;
  const T = 10;
  if (len < T) return [];
  let result = [];
  let temp = {};
  for (let i = 0; i < len - T + 1; i++) {
    const str = s.substr(i, T);
    if (temp[str] && temp[str] === 1) {
      result.push(str);
    }
    temp[str] = (temp[str] || 0) + 1;
  }

  return result;
};
```

> 复杂度分析

时间复杂度：O((N - L) * L)，这里 L = 10。

空间复杂度：O(N)。

> 执行

执行用时：172 ms, 在所有 JavaScript 提交中击败了15.23%的用户

内存消耗：58.4 MB, 在所有 JavaScript 提交中击败了10.75%的用户

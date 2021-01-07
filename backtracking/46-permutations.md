### 46. 全排列

> 题目

给定一个 没有重复 数字的序列，返回其所有可能的全排列。

示例:
```
输入: [1,2,3]
输出:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

> 思路

使用深度优先，回溯法。

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
const permute = (nums) => {
  const res = [];
  const used = {};

  function dfs(path) {
    if (path.length == nums.length) {
      res.push(path.slice());
      return;
    }
    for (const num of nums) {
      if (used[num]) continue;
      path.push(num);
      used[num] = true;
      dfs(path);
      path.pop();
      used[num] = false;
    }
  }

  dfs([]);
  return res;
};
```

> 复杂度分析

时间复杂度：O(n*n!)。

空间复杂度：O(n)。n 为 nums 的length。

> 执行

执行用时：104 ms, 在所有 JavaScript 提交中击败了52.41%的用户

内存消耗：40.6 MB, 在所有 JavaScript 提交中击败了69.57%的用户

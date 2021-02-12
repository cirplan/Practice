### 剑指 Offer 29. 顺时针打印矩阵

> 题目

[链接](https://leetcode-cn.com/problems/shun-shi-zhen-da-yin-ju-zhen-lcof/)

> 思路

直接循环即可，判断好边界。

> 代码

```js
/**
 * @param {number[][]} matrix
 * @return {number[]}
 */
var spiralOrder = function(matrix) {
  if (!matrix.length) return [];
  let M = matrix.length;
  let N = matrix[0].length;

  // 四个边界
  let t = 0;
  let r = N - 1;
  let b = M - 1;
  let l = 0;

  let list = [];
  while (true) {
    for (let i = l; i <= r; i++) {
      list.push(matrix[t][i]);
    }

    if (++t > b) break;

    for (let i = t; i <= b; i++) {
      list.push(matrix[i][r]);
    }

    if (--r < l) break;

    for (let i = r; i >= l; i--) {
      list.push(matrix[b][i]);
    }

    if (--b < t) break;

    for (let i = b; i >= t; i--) {
      list.push(matrix[i][l]);
    }

    if (++l > r) break;
  }

  return list;
};
```

> 复杂度分析

时间复杂度：O(MN)。

空间复杂度：O(MN)。

> 执行

执行用时：104 ms, 在所有 JavaScript 提交中击败了79.04%的用户

内存消耗：41.3 MB, 在所有 JavaScript 提交中击败了41.81%的用户
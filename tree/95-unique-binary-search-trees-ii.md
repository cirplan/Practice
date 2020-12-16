### 95. 不同的二叉搜索树 II

> 题目

给定一个整数 n，生成所有由 1 ... n 为节点所组成的 二叉搜索树 。

示例：

输入：3
输出：
[
  [1,null,3,2],
  [3,2,null,1],
  [3,1,null,null,2],
  [2,1,3],
  [1,null,2,null,3]
]
解释：
以上的输出对应以下 5 种不同结构的二叉搜索树：

   1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3
 

提示：

0 <= n <= 8

> 思路

二叉搜索树，左子树的所有节点小于根节点，右子树的所有节点大于根节点。所有根据start，end定义函数。分别求左右子树的类别，再组合。

> 代码

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {number} n
 * @return {TreeNode[]}
 */
var generateTrees = function (n) {
  if (n === 0) return [];
  return generate(1, n);
};

function generate(start, end) {
  const allTree = [];
  if (start > end) {
    allTree.push(null);
    return allTree;
  }

  for (let i = start; i <= end; i++) {
    const leftTree = generate(start, i - 1);
    const rightTree = generate(i + 1, end);

    for (let left of leftTree) {
      for (let right of rightTree) {
        const cur = new TreeNode(i, left, right);
        allTree.push(cur);
      }
    }
  }

  return allTree;
}
```


> 复杂度分析

时间复杂度： n 个点生成的二叉搜索树数量等价于数学上第 n 个「卡特兰数」，用 Gn表示。生成一棵二叉搜索树需要 O(n) 的时间复杂度，一共有 Gn棵二叉搜索树，也就是 O(nGn)。卡特兰数以 4^n / n^(3/2)增长。所以总的时间复杂度是：O(4^n / n^(1/2))。

空间复杂度：n个点生成的二叉搜索树有 Gn棵，每棵有 n 个节点，因此存储的空间需要 O(nGn) = O(4^n / n^(1/2))。

> 执行

执行用时：100 ms, 在所有 JavaScript 提交中击败了88.39%的用户

内存消耗：44.9 MB, 在所有 JavaScript 提交中击败了11.37%的用户

### 297. 二叉树的序列化与反序列化

> 题目

序列化是将一个数据结构或者对象转换为连续的比特位的操作，进而可以将转换后的数据存储在一个文件或者内存中，同时也可以通过网络传输到另一个计算机环境，采取相反方式重构得到原数据。

请设计一个算法来实现二叉树的序列化与反序列化。这里不限定你的序列 / 反序列化算法执行逻辑，你只需要保证一个二叉树可以被序列化为一个字符串并且将这个字符串反序列化为原始的树结构。

示例: 

你可以将以下二叉树：

    1
   / \
  2   3
     / \
    4   5

序列化为 "[1,2,3,null,null,4,5]"
提示: 这与 LeetCode 目前使用的方式一致，详情请参阅 LeetCode 序列化二叉树的格式。你并非必须采取这种方式，你也可以采用其他的方法解决这个问题。

说明: 不要使用类的成员 / 全局 / 静态变量来存储状态，你的序列化和反序列化算法应该是无状态的。

> 思路

采用迭代即可，关注当前节点。

> 代码

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */

/**
 * Encodes a tree to a single string.
 *
 * @param {TreeNode} root
 * @return {string}
 */
var serialize = function(root) {
    let list = [];

    function serializeTree (root) {
        if (root === null) return list.push(null);
        list.push(root.val);

        if (root.left || root.right) {
            serializeTree(root.left);
            serializeTree(root.right);
        }
    }

    serializeTree(root);
    return list;
};

/**
 * Decodes your encoded data to tree.
 *
 * @param {string} data
 * @return {TreeNode}
 */
var deserialize = function(data) {
    let data = 
};

/**
 * Your functions will be called as such:
 * deserialize(serialize(root));
 */
```

> 复杂度分析

时间复杂度 : O(N)。

空间复杂度 : O(N)。

> 执行

执行用时：184 ms, 在所有 JavaScript 提交中击败了52.53%的用户

内存消耗：48.2 MB, 在所有 JavaScript 提交中击败了86.60%的用户
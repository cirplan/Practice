### 剑指 Offer 26. 树的子结构

> 题目

[链接](https://leetcode-cn.com/problems/shu-de-zi-jie-gou-lcof/)

> 思路

使用递归的方式判断，注意边界条件。

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
 * @param {TreeNode} A
 * @param {TreeNode} B
 * @return {boolean}
 */
var isSubStructure = function (A, B) {
    if (!A || !B) {
        return false;
    }
   let flag = isSubTreeStructure(A, B);
   if (flag) {
       return true;
   }

   return isSubStructure(A.left, B) || isSubStructure(A.right, B);
};

function isSubTreeStructure(A, B) {
    if (A === B) {
        return true;
    }

    if (!A) {
        return false;
    }

    if (!B) {
        return true;
    }

    if (A.val !== B.val) {
        return false;
    }
    return isSubTreeStructure(A.left, B.left) && isSubTreeStructure(A.right, B.right);
}
```

> 复杂度分析

时间复杂度：O(MN)。M，N分别是A，B的节点数。

空间复杂度：O(M)。

> 执行

执行用时：136 ms, 在所有 JavaScript 提交中击败了61.47%的用户

内存消耗：57.9 MB, 在所有 JavaScript 提交中击败了28.22%的用户

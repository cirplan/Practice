### 77. 组合

> 题目

[链接](https://leetcode-cn.com/problems/combinations/)

> 思路

回溯

> 代码

```js
/**
 * @param {number} n
 * @param {number} k
 * @return {number[][]}
 */
var combine = function (n, k) {
    const res = [];

    const helper = (start, path) => { // start是枚举选择的起点 path是当前构建的路径（组合）
        if (path.length == k) {
            res.push(path.slice());       // 拷贝一份path，推入res
            return;                       // 结束当前递归
        }
        for (let i = start; i <= n; i++) { // 枚举出所有选择
            path.push(i);                    // 选择
            helper(i + 1, path);             // 向下继续选择
            path.pop();                      // 撤销选择
        }
    };

    helper(1, []); // 递归的入口，从数字1开始选
    return res;
};
```

> 复杂度分析

时间复杂度：O(n * 2 ^ n)。

空间复杂度：O(n)。

> 执行

执行用时：184 ms, 在所有 JavaScript 提交中击败了20.80%的用户

内存消耗：42.9 MB, 在所有 JavaScript 提交中击败了74.56%的用户
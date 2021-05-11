### 78. 子集

> 题目

[链接](https://leetcode-cn.com/problems/subsets/)

> 思路

回溯

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var subsets = function (nums) {
    const res = [];

    const dfs = (index, list) => {
        if (index == nums.length) { // 指针越界
            res.push(list.slice());   // 加入解集
            return;                   // 结束当前的递归
        }
        list.push(nums[index]); // 选择这个数
        dfs(index + 1, list);   // 基于该选择，继续往下递归，考察下一个数
        list.pop();             // 上面的递归结束，撤销该选择
        dfs(index + 1, list);   // 不选这个数，继续往下递归，考察下一个数
    };

    dfs(0, []);
    return res;
};
```

> 复杂度分析

时间复杂度：O(n * 2 ^ n)。

空间复杂度：O(n)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了95.08%的用户

内存消耗：39.4 MB, 在所有 JavaScript 提交中击败了97.57%的用户

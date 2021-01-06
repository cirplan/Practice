### 40. 组合总和 II

> 题目

给定一个数组 candidates 和一个目标数 target ，找出 candidates 中所有可以使数字和为 target 的组合。

candidates 中的每个数字在每个组合中只能使用一次。

说明：

所有数字（包括目标数）都是正整数。
解集不能包含重复的组合。 

示例 1:
```
输入: candidates = [10,1,2,7,6,1,5], target = 8,
所求解集为:
[
  [1, 7],
  [1, 2, 5],
  [2, 6],
  [1, 1, 6]
]
```

示例 2:
```
输入: candidates = [2,5,2,1,2], target = 5,
所求解集为:
[
  [1,2,2],
  [5]
]
```

> 思路

递归加回溯

> 代码

```js
/**
 * @param {number[]} candidates
 * @param {number} target
 * @return {number[][]}
 */
const combinationSum2 = (candidates, target) => {
    candidates.sort((a, b) => a - b);
    const res = [];

    const dfs = (start, temp, sum) => {
        if (sum >= target) {
            if (sum == target) {
                res.push(temp.slice());
            }
            return;
        }
        for (let i = start; i < candidates.length; i++) {
            if (i - 1 >= start && candidates[i - 1] == candidates[i]) {
                continue;
            }
            temp.push(candidates[i]);
            dfs(i + 1, temp, sum + candidates[i]);
            temp.pop();
        }
    };

    dfs(0, [], 0);
    return res;
};

```

> 复杂度分析

时间复杂度：O(S)，其中 S 为所有可行解的长度之和。。

空间复杂度：O(target)。

> 执行

执行用时：104 ms, 在所有 JavaScript 提交中击败了45.35%的用户

内存消耗：39.2 MB, 在所有 JavaScript 提交中击败了93.22%的用户
### 47. 全排列 II

> 题目

给定一个可包含重复数字的序列 nums ，按任意顺序 返回所有不重复的全排列。

示例 1：
```
输入：nums = [1,1,2]
输出：
[[1,1,2],
 [1,2,1],
 [2,1,1]]
```

示例 2：
```
输入：nums = [1,2,3]
输出：[[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

提示：

1 <= nums.length <= 8
-10 <= nums[i] <= 10


> 思路

迭代回溯，注意重复数字判断。

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
const permuteUnique = (nums) => {
    const res = [];
    const len = nums.length;
    const used = new Array(len);
    nums.sort((a, b) => a - b);

    const helper = (path) => {
        if (path.length == len) {
            res.push(path.slice());
            return;
        }

        for (let i = 0; i < len; i++) {
            if (nums[i - 1] == nums[i] && i - 1 >= 0 && !used[i - 1]) {
                continue;
            }
            if (used[i]) {
                continue;
            }
            path.push(nums[i]);
            used[i] = true;
            helper(path);
            path.pop();
            used[i] = false;
        }
    };

    helper([]);
    return res;
};
```

> 复杂度分析


时间复杂度：O(n*n!)。

空间复杂度：O(n)。

> 执行

执行用时：108 ms, 在所有 JavaScript 提交中击败了66.07%的用户

内存消耗：41 MB, 在所有 JavaScript 提交中击败了55.79%的用户

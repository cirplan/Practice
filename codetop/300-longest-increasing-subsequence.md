### 300. 最长递增子序列

> 题目

[链接](https://leetcode-cn.com/problems/longest-increasing-subsequence/)

> 思路

??

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var lengthOfLIS = function (nums) {
    let len = 1, n = nums.length
    if (n === 0) return 0
    let d = []
    d[len] = nums[0]
    for (let i = 1; i < n; ++i) {
        if (nums[i] > d[len]) {
            d[++len] = nums[i];
        } else {
            let l = 1, r = len, pos = 0; // 如果找不到说明所有的数都比 nums[i] 大，此时要更新 d[1]，所以这里将 pos 设为 0
            while (l <= r) {
                let mid = (l + r) >> 1;
                if (d[mid] < nums[i]) {
                    pos = mid;
                    l = mid + 1;
                } else {
                    r = mid - 1;
                }
            }
            d[pos + 1] = nums[i];
        }
    }
    return len;
};
```

> 复杂度分析

时间复杂度：O(nlogn)。

空间复杂度：O(n)。

> 执行

执行用时：96 ms, 在所有 JavaScript 提交中击败了88.46%的用户

内存消耗：39.3 MB, 在所有 JavaScript 提交中击败了79.76%的用户
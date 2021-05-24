### 494. 目标和

> 题目

[链接](https://leetcode-cn.com/problems/target-sum/)

> 思路

？？

> 代码

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var findTargetSumWays = function (nums, S) {
    let len = nums.length;
    let arr = []
    arr[0] = {}
    if (nums[0] == 0) {
        arr[0][0] = 2;
    } else {
        let sum = nums[0];
        let subt = -nums[0]
        arr[0][sum] = 1;
        arr[0][subt] = 1;
    }
    for (let i = 1; i < len; i++) {
        arr[i] = {};
        for (let key in arr[i - 1]) {
            let sum = parseInt(key) + nums[i];
            let subt = parseInt(key) - nums[i];
            let last = arr[i - 1][key];
            if (arr[i][sum] == undefined) {
                arr[i][sum] = last;
            } else {
                arr[i][sum] += last
            }
            if (arr[i][subt] == undefined) {
                arr[i][subt] = last;
            } else {
                arr[i][subt] += last;
            }
        }
    }
    return arr[len - 1][S] ? arr[len - 1][S] : 0;
};
```


> 复杂度分析

时间复杂度：O(N ^ 2)。

空间复杂度：O(N)。

> 执行

执行用时：352 ms, 在所有 JavaScript 提交中击败了54.70%的用户

内存消耗：46.3 MB, 在所有 JavaScript 提交中击败了8.46%的用户

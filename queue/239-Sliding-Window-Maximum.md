### 239. 滑动窗口最大值

> 题目

给定一个数组 nums，有一个大小为 k 的滑动窗口从数组的最左侧移动到数组的最右侧。你只可以看到在滑动窗口内的 k 个数字。滑动窗口每次只向右移动一位。

返回滑动窗口中的最大值。

进阶：

你能在线性时间复杂度内解决此题吗？

示例:
```
输入: nums = [1,3,-1,-3,5,3,6,7], 和 k = 3
输出: [3,3,5,5,6,7] 
解释: 

  滑动窗口的位置                最大值
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7
 ```

提示：

1 <= nums.length <= 10^5
-10^4 <= nums[i] <= 10^4
1 <= k <= nums.length

> 思路

最直接的思路是，对每个窗口的数据分别比较，取最大值。但这样下来，耗费的时间是 N ^ k。
题目要求用线性的时间。我们使用双向队列的方式，注意：这里双向队列仅保存下标。

* 对前K个数，执行如下步骤
* 设置 maxIndex = 0；然后对队列里的数据进行过滤，一是要过滤超出范围的，二是过滤值比当前值要小的
* 然后把当前值下标添加到队列里
* 再判断当前值是否大于最大值，是则更新 maxIndex
* 循环结束，把 nums[maxIndex] 推到结果列表
* 从 k 开始循环到 n 结束，先执行数据过滤，再把数据添加到队列，然后把队首值添加到结果列表

> 代码

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number[]}
 */
var maxSlidingWindow = function (nums, k) {
    if (k === 1) return nums;

    let queue = [];
    let maxIdx = 0;
    for (let i = 0; i < k; i++) {
        cleanQueue(i, k);
        queue.push(i);
        if (nums[i] > nums[maxIdx]) {
            maxIdx = i;
        }
    }

    let result = [];
    result.push(nums[maxIdx]);

    for (let i = k; i < nums.length; i++) {
        cleanQueue(i, k);
        queue.push(i);
        result.push(nums[queue[0]]);
    }

    return result;

    function cleanQueue(i, k) {
        if (queue[0] === i - k) {
            queue.shift();
        }
        while (queue.length && nums[i] > nums[queue[queue.length - 1]]) {
            queue.pop();
        }
    }
};
```

> 复杂度分析

时间复杂度：O(N)，每个元素被处理两次：其索引被添加到双向队列中和被双向队列删除。

空间复杂度：O(N)，输出数组使用了 O(N−k+1) 空间，双向队列使用了 O(k)。

> 执行

执行用时：336 ms, 在所有 JavaScript 提交中击败了50.17%的用户

内存消耗：68.5 MB, 在所有 JavaScript 提交中击败了10.05%的用户

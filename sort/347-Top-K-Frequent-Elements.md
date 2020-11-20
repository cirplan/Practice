### 347. 前 K 个高频元素

> 题目

给定一个非空的整数数组，返回其中出现频率前 k 高的元素。

示例 1:
```
输入: nums = [1,1,1,2,2,3], k = 2
输出: [1,2]
```

示例 2:
```
输入: nums = [1], k = 1
输出: [1]
```

提示：

你可以假设给定的 k 总是合理的，且 1 ≤ k ≤ 数组中不相同的元素的个数。
你的算法的时间复杂度必须优于 O(n log n) , n 是数组的大小。
题目数据保证答案唯一，换句话说，数组中前 k 个高频元素的集合是唯一的。
你可以按任意顺序返回答案。

> 思路

先遍历数组，得出每个数字出现的次数。再对次数进行桶排序。

> 代码

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number[]}
 */
var topKFrequent = function (nums, k) {
    let map = new Map();
    nums.forEach(num => {
        map.has(num) ? map.set(num, map.get(num) + 1) : map.set(num, 1);
    });

    if (map.size < k) {
        return [...map.keys()];
    }

    let bucket = [];
    let result = [];
    map.forEach((value, key) => {
        bucket[value] ? bucket[value].push(key) : bucket[value] = [key];
    });
    for (let i = bucket.length - 1; i >= 0 && result.length < k; i--) {
        if (bucket[i]) {
            result.push(...bucket[i]);
        }
    }

    return result;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：104 ms, 在所有 JavaScript 提交中击败了53.79%的用户

内存消耗：40.8 MB, 在所有 JavaScript 提交中击败了29.63%的用户

### 169. 多数元素

> 题目

给定一个大小为 n 的数组，找到其中的多数元素。多数元素是指在数组中出现次数 大于 ⌊ n/2 ⌋ 的元素。

你可以假设数组是非空的，并且给定的数组总是存在多数元素。
 
示例 1：
```
输入：[3,2,3]
输出：3
```

示例 2：
```
输入：[2,2,1,1,1,2,2]
输出：2
```

进阶：
尝试设计时间复杂度为 O(n)、空间复杂度为 O(1) 的算法解决此问题。

> 思路

可以用哈希表记录元素的次数。也可以先排序，再取 n / 2 位置的元素。最巧妙的是用投票法，与前一个数相同 + 1，不同则 - 1，最后留下来的就是众数。

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function (nums) {
    let count = 0;
    let candidate = null;

    for (let num of nums) {
        if (count == 0) {
            candidate = num;
        }
        count += (num == candidate) ? 1 : -1;
    }

    return candidate;
};
```

> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(1)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了77.42%的用户

内存消耗：41.3 MB, 在所有 JavaScript 提交中击败了49.82%的用户
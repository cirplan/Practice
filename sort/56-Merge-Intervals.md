### 56. Merge Intervals

> 题目

给出一个区间的集合，请合并所有重叠的区间。

示例 1:

输入: [[1,3],[2,6],[8,10],[15,18]]
输出: [[1,6],[8,10],[15,18]]

解释: 区间 [1,3] 和 [2,6] 重叠, 将它们合并为 [1,6]

示例 2:

输入: [[1,4],[4,5]]
输出: [[1,5]]

解释: 区间 [1,4] 和 [4,5] 可被视为重叠区间。


> 思路

先对数组排序，则可以合并的数组必然是相邻项，所以判断相邻的项即可。这里采用双指针的方式，i指向当前项，j指向下一项，当i项和j项重叠，合并两项，j++。再用合并后的项和j++项重复上面判断，直到最后。

> 代码

```js
/**
 * @param {number[][]} intervals
 * @return {number[][]}
 */
var merge = function (intervals) {
  if (intervals.length <= 1) return intervals;
​
  intervals.sort((a, b) => a[0] - b[0]);
  const len = intervals.length;
  let i = 0;
  let result = [];
  while (i < len) {
    const begin = intervals[i][0];
    const end = intervals[i][1];
​
    let j = i + 1;
    while (j < len && end >= intervals[j][0]) {
      end = Math.max(end, intervals[j][1]);
      j++;
    }
​
    i = j;
    result.push([begin, end]);
  }
​
  return result;
};
```

> 复杂度分析

时间复杂度：O(nlogn)。排序的时间复杂度O(nlogn)，再循环一次O(n)，所以为O(nlogn + n) = O(nlogn)。

空间复杂度：O(N)。

> 执行

用时：104 ms, 在所有 JavaScript 提交中击败了28.64%的用户

内存消耗：40.3 MB, 在所有 JavaScript 提交中击败了22.22%的用户
### 57. Insert Interval

> 题目

给出一个无重叠的 ，按照区间起始端点排序的区间列表。

在列表中插入一个新的区间，你需要确保列表中的区间仍然有序且不重叠（如果有必要的话，可以合并区间）。

示例 1:
```
输入: intervals = [[1,3],[6,9]], newInterval = [2,5]
输出: [[1,5],[6,9]]
```

示例 2:
```
输入: intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], newInterval = [4,8]
输出: [[1,2],[3,10],[12,16]]
解释: 这是因为新的区间 [4,8] 与 [3,5],[6,7],[8,10] 重叠。
```

> 思路

这道题和56题很类似，主要是合并区间。这里要注意的关键词是`无重叠`，`按起始端点排序`。

可以先看些例子。

1. 起点无交集
```
输入: intervals = [[2,3],[6,9]], newInterval = [0,1]
输出: [[0,1], [2,3], [6,9]]
```

2. 有交集
```
输入: intervals = [[2,3],[6,9]], newInterval = [1,2]
输出: [[1,3], [6,9]]
```

2. 终点无交集
```
输入: intervals = [[2,3],[6,9]], newInterval = [10,11]
输出: [[2,3], [6,9], [10, 11]]
```

所以我们可以直接对数组进行循环，先判断是否有交集，否则再判断待合并项是否在当前项间前，最后终点再判断是否已添加到数组里。

> 代码

```js
/**
 * @param {number[][]} intervals
 * @param {number[]} newInterval
 * @return {number[][]}
 */
var insert = function (intervals, newInterval) {
  if (!intervals.length) return [newInterval];
  const len = intervals.length;
  let result = [];
  // 标记是否已添加到数组
  let flag = false;

  for (let i = 0; i < len; i++) {
    let item = intervals[i];
    const s1 = item[0];
    const e1 = item[1];
    const s2 = newInterval[0];
    const e2 = newInterval[1];

    if (hasMixed(item, newInterval)) {
      let _s = Math.min(s1, s2);
      let _e = Math.max(e1, e2);
      // 已添加到数组，直接对当前项进行操作
      if (flag) {
        newInterval[0] = _s;
        newInterval[1] = _e;
      } else {
        newInterval = [_s, _e];
        result.push(newInterval);
      }

      !flag && (flag = true);
      continue;
    }

    // 待合并项比当前项范围更小
    if (!flag && (e2 < s1)) {
      flag = true;
      result.push(newInterval);
    }
    
    result.push(item);
  }

  // 判断是否已添加合并项
  if (!flag) {
    result.push(newInterval);
  }

  return result;
};

// 判断是否有交集
function hasMixed(n1, n2) {
  const s1 = n1[0];
  const e1 = n1[1];
  const s2 = n2[0];
  const e2 = n2[1];

  return (
    (s1 >= s2 && s1 <= e2) ||
    (s2 >= s1 && s2 <= e1)
  );
}
```

> 复杂度分析

循环了一次，时间复杂度为O(N)。

使用了数组存储结果，空间复杂度为O(N)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了62.16%的用户。

内存消耗：40.7 MB, 在所有 JavaScript 提交中击败了100.00%的用户。
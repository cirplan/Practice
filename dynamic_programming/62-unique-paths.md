### 62. 不同路径

> 题目

一个机器人位于一个 m x n 网格的左上角 （起始点在下图中标记为 “Start” ）。

机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为 “Finish” ）。

问总共有多少条不同的路径？

示例 1：
```
输入：m = 3, n = 7
输出：28
```

示例 2：
```
输入：m = 3, n = 2
输出：3
解释：
从左上角开始，总共有 3 条路径可以到达右下角。
1. 向右 -> 向右 -> 向下
2. 向右 -> 向下 -> 向右
3. 向下 -> 向右 -> 向右
```

示例 3：
```
输入：m = 7, n = 3
输出：28
```

示例 4：
```
输入：m = 3, n = 3
输出：6
```

提示：

1 <= m, n <= 100
题目数据保证答案小于等于 2 * 109


> 思路

使用迭代大法。

> 代码

```js
/**
 * @param {number} m
 * @param {number} n
 * @return {number}
 */
let cache = new Map();
var uniquePaths = function (m, n) {
    if (n === 1) return 1;
    else if (m === 1) return 1;

    const mKey = `${m - 1}-${n}`;
    const nKey = `${m}-${n - 1}`;

    let m1;
    let n1;
    if (cache.has(mKey)) {
        m1 = cache.get(mKey);
    } else {
        m1 = uniquePaths(m - 1, n);
        cache.set(mKey, m1);
    }

    if (cache.has(nKey)) {
        n1 = cache.get(nKey);
    } else {
        n1 = uniquePaths(m, n - 1);
        cache.set(nKey, n1);
    }

    return m1 + n1;
};
```

> 复杂度分析

时间复杂度：O(mn)。

空间复杂度：O(mn)。

> 执行

执行用时：76 ms, 在所有 JavaScript 提交中击败了90.32%的用户

内存消耗：38.1 MB, 在所有 JavaScript 提交中击败了29.88%的用户
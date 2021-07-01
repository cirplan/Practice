### LCP 07. 传递信息

> 题目

[链接](https://leetcode-cn.com/problems/chuan-di-xin-xi/)

> 思路

深度优先

> 代码

```js
/**
 * @param {number} n
 * @param {number[][]} relation
 * @param {number} k
 * @return {number}
 */
var numWays = function (n, relation, k) {
    let ways = 0;
    const edges = new Array(n).fill(0).map(() => new Array());

    for (const [src, dst] of relation) {
        edges[src].push(dst);
    }

    const dfs = (index, steps) => {
        if (steps === k) {
            if (index === n - 1) {
                ways++;
            }
            return;
        }
        const list = edges[index];
        for (const nextIndex of list) {
            dfs(nextIndex, steps + 1);
        }
    }

    dfs(0, 0);
    return ways;
};
```

> 复杂度分析

时间复杂度：O(n^k)。最多需要遍历 k 层，每层遍历最多有 O(n) 个分支。

空间复杂度：O(n+m+k)。其中 m 为 relation 数组的长度。空间复杂度主要取决于图的大小和递归调用栈的深度，保存有向图信息所需空间为 O(n+m)，递归调用栈的深度不会超过 k。

> 执行

？？
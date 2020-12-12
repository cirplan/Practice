### 332. 重新安排行程

> 题目

给定一个机票的字符串二维数组 [from, to]，子数组中的两个成员分别表示飞机出发和降落的机场地点，对该行程进行重新规划排序。所有这些机票都属于一个从 JFK（肯尼迪国际机场）出发的先生，所以该行程必须从 JFK 开始。

提示：

如果存在多种有效的行程，请你按字符自然排序返回最小的行程组合。例如，行程 ["JFK", "LGA"] 与 ["JFK", "LGB"] 相比就更小，排序更靠前
所有的机场都用三个大写字母表示（机场代码）。
假定所有机票至少存在一种合理的行程。
所有的机票必须都用一次 且 只能用一次。

示例 1：
```
输入：[["MUC", "LHR"], ["JFK", "MUC"], ["SFO", "SJC"], ["LHR", "SFO"]]
输出：["JFK", "MUC", "LHR", "SFO", "SJC"]
```

示例 2：
```
输入：[["JFK","SFO"],["JFK","ATL"],["SFO","ATL"],["ATL","JFK"],["ATL","SFO"]]
输出：["JFK","ATL","JFK","SFO","ATL","SFO"]
解释：另一种有效的行程是 ["JFK","SFO","ATL","JFK","ATL","SFO"]。但是它自然排序更大更靠后。
```

> 思路

欧拉路径。先建表，使用深度优先算法，找到第一个没有后面节点的点，把它插入到结果中，再逐步回溯。

> 代码

```js
/**
 * @param {string[][]} tickets
 * @return {string[]}
 */
const findItinerary = (tickets) => {
  const res = [];
  const map = {};
  
  for (const ticket of tickets) {
    const [from, to] = ticket;
    if (!map[from]) {
      map[from] = [];
    }
    map[from].push(to);
  }
  for (const city in map) {
    map[city].sort();
  }

  const dfs = (node) => {
    const nextNodes = map[node]; 
    while (nextNodes && nextNodes.length) { 
      const next = nextNodes.shift(); 
      dfs(next);                      
    }                 

    res.unshift(node); 
  };

  dfs('JFK'); 
  return res;
};

```

> 复杂度分析

时间复杂度：O(mlogm)，其中 m 是边的数量。对于每一条边我们需要 O(logm) 地删除它，最终的答案序列长度为 m+1，而与 n 无关。

空间复杂度：O(m)，其中 m 是边的数量。我们需要存储每一条边。

> 执行

执行用时：104 ms, 在所有 JavaScript 提交中击败了79.37%的用户

内存消耗：41.7 MB, 在所有 JavaScript 提交中击败了70.49%的用户
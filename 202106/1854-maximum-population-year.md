### 1854. 人口最多的年份

> 题目

[链接](https://leetcode-cn.com/problems/maximum-population-year/)

> 思路

??

> 代码

```js
/**
 * @param {number[][]} logs
 * @return {number}
 */
var maximumPopulation = function (logs) {
    var count = 0
    var max = [0, 0] 
    logs = logs.sort((a, b) => a[0] - b[0]) 

    var waitForDead = []
    for (let it of logs) {
        const birth = it[0]
        count += 1
        const originDead = waitForDead.length
        waitForDead = waitForDead.filter(it => it > birth)
        count -= originDead - waitForDead.length
        if (count > max[0]) max = [count, birth]
        waitForDead.push(it[1])
    }
    return max[1]
};
```

> 复杂度分析

时间复杂度：O(nlogn)。

空间复杂度：O(n)。

> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了56.09%的用户

内存消耗：39.4 MB, 在所有 JavaScript 提交中击败了48.34%的用户

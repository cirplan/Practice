### 121. 买卖股票的最佳时机

> 题目

给定一个数组，它的第 i 个元素是一支给定股票第 i 天的价格。

如果你最多只允许完成一笔交易（即买入和卖出一支股票一次），设计一个算法来计算你所能获取的最大利润。

注意：你不能在买入股票前卖出股票。

示例 1:
```
输入: [7,1,5,3,6,4]
输出: 5
解释: 在第 2 天（股票价格 = 1）的时候买入，在第 5 天（股票价格 = 6）的时候卖出，最大利润 = 6-1 = 5 。
     注意利润不能是 7-1 = 6, 因为卖出价格需要大于买入价格；同时，你不能在买入前卖出股票。
```

示例 2:
```
输入: [7,6,4,3,1]
输出: 0
解释: 在这种情况下, 没有交易完成, 所以最大利润为 0。
```

> 思路

最简单的两层循环，暴力破解。但可以用动态规划，f(i) 代表第i次的最大利润，所以求 max(f(i)) 即可。但 f(i) 还和 f(i - 1)有关，f(i-1) = p[i-1] - minValue， 其中 minValue 表示以 i-1 结尾的前排数组的最小值，故 minValue = p[i-1] - f(i-1)。

> 代码

```js
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function (prices) {
    if (!prices.length) return 0;

    let maxVal = 0;
    let prevMin = 0, current = 0;
    for (let i = 1; i < prices.length; i++) {
        current = Math.max(prevMin + prices[i] - prices[i - 1], 0);
        maxVal = Math.max(current, maxVal);
        prevMin = current;
    }
    return maxVal;
};
```

> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(1)。

> 执行

执行用时：108 ms, 在所有 JavaScript 提交中击败了33.20%的用户

内存消耗：47.5 MB, 在所有 JavaScript 提交中击败了5.02%的用户

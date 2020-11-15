### 862. 和至少为 K 的最短子数组

> 题目

返回 A 的最短的非空连续子数组的长度，该子数组的和至少为 K 。

如果没有和至少为 K 的非空子数组，返回 -1 。

示例 1：
```
输入：A = [1], K = 1
输出：1
```

示例 2：
```
输入：A = [1,2], K = 4
输出：-1
```

示例 3：
```
输入：A = [2,-1,2], K = 3
输出：3
```

提示：

1 <= A.length <= 50000
-10 ^ 5 <= A[i] <= 10 ^ 5
1 <= K <= 10 ^ 9

> 思路

暴力计算，超出时间限制。这里要先统计前缀和，再维持一个前缀和的下标队列。这个队列遵循如下规则：

* 对于新加入的y，P[y] 要比前面的值大，否则要 pop 掉。因为要P[y] - P[x] >= K。
* 当 P[y] - P[x] >= K，要把X pop掉。

> 代码

```js
/**
 * @param {number[]} A
 * @param {number} K
 * @return {number}
 */
var shortestSubarray = function (A, K) {
    const len = A.length;
    let P = [0];

    for (let i = 0; i < len; i++) {
        P[i + 1] = P[i] + A[i];
    }
    let ans = len + 1;
    let monoq = [];

    for (let y = 0; y < P.length; y++) {
        while (monoq.length && P[y] <= P[monoq[monoq.length - 1]]) {
            monoq.pop();
        }
        while (monoq.length && P[y] >= P[monoq[0]] + K) {
            ans = Math.min(ans, y - monoq.shift());
        }

        monoq.push(y);
    }

    return ans < len + 1 ? ans : -1;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：312 ms, 在所有 JavaScript 提交中击败了57.58%的用户。

内存消耗：49.3 MB, 在所有 JavaScript 提交中击败了6.25%的用户。

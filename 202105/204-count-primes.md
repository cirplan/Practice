### 204. 计数质数

> 题目

[链接](https://leetcode-cn.com/problems/count-primes/)

> 思路

埃氏筛

> 代码

```js
/**
 * @param {number} n
 * @return {number}
 */
var countPrimes = function (n) {
    const isPrime = new Array(n).fill(1);
    let ans = 0;
    for (let i = 2; i < n; ++i) {
        if (isPrime[i]) {
            ans += 1;
            for (let j = i * i; j < n; j += i) {
                isPrime[j] = 0;
            }
        }
    }
    return ans;
};
```


> 复杂度分析

时间复杂度：O(nloglogn)。

空间复杂度：O(n)。

> 执行

执行用时：252 ms, 在所有 JavaScript 提交中击败了52.61%的用户

内存消耗：77.3 MB, 在所有 JavaScript 提交中击败了28.16%的用户
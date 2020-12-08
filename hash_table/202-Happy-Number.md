### 202. 快乐数

> 题目

编写一个算法来判断一个数 n 是不是快乐数。

「快乐数」定义为：对于一个正整数，每一次将该数替换为它每个位置上的数字的平方和，然后重复这个过程直到这个数变为 1，也可能是 无限循环 但始终变不到 1。如果 可以变为  1，那么这个数就是快乐数。

如果 n 是快乐数就返回 True ；不是，则返回 False 。

示例：
```
输入：19
输出：true
解释：
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```

> 思路

这里最关键的点是判断是否会出现循环，我们可以借助map来记录每次计算的结果，当新的结果已经存在map里的时候，就是出现循环了。

> 代码

```js
/**
 * @param {number} n
 * @return {boolean}
 */
var isHappy = function (n) {
  let tempMap = {};
  tempMap[n] = 1;

  while (n !== 1) {
    const nStr = String(n);
    let total = 0;
    let i = 0;
    while (i < nStr.length) {
      total += Math.pow(nStr.charAt(i), 2);
      i++;
    }
    if (tempMap[total]) {
      return false;
    } else {
      tempMap[total] = 1;
      n = total;
    }
  }

  return true;
};
```

解法二：使用快慢指针

```js
/**
 * @param {number} n
 * @return {boolean}
 */
var isHappy = function (n) {
    let slow = n;
    let fast = n;
    do {
        slow = bitSquareSum(slow);
        fast = bitSquareSum(fast);
        fast = bitSquareSum(fast);
    } while (slow != fast && fast !== 1);

    return slow === 1 || fast === 1;
};


function bitSquareSum(n) {
    let sum = 0;
    while (n > 0) {
        let bit = n % 10;
        sum += bit * bit;
        n = parseInt(n / 10);
    }
    return sum;
}
```

> 复杂度分析

时间复杂度：当计算一个数的下一个值，要循环数的长度K次，时间复杂度为O(logn)。则整个的时间为O(logn)+O(loglogn)+O(logloglogn)... = O(logn)。

空间复杂度：O(logn)。

> 执行

执行用时：96 ms, 在所有 JavaScript 提交中击败了19.82%的用户。

内存消耗：39.8 MB, 在所有 JavaScript 提交中击败了37.14%的用户。



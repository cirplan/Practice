### 875. 爱吃香蕉的珂珂

> 题目

珂珂喜欢吃香蕉。这里有 N 堆香蕉，第 i 堆中有 piles[i] 根香蕉。警卫已经离开了，将在 H 小时后回来。

珂珂可以决定她吃香蕉的速度 K （单位：根/小时）。每个小时，她将会选择一堆香蕉，从中吃掉 K 根。如果这堆香蕉少于 K 根，她将吃掉这堆的所有香蕉，然后这一小时内不会再吃更多的香蕉。  

珂珂喜欢慢慢吃，但仍然想在警卫回来前吃掉所有的香蕉。

返回她可以在 H 小时内吃掉所有香蕉的最小速度 K（K 为整数）。

示例 1：
```
输入: piles = [3,6,7,11], H = 8
输出: 4
```

示例 2：
```
输入: piles = [30,11,23,4,20], H = 5
输出: 30
```

示例 3：
```
输入: piles = [30,11,23,4,20], H = 6
输出: 23
```

提示：

* 1 <= piles.length <= 10^4
* piles.length <= H <= 10^9
* 1 <= piles[i] <= 10^9

> 思路

```
piles = [3,6,7,11]， H = 4，piles.length == H， 则 K 为11（最大值）

piles = [3,6,7,11]， H = 8，piles.length > H，先找出最大值11，则 0 < K < H。找出最小的K，则相当于数组里寻找一个数，直接用二分法即可。
```

> 代码

```js
/**
 * @param {number[]} piles
 * @param {number} H
 * @return {number}
 */
var minEatingSpeed = function (piles, H) {
  const len = piles.length;
  let max = 0;

  for (let i = 0; i < piles.length; i++) {
    const pile = piles[i];
    if (max < pile) {
      max = pile;
    }
  }

  if (H === len) return max;

  let low = 0;
  let height = max;
  let k = max;

  while (low <= height) {
    const _k = Math.floor((low + height) / 2);
    const _h = piles.reduce((total, pile) => {
      return total + Math.ceil(pile / _k);
    }, 0);

    if (_h > H) {
      low = _k + 1;
    } else {
      k = _k;
      height = _k - 1;
    }
  }

  return k;
};
```

> 复杂度分析

先执行了循环，为 O(N)，然后使用了二分法，时间复杂度为 O(N + logN)。

空间复杂度为 O(1)。

> 执行

执行用时：116 ms, 在所有 JavaScript 提交中击败了59.68%的用户。

内存消耗：41.1 MB, 在所有 JavaScript 提交中击败了100.00%的用户。

> 算法

二分法


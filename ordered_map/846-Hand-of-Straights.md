### 846. 一手顺子

> 题目

爱丽丝有一手（hand）由整数数组给定的牌。 

现在她想把牌重新排列成组，使得每个组的大小都是 W，且由 W 张连续的牌组成。

如果她可以完成分组就返回 true，否则返回 false。

示例 1：
```
输入：hand = [1,2,3,6,2,3,4,7,8], W = 3
输出：true
解释：爱丽丝的手牌可以被重新排列为 [1,2,3]，[2,3,4]，[6,7,8]。
```

示例 2：
```
输入：hand = [1,2,3,4,5], W = 4
输出：false
解释：爱丽丝的手牌无法被重新排列成几个大小为 4 的组。
```

提示：
1 <= hand.length <= 10000
0 <= hand[i] <= 10^9
1 <= W <= hand.length

> 思路

先判断牌的数量是否能等分成W，不能直接返回false。然后对hand排序，再从小开始分别取W个按顺序的数，取出的直接从数组里删除，取不到则返回false。

> 代码

```js
/**
 * @param {number[]} hand
 * @param {number} W
 * @return {boolean}
 */
var isNStraightHand = function (hand, W) {
  if (W === 1) return true;

  if (hand.length % W !== 0) return false;

  hand = hand.sort((a, b) => a - b);
  let temp = [];

  let i = 0;
  while (hand.length) {
    const num = hand[i];
    if (!temp.length) {
      temp.push(num);
      hand.splice(i, 1);
    } else {
      const prevNum = temp[temp.length - 1];
      if (num === prevNum) {
        i++;
      } else if (num === prevNum + 1) {
        temp.push(num);
        hand.splice(i, 1);

        if (temp.length === W) {
          i = 0;
          temp = [];
        }
      } else {
        return false;
      }
    }
  }

  return true;
};
```

> 复杂度分析

时间复杂度：排序用O(logN)，然后再对数组循环O(N)，所以为O(logN + N)。

空间复杂度：O(N)。

> 执行

执行用时：160 ms, 在所有 JavaScript 提交中击败了45.24%的用户。

内存消耗：44.2 MB, 在所有 JavaScript 提交中击败了50.00%的用户。



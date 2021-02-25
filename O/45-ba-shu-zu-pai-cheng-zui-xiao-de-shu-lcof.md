### 剑指 Offer 45. 把数组排成最小的数

> 题目

[链接](https://leetcode-cn.com/problems/ba-shu-zu-pai-cheng-zui-xiao-de-shu-lcof/)

> 思路

使用sort，确定好新的排序判断就行。ab < ba，则 a 在前面

> 代码

```js
/**
 * @param {number[]} nums
 * @return {string}
 */
var minNumber = function (nums) {
    nums.sort((a, b) => {
        const _a = a.toString();
        const _b = b.toString();
        const _ab = Number(_a + _b);
        const _ba = Number(_b + _a);
        if (_ab < _ba) {
            return -1;
        } else if (_ab === _ba) {
            return 0;
        } else {
            return 1;
        }
    });
    return nums.join('');
};
```

> 复杂度分析

时间复杂度：O(nlogn)。

空间复杂度：O(1)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了73.50%的用户

内存消耗：39.4 MB, 在所有 JavaScript 提交中击败了76.50%的用户
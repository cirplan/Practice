### 17. 电话号码的字母组合

> 题目

[链接](https://leetcode-cn.com/problems/letter-combinations-of-a-phone-number/)

> 思路

使用递归

> 代码

```js
/**
 * @param {string} digits
 * @return {string[]}
 */

const numMap = {
    2: ['a', 'b', 'c'],
    3: ['d', 'e', 'f'],
    4: ['g', 'h', 'i'],
    5: ['j', 'k', 'l'],
    6: ['m', 'n', 'o'],
    7: ['p', 'q', 'r', 's'],
    8: ['t', 'u', 'v'],
    9: ['w', 'x', 'y', 'z']
};
var letterCombinations = function (digits) {
    if (!digits) return [];

    if (digits.length === 1) {
        return numMap[digits];
    }

    var s = digits.charAt(0);
    const numList = letterCombinations(digits.slice(1));

    let res = [];
    let sNums = numMap[s];

    for (let i = 0; i < sNums.length; i++) {
        for (let j = 0; j < numList.length; j++) {
            res.push(`${sNums[i]}${numList[j]}`);
        }
    }

    return res;
};
```

> 复杂度分析

时间复杂度：O(3 ^ N x 4 ^ M)。N 是3个字母的数组，M 是4个字母的数字

空间复杂度：O(3 ^ N x 4 ^ M)。

> 执行

执行用时：72 ms, 在所有 JavaScript 提交中击败了96.00%的用户

内存消耗：37.7 MB, 在所有 JavaScript 提交中击败了79.66%的用户

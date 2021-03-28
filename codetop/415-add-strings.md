### 415. 字符串相加

> 题目

[链接](https://leetcode-cn.com/problems/add-strings/)

> 思路

模拟加法，取对应位进行相加。注意正常加法是从右到左。

> 代码

```js
/**
 * @param {string} num1
 * @param {string} num2
 * @return {string}
 */
var addStrings = function (num1, num2) {
    let res = [];
    const len1 = num1.length;
    const len2 = num2.length;
  
    let i = len1 - 1;
    let j = len2 - 1;
    let add = 0;
    while (i >= 0 || j >=0 || add > 0) {
        const n1 = Number(i >= 0 ? num1[i] : 0);
        const n2 = Number(j >= 0 ? num2[j] : 0);
        const result = n1 + n2 + add;
        const val = result % 10;
        add = parseInt(result / 10);
        res.push(val);
        i--;
        j--;
    }
    
    return res.reverse().join('');
};
```

> 复杂度分析

时间复杂度：O(max(len1, len2))。

空间复杂度：O(1)。

> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了76.39%的用户

内存消耗：40.5 MB, 在所有 JavaScript 提交中击败了15.27%的用户

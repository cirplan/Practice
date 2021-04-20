### 118. 杨辉三角

> 题目

[链接](https://leetcode-cn.com/problems/pascals-triangle/)

> 思路

循环

> 代码

```js
/**
 * @param {number} numRows
 * @return {number[][]}
 */
var generate = function (numRows) {
    let i = 0;
    let result = [];
    while (i < numRows) {
        let array = [1];
        if (i > 0) {
            const prevArray = result[result.length - 1];
            for (let i = 0; i < prevArray.length; i++) {
                array.push(prevArray[i] + (prevArray[i + 1] || 0));
            }
        }
        result.push(array);

        i++;
    }

    return result;
};
```

> 复杂度分析

时间复杂度：O(n ^ 2)。

空间复杂度：O(1)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了72.91%的用户

内存消耗：37.7 MB, 在所有 JavaScript 提交中击败了65.44%的用户

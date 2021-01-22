### 43. 字符串相乘

> 题目

给定两个以字符串形式表示的非负整数 num1 和 num2，返回 num1 和 num2 的乘积，它们的乘积也表示为字符串形式。

示例 1:
```
输入: num1 = "2", num2 = "3"
输出: "6"
```

示例 2:
```
输入: num1 = "123", num2 = "456"
输出: "56088"
```

说明：

num1 和 num2 的长度小于110。
num1 和 num2 只包含数字 0-9。
num1 和 num2 均不以零开头，除非是数字 0 本身。
不能使用任何标准库的大数类型（比如 BigInteger）或直接将输入转换为整数来处理。

> 思路

从右往左，先乘再加。

> 代码

```js
/**
 * @param {string} num1
 * @param {string} num2
 * @return {string}
 */
var multiply = function (num1, num2) {
    if (num1 === '0' || num2 === '0') {
        return "0";
    }
    let m = num1.length;
    let n = num2.length;
    let ansArr = new Array(m + n).fill(0);
    
    for (let i = m - 1; i >= 0; i--) {
        let x = num1.charAt(i) - '0';
        for (let j = n - 1; j >= 0; j--) {
            let y = num2.charAt(j) - '0';
            ansArr[i + j + 1] += x * y;
        }
    }
    
    for (let i = m + n - 1; i > 0; i--) {
        ansArr[i - 1] += parseInt(ansArr[i] / 10);
        ansArr[i] %= 10;
    }
    
    let index = ansArr[0] == 0 ? 1 : 0;
    let ans = new Array();
    while (index < m + n) {
        ans.push(ansArr[index]);
        index++;
    }
    return ans.join('');
};
```

> 复杂度分析

时间复杂度 : O(mn)。

空间复杂度 : O(m + n)。

> 执行

执行用时：100 ms, 在所有 JavaScript 提交中击败了64.55%的用户

内存消耗：39.7 MB, 在所有 JavaScript 提交中击败了74.35%的用户

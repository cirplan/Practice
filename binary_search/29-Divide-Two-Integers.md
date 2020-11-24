### 29. 两数相除

> 题目

给定两个整数，被除数 `dividend` 和除数 `divisor`。将两数相除，要求不使用乘法、除法和 mod 运算符。

返回被除数 `dividend` 除以除数 `divisor` 得到的商。

整数除法的结果应当截去（truncate）其小数部分，例如：truncate(8.345) = 8 以及 truncate(-2.7335) = -2


示例 1:
```
输入: dividend = 10, divisor = 3
输出: 3
解释: 10/3 = truncate(3.33333..) = truncate(3) = 3
```

示例 2:
```
输入: dividend = 7, divisor = -3
输出: -2
解释: 7/-3 = truncate(-2.33333..) = -2
```

提示：

被除数和除数均为 32 位有符号整数。

除数不为 0。

假设我们的环境只能存储 32 位有符号整数，其数值范围是 [−231,  231 − 1]。本题中，如果除法结果溢出，则返回 231 − 1。

> 思路

其实这道题没有想出怎么解，看了答案才知道。这里说下答案提供的思路。

题目要求不能用乘法，除法和 mod 运算符。所以我们可以思考下，计算机里的都是加法，乘法 / 除法 都是怎么实现的。
乘法是通过移位和加法，除法也是通过移位和减法实现。这里的移位是一个非常重要的概念，转换成二进制后，往左移是乘2，往右移是除2。好了，最重要的概念我们已经了解了，接下来就可以尝试着去解了。我们来看个具体的例子。

```
dividend = 15, divisor = 3, result = 0, k = 1
dividend = 15 - 3 = 12, divisor = 3 * 2 = 6, result = 1, k = 1 * 2 = 2
dividend = 12 - 6 = 6, divisor = 6 * 2 = 12, result = 3, k = 2 * 2 = 4
因为 6 < 12 && 6 > 3，所以 divisor = 3，k = 1
dividend = 6 - 3 = 3, divisor = 3 * 2 = 6, result = 4, k = 2
因为 3 < 6 && 3 >= 3，所以 divisor = 3，k = 1
dividend = 3 - 3 = 0, divisor = 3, result = 5, k = 2
```

但是这里还有个巨坑，就是边界问题。

> 代码

```js
/**
 * @param {number} dividend
 * @param {number} divisor
 * @return {number}
 */
var divide = function (dividend, divisor) {
    const maxInt = Math.pow(2, 31);
    // 判断边界
    if (dividend === -maxInt && divisor == -1) return maxInt - 1;

    if (divisor === 1) return dividend;
    else if (divisor === -1) return -dividend;
    // 是否是负数
    let isNegative = (dividend > 0 && divisor < 0) || (dividend < 0 && divisor > 0);

    dividend = Math.abs(dividend);
    divisor = Math.abs(divisor);

    const defaultDivisor = divisor;
    let result = 0;
    let k = 1;
    const maxNum = maxInt - 1;
    // 防溢出判断值
    const partOfMaxNum = maxNum >> 1;

    while (true) {
        if (dividend < defaultDivisor) {
            return isNegative ? -result : result;
        }
        
        if (dividend >= divisor) {
            dividend = dividend - divisor;
            if (divisor >= partOfMaxNum) {
                divisor = maxNum;
            } else {
                divisor = divisor << 1;
            }
            result += k;
            k = k << 1;
        } else {
            divisor = defaultDivisor;
            k = 1;
        }
    }
};
```

> 复杂度分析

时间复杂度 : 二分法，时间复杂度为O(logN)。。

空间复杂度 : O(1)。

> 执行

执行用时：112 ms, 在所有 JavaScript 提交中击败了28.65%的用户。

内存消耗：38.9 MB, 在所有 JavaScript 提交中击败了100.00%的用户。


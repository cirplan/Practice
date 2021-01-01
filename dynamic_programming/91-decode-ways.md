### 91. 解码方法

> 题目

一条包含字母 A-Z 的消息通过以下方式进行了编码：

'A' -> 1
'B' -> 2
...
'Z' -> 26
给定一个只包含数字的非空字符串，请计算解码方法的总数。

题目数据保证答案肯定是一个 32 位的整数。

示例 1：

输入：s = "12"
输出：2
解释：它可以解码为 "AB"（1 2）或者 "L"（12）。
示例 2：

输入：s = "226"
输出：3
解释：它可以解码为 "BZ" (2 26), "VF" (22 6), 或者 "BBF" (2 2 6) 。
示例 3：

输入：s = "0"
输出：0
示例 4：

输入：s = "1"
输出：1
示例 5：

输入：s = "2"
输出：1
 
提示：

1 <= s.length <= 100
s 只包含数字，并且可能包含前导零。

> 思路

使用动态规划，要分情况：

* s[i] == 0，若s[i - 1] = 1 / 2，则dp[i] = dp[i - 2]，否则 return 0
* s[i] == 1，dp[i] = dp[i - 1] + dp[i - 2]
* s[i - 1] = 2，若1 <= s[i] <= 6，则dp[i] = dp[i - 1] + dp[i - 2]

> 代码

```js
/**
 * @param {string} s
 * @return {number}
 */
var numDecodings = function (s) {
    if (s[0] == '0') return 0;
    let pre = 1, curr = 1;
    for (let i = 1; i < s.length; i++) {
        let tmp = curr;
        if (s[i] == '0') {
            if (s[i - 1] == '1' || s[i - 1] == '2') curr = pre;
            else return 0;
        }
        else if (s[i - 1] == '1' || (s[i - 1] == '2' && s[i] >= '1' && s[i] <= '6')) {
        curr = curr + pre;
        }
        pre = tmp;
    }
    return curr;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

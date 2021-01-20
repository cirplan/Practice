### 5. 最长回文子串

> 题目

给你一个字符串 s，找到 s 中最长的回文子串。

示例 1：

输入：s = "babad"
输出："bab"
解释："aba" 同样是符合题意的答案。
示例 2：

输入：s = "cbbd"
输出："bb"
示例 3：

输入：s = "a"
输出："a"
示例 4：

输入：s = "ac"
输出："a"

提示：

1 <= s.length <= 1000
s 仅由数字和英文字母（大写和/或小写）组成

> 思路

？

> 代码

```js
/**
 * @param {string} s
 * @return {string}
 */
var longestPalindrome = function (s) {
    if (s == '') return '';
    const len = s.length;
    let index = 0, maxL = 0, begin = 0;
    while (index < len) {
        let right = index, left = index;
        while (index < len && s[index + 1] == s[index]) {
            index++;
            right++;
        }
        while (right < len && left >= 0 && s[right] == s[left]) {
            right++;
            left--;
        }
        right-- , left++;
        if (right - left + 1 > maxL) {
            maxL = right - left + 1;
            begin = left;
        }
        index++;
    }
    return s.substr(begin, maxL)
};
```

> 复杂度分析

时间复杂度 : O(N ^ 2)。

空间复杂度 : O(1)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了99.61%的用户

内存消耗：39.8 MB, 在所有 JavaScript 提交中击败了92.12%的用户
### 242. 有效的字母异位词

> 题目

给定两个字符串 s 和 t ，编写一个函数来判断 t 是否是 s 的字母异位词。

示例 1:
```
输入: s = "anagram", t = "nagaram"
输出: true
```

示例 2:
```
输入: s = "rat", t = "car"
输出: false
```

说明:
你可以假设字符串只包含小写字母。

进阶:
如果输入字符串包含 unicode 字符怎么办？你能否调整你的解法来应对这种情况？

> 思路

长度不一致，肯定不是。然后先统计s中字符出现的次数，再用t中的字符去判断。

> 代码

```js
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isAnagram = function(s, t) {
    let strMap = {};
    const sLen = s.length;
    const tLen = t.length;
    if (sLen !== tLen) return false;
    for (let i = 0; i < sLen; i++) {
        const str = s.charAt(i);
        strMap[str] = (strMap[str] || 0) + 1;
    }

    for (let i = 0; i < tLen; i++) {
        const str = t.charAt(i);
        if (!strMap[str]) {
            return false;
        } else {
            strMap[str] -= 1;
        }
    }

    return true;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了99.27%的用户

内存消耗：39.2 MB, 在所有 JavaScript 提交中击败了70.20%的用户
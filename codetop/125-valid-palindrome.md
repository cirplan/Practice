### 125. 验证回文串

> 题目

[链接](https://leetcode-cn.com/problems/valid-palindrome/)

> 思路

双指针，从前后分别对比

> 代码

```js
/**
 * @param {string} s
 * @return {boolean}
 */
var isPalindrome = function(s) {
    const len = s.length;
    let i = 0;
    let j = len - 1;
    const reg = /[a-z0-9]/i;

    while (i < j) {
        let iS = s.charAt(i);
        let jS = s.charAt(j);

        if (!reg.test(iS)) {
            i++;
        } else if (!reg.test(jS)) {
            j--;
        } else {
            iS = iS.toLowerCase();
            jS = jS.toLowerCase();
            if (iS !== jS) {
                return false;
            }

            i++;
            j--;
        }
    }

    return true;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：124 ms, 在所有 JavaScript 提交中击败了14.87%的用户

内存消耗：40.3 MB, 在所有 JavaScript 提交中击败了63.40%的用户

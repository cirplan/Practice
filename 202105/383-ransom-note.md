### 383. 赎金信

> 题目

[链接](https://leetcode-cn.com/problems/ransom-note/)

> 思路

使用Map

> 代码

```js
/**
 * @param {string} ransomNote
 * @param {string} magazine
 * @return {boolean}
 */
var canConstruct = function (ransomNote, magazine) {
    let hash = {};
    //记录字符空缺
    for (let i = 0; i < ransomNote.length; i++) {
        let value = ransomNote[i];
        hash[value] ? hash[value]++ : hash[value] = 1;
    }

    //填补空缺
    for (let i = 0; i < magazine.length; i++) {
        let value = magazine[i];
        if (hash[value]) {
            hash[value]--;
        }
    }

    //最后查看哈希表
    for (let key in hash) {
        //如果有空缺没填满，则返回false
        if (hash[key]) {
            return false;
        }
    }

    return true;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了93.85%的用户

内存消耗：40.3 MB, 在所有 JavaScript 提交中击败了90.37%的用户

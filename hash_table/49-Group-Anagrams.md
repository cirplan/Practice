### 49. 字母异位词分组

> 题目

给定一个字符串数组，将字母异位词组合在一起。字母异位词指字母相同，但排列不同的字符串。

示例:
```
输入: ["eat", "tea", "tan", "ate", "nat", "bat"]
输出:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```

说明：

所有输入均为小写字母。
不考虑答案输出的顺序。

> 思路

画重点，所有输入均是小写字母。

* 那第一种思路是对每个字符串进行排序，再用排序后的字符串分别对比。
* 另一种思路是，记录每个字符的 Unicode值，计算出现的次数。如：abcc 则记为 [1, 1, 2]，然后对比输出的数组则得知是否一致。

> 代码

```js
/**
 * @param {string[]} strs
 * @return {string[][]}
 */
var groupAnagrams = function (strs) {
    let strMap = {};
    const zCode = 'z'.charCodeAt();

    strs.forEach((str) => {
        let keys = [];
        let i = 0;
        while (i < str.length) {
            const _char = str[i];
            const code = _char.charCodeAt();
            const idx = zCode - code;
            keys[idx] = keys[idx] || 0;
            keys[idx]++;
            i++;
        }
        const _key = keys.join(',');
        if (strMap[_key]) {
            strMap[_key].push(str);
        } else {
            strMap[_key] = [str];
        }
    });

    return Object.keys(strMap).map(key => strMap[key]);
};
```

> 复杂度分析

时间复杂度：O(NK)，其中 N 是 strs 的长度，而 K 是 strs 中字符串的最大长度。

空间复杂度：O(NK)。

> 执行

执行用时：132 ms, 在所有 JavaScript 提交中击败了89.35%的用户

内存消耗：48.6 MB, 在所有 JavaScript 提交中击败了41.15%的用户

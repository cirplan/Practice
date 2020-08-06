### 30. 串联所有单词的子串

> 题目

给定一个字符串 s 和一些长度相同的单词 words。找出 s 中恰好可以由 words 中所有单词串联形成的子串的起始位置。

注意子串要与 words 中的单词完全匹配，中间不能有其他字符，但不需要考虑 words 中单词串联的顺序。

示例 1：
```
输入：
  s = "barfoothefoobarman",
  words = ["foo","bar"]
输出：[0,9]
解释：
从索引 0 和 9 开始的子串分别是 "barfoo" 和 "foobar" 。
输出的顺序不重要, [9,0] 也是有效答案。
```

示例 2：
```
输入：
  s = "wordgoodgoodgoodbestword",
  words = ["word","good","best","word"]
输出：[]
```

> 思路

先用map记录每个单词出现的次数，然后用 words 单词的长度作为滑动区间长度，分别截取对应字符去对比。

> 代码

```js
/**
 * @param {string} s
 * @param {string[]} words
 * @return {number[]}
 */
var findSubstring = function (s, words) {
    const len = s.length;
    const wordsLen = words.length;
    if (!len || !wordsLen) return [];

    let result = [];
    const singleWordLen = words[0].length;
    let wordsMap = {};
    words.forEach((word) => {
        let num = wordsMap[word] || 0;
        wordsMap[word] = num + 1;
    });

    let i = 0;
    while (i < len - wordsLen * singleWordLen + 1) {
        const tempWordsMap = {};
        let count = 0;

        while (count < wordsLen) {
            const str = s.substr(i + count * singleWordLen,singleWordLen);
            if (wordsMap[str]) {
                const num = tempWordsMap[str] || 0;
                tempWordsMap[str] = num + 1;
                if (tempWordsMap[str] > wordsMap[str]) {
                    break;
                }
            } else {
                break;
            }
            count++;
        }

        if (count == wordsLen) {
            result.push(i);
        }

        i++;
    }

    return result;
};
```

> 复杂度分析

时间复杂度：O(N^2)。

空间复杂度：O(N)。

> 执行

执行用时：248 ms, 在所有 JavaScript 提交中击败了68.58%的用户。

内存消耗：46.4 MB, 在所有 JavaScript 提交中击败了29.55%的用户。


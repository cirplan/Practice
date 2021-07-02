### 451. 根据字符出现频率排序

> 题目

[链接](https://leetcode-cn.com/problems/sort-characters-by-frequency/)

> 思路

统计字符

> 代码

```js
/**
 * @param {string} s
 * @return {string}
 */
var frequencySort = function (s) {
    let result = []
    let map = new Map()
    s.split('').forEach(val => {
        if (map.has(val)) {
            map.set(val, map.get(val) + 1)
        } else {
            map.set(val, 1)
        }
    })

    let arr = [] // 存桶，下标代表频率
    map.forEach((freq, char) => {
        console.log('freq', freq, char);
        if (arr[freq]) {
            arr[freq].push(char)
        } else {
            arr[freq] = [char]
        }
    })

    // 倒序输出
    for (let i = arr.length - 1; i >= 0; i--) {
        if (arr[i]) {
            arr[i].map(char => {
                result.push(char.repeat(i))
            })
        }
    }
    return result.join('')
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：124 ms, 在所有 JavaScript 提交中击败了37.05%的用户

内存消耗：42.3 MB, 在所有 JavaScript 提交中击败了74.35%的用户
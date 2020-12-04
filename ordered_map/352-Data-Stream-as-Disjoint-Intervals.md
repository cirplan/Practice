### 352. 将数据流变为多个不相交区间

> 题目

给定一个非负整数的数据流输入 a1，a2，…，an，…，将到目前为止看到的数字总结为不相交的区间列表。

例如，假设数据流中的整数为 1，3，7，2，6，…，每次的总结为：
```
[1, 1]
[1, 1], [3, 3]
[1, 1], [3, 3], [7, 7]
[1, 3], [7, 7]
[1, 3], [6, 7]
```

进阶：
如果有很多合并，并且与数据流的大小相比，不相交区间的数量很小，该怎么办?

> 思路

先理解题意，要输出没有交集的区间。根据这个特性，我们可以用数组来记录。

> 代码

```js
/**
 * Initialize your data structure here.
 */
var SummaryRanges = function () {
    this.all = [];
};

/** 
 * @param {number} val
 * @return {void}
 */
SummaryRanges.prototype.addNum = function (val) {
    this.all[val] = val;
};

/**
 * @return {number[][]}
 */
SummaryRanges.prototype.getIntervals = function () {
    const { all } = this;
    let result = [];
    let i = 0;
    while (i < all.length) {
        let start = all[i];
        if (start !== undefined) {
            let end = start;
            while (all[++i]) {
                end = all[i];
            }

            result.push([start, end]);
        } else {
            i++;
        }
    }

    return result;
};

/**
 * Your SummaryRanges object will be instantiated and called as such:
 * var obj = new SummaryRanges()
 * obj.addNum(val)
 * var param_2 = obj.getIntervals()
 */
```

> 复杂度分析

时间复杂度：addNum 为 O(1)，getIntervals 为 O(N)。

空间复杂度：为O(N)。

> 执行

执行用时：188 ms, 在所有 JavaScript 提交中击败了95.00%的用户

内存消耗：48.1 MB, 在所有 JavaScript 提交中击败了85.00%的用户

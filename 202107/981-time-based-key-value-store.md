### 981. 基于时间的键值存储

> 题目

[链接](https://leetcode-cn.com/problems/time-based-key-value-store/)

> 思路

哈希表 + 二分

> 代码

```js
/**
 * Initialize your data structure here.
 */
var TimeMap = function () {
    this.map = new Map();
};

TimeMap.prototype.set = function (key, value, timestamp) {
    if (this.map.has(key)) {
        this.map.get(key).push([value, timestamp]);
    } else {
        this.map.set(key, [[value, timestamp]]);
    }
};

TimeMap.prototype.get = function (key, timestamp) {
    let pairs = this.map.get(key)
    if (pairs) {
        let low = 0, high = pairs.length - 1;
        while (low <= high) {
            let mid = Math.floor((high - low) / 2) + low;
            if (pairs[mid][1] > timestamp) {
                high = mid - 1;
            } else if (pairs[mid][1] < timestamp) {
                low = mid + 1;
            } else {
                return pairs[mid][0];
            }
        }
        if (high >= 0) {
            return pairs[high][0];
        }
        return "";
    }
    return "";
};


/**
 * Your TimeMap object will be instantiated and called as such:
 * var obj = new TimeMap()
 * obj.set(key,value,timestamp)
 * var param_2 = obj.get(key,timestamp)
 */
```

> 复杂度分析

时间复杂度：O(logn)。

空间复杂度：O(n)。

> 执行

执行用时：412 ms, 在所有 JavaScript 提交中击败了87.50%的用户

内存消耗：76.6 MB, 在所有 JavaScript 提交中击败了53.13%的用户
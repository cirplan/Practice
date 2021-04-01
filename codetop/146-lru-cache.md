### 146. LRU 缓存机制

> 题目

[链接](https://leetcode-cn.com/problems/lru-cache/)

> 思路

get 的时候，要提取出来，放在队列头部；set 的时候要判断是否已存在。最后要判断是否超出长度。使用 Map 的数据结构

> 代码

```js
/**
 * @param {number} capacity
 */
var LRUCache = function (capacity) {
    this.capacity = capacity;
    this.map = new Map();
};

/** 
 * @param {number} key
 * @return {number}
 */
LRUCache.prototype.get = function (key) {
    const { map } = this;
    if (!map.has(key)) return -1;
    const val = map.get(key);
    map.delete(key);
    map.set(key, val)
    return val;
};

/** 
 * @param {number} key 
 * @param {number} value
 * @return {void}
 */
LRUCache.prototype.put = function (key, value) {
    const { map, capacity } = this;
    if (map.has(key)) {
        map.delete(key);
    }
    map.set(key, value);
    if (map.size > capacity) {
        map.delete(map.keys().next().value)
    }
};

/**
 * Your LRUCache object will be instantiated and called as such:
 * var obj = new LRUCache(capacity)
 * var param_1 = obj.get(key)
 * obj.put(key,value)
 */
```

> 复杂度分析

时间复杂度：O(1)。

空间复杂度：O(capacity)。

> 执行

执行用时：224 ms, 在所有 JavaScript 提交中击败了91.13%的用户

内存消耗：50.9 MB, 在所有 JavaScript 提交中击败了55.92%的用户
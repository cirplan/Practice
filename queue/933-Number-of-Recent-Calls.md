### 933. 最近的请求次数

> 题目

写一个 RecentCounter 类来计算特定时间范围内最近的请求。

请你实现 RecentCounter 类：

RecentCounter() 初始化计数器，请求数为 0 。
int ping(int t) 在时间 t 添加一个新请求，其中 t 表示以毫秒为单位的某个时间，并返回过去 3000 毫秒内发生的所有请求数（包括新请求）。确切地说，返回在 [t-3000, t] 内发生的请求数。
保证每次对 ping 的调用都使用比之前更大的 t 值。

示例 1：
```
输入：
["RecentCounter", "ping", "ping", "ping", "ping"]
[[], [1], [100], [3001], [3002]]
输出：
[null, 1, 2, 3, 3]

解释：
RecentCounter recentCounter = new RecentCounter();
recentCounter.ping(1);     // requests = [1]，范围是 [-2999,1]，返回 1
recentCounter.ping(100);   // requests = [<u>1</u>, <u>100</u>]，范围是 [-2900,100]，返回 2
recentCounter.ping(3001);  // requests = [<u>1</u>, <u>100</u>, <u>3001</u>]，范围是 [1,3001]，返回 3
recentCounter.ping(3002);  // requests = [1, <u>100</u>, <u>3001</u>, <u>3002</u>]，范围是 [2,3002]，返回 3
```

提示：

1 <= t <= 104
保证每次对 ping 的调用都使用比之前更大的 t 值
至多调用 ping 方法 104 次

> 思路

这是一个排好序的数组，通过记录头指针，不断往右移。也可以用队列的形式。

> 代码

```js
var RecentCounter = function() {
    this.requests =  [];
    this.position = 0;
};

/** 
 * @param {number} t
 * @return {number}
 */
RecentCounter.prototype.ping = function(t) {
    this.requests.push(t);
    const rangStart = t - 3000;
    let position = this.position;
    while (this.requests[position] < rangStart) {
        position++;
    }
    
    this.position = position;
    return this.requests.length - position;
};

/**
 * Your RecentCounter object will be instantiated and called as such:
 * var obj = new RecentCounter()
 * var param_1 = obj.ping(t)
 */
```

> 复杂度分析

时间复杂度 : O(N)。N 为push的数量

空间复杂度 : O(W)。W 为3000

> 执行

执行用时：240 ms, 在所有 JavaScript 提交中击败了98.07%的用户

内存消耗：47.3 MB, 在所有 JavaScript 提交中击败了11.95%的用户

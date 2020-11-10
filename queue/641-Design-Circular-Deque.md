### 641. 设计循环双端队列

> 题目

设计实现双端队列。
你的实现需要支持以下操作：
```
MyCircularDeque(k)：构造函数,双端队列的大小为k。
insertFront()：将一个元素添加到双端队列头部。 如果操作成功返回 true。
insertLast()：将一个元素添加到双端队列尾部。如果操作成功返回 true。
deleteFront()：从双端队列头部删除一个元素。 如果操作成功返回 true。
deleteLast()：从双端队列尾部删除一个元素。如果操作成功返回 true。
getFront()：从双端队列头部获得一个元素。如果双端队列为空，返回 -1。
getRear()：获得双端队列的最后一个元素。 如果双端队列为空，返回 -1。
isEmpty()：检查双端队列是否为空。
isFull()：检查双端队列是否满了。

示例：

MyCircularDeque circularDeque = new MycircularDeque(3); // 设置容量大小为3
circularDeque.insertLast(1);			        // 返回 true
circularDeque.insertLast(2);			        // 返回 true
circularDeque.insertFront(3);			        // 返回 true
circularDeque.insertFront(4);			        // 已经满了，返回 false
circularDeque.getRear();  				// 返回 2
circularDeque.isFull();				        // 返回 true
circularDeque.deleteLast();			        // 返回 true
circularDeque.insertFront(4);			        // 返回 true
circularDeque.getFront();				// 返回 4
```

提示：

* 所有值的范围为 [1, 1000]
* 操作次数的范围为 [1, 1000]
* 请不要使用内置的双端队列库。

> 思路

第一想法是通过操作数组来完成，但有没有其他方式呢？有的，通过设置双指针。

* 初始化，front = rear = 0，capacity = k + 1
* 从头部插入，front = fron - 1
* 从尾部插入，rear = rear + 1
* 其中会存在队列循环，所以 front = (fron - 1 + capacity) % capacity；rear = (rear + 1) % capacity
* 当 (rear + 1) % capacity === front，表示满队列

> 代码

```js
/**
 * Initialize your data structure here. Set the size of the deque to be k.
 * @param {number} k
 */
var MyCircularDeque = function(k) {
    this.queue = [];
    this.front = 0;
    this.rear = 0;
    this.capacity = k + 1;
};

/**
 * Adds an item at the front of Deque. Return true if the operation is successful. 
 * @param {number} value
 * @return {boolean}
 */
MyCircularDeque.prototype.insertFront = function(value) {
    if (this.isFull()) return false;
    let { front, capacity } = this;
    front = this.front = (front - 1 + capacity) % capacity;
    this.queue[front] = value;
    return true;
};

/**
 * Adds an item at the rear of Deque. Return true if the operation is successful. 
 * @param {number} value
 * @return {boolean}
 */
MyCircularDeque.prototype.insertLast = function(value) {
    if (this.isFull()) return false;
    let { rear, capacity } = this;
    this.queue[rear] = value;
    this.rear = (rear + 1) % capacity;
    return true;
};

/**
 * Deletes an item from the front of Deque. Return true if the operation is successful.
 * @return {boolean}
 */
MyCircularDeque.prototype.deleteFront = function() {
    if (this.isEmpty()) return false;
    this.front = (this.front + 1) % this.capacity;
    return true;
};

/**
 * Deletes an item from the rear of Deque. Return true if the operation is successful.
 * @return {boolean}
 */
MyCircularDeque.prototype.deleteLast = function() {
    if (this.isEmpty()) return false;
    this.rear = (this.rear - 1 + this.capacity) % this.capacity;
    return true;
};

/**
 * Get the front item from the deque.
 * @return {number}
 */
MyCircularDeque.prototype.getFront = function() {
    if (this.isEmpty()) return -1;
    return this.queue[this.front];
};

/**
 * Get the last item from the deque.
 * @return {number}
 */
MyCircularDeque.prototype.getRear = function() {
    if (this.isEmpty()) return -1;
    console.log('get rear', this.queue, (this.rear - 1 + this.capacity) % this.capacity);
    return this.queue[(this.rear - 1 + this.capacity) % this.capacity];
};

/**
 * Checks whether the circular deque is empty or not.
 * @return {boolean}
 */
MyCircularDeque.prototype.isEmpty = function() {
    return this.front === this.rear;
};

/**
 * Checks whether the circular deque is full or not.
 * @return {boolean}
 */
MyCircularDeque.prototype.isFull = function() {
    return (this.rear + 1) % this.capacity === this.front;
};

/**
 * Your MyCircularDeque object will be instantiated and called as such:
 * var obj = new MyCircularDeque(k)
 * var param_1 = obj.insertFront(value)
 * var param_2 = obj.insertLast(value)
 * var param_3 = obj.deleteFront()
 * var param_4 = obj.deleteLast()
 * var param_5 = obj.getFront()
 * var param_6 = obj.getRear()
 * var param_7 = obj.isEmpty()
 * var param_8 = obj.isFull()
 */

```

> 复杂度分析

时间复杂度 : O(1)。

空间复杂度 : O(K)。

> 执行

执行用时：404 ms, 在所有 JavaScript 提交中击败了8.56%的用户

内存消耗：50.3 MB, 在所有 JavaScript 提交中击败了5.43%的用户

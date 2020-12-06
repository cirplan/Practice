### 715. Range 模块

> 题目

Range 模块是跟踪数字范围的模块。你的任务是以一种有效的方式设计和实现以下接口。

addRange(int left, int right) 添加半开区间 [left, right)，跟踪该区间中的每个实数。添加与当前跟踪的数字部分重叠的区间时，应当添加在区间 [left, right) 中尚未跟踪的任何数字到该区间中。
queryRange(int left, int right) 只有在当前正在跟踪区间 [left, right) 中的每一个实数时，才返回 true。
removeRange(int left, int right) 停止跟踪区间 [left, right) 中当前正在跟踪的每个实数。

示例：
```
addRange(10, 20): null
removeRange(14, 16): null
queryRange(10, 14): true （区间 [10, 14) 中的每个数都正在被跟踪）
queryRange(13, 15): false （未跟踪区间 [13, 15) 中像 14, 14.03, 14.17 这样的数字）
queryRange(16, 17): true （尽管执行了删除操作，区间 [16, 17) 中的数字 16 仍然会被跟踪）

提示：

半开区间 [left, right) 表示所有满足 left <= x < right 的实数。
对 addRange, queryRange, removeRange 的所有调用中 0 < left < right < 10^9。
在单个测试用例中，对 addRange 的调用总数不超过 1000 次。
在单个测试用例中，对  queryRange 的调用总数不超过 5000 次。
在单个测试用例中，对 removeRange 的调用总数不超过 1000 次。
```

> 思路

没有思路，直接看的题解。（此处题解忽略

> 代码


```js
function isEven(val) {
    return val % 2 == 0;
}

function isOdd(val) {
    return !isEven(val);
}

var RangeModule = function () {
    this.ranges = [];
};

RangeModule.prototype.binarySearch = function (val) {
    let low = 0, high = this.ranges.length - 1;
    while (low <= high) {
        const mid = Math.trunc((high + low) / 2);
        const curValue = Math.abs(this.ranges[mid]);
        switch (true) {
            case val < curValue:
                high = mid - 1;
                break;
            case val > curValue:
                low = mid + 1;
                break;
            case val == curValue:
                return mid;
        }
    }
    return low;
}

/** 
 * @param {number} left 
 * @param {number} right
 * @return {void}
 */
RangeModule.prototype.addRange = function (left, right) {
    const startIndex = this.binarySearch(left);
    const endIndex = this.binarySearch(right);
    const insertNums = [];
    let spliceCount = endIndex - startIndex;
    if (isEven(startIndex)) {
        insertNums.push(left);
    }
    if (isEven(endIndex)) {
        if (endIndex < this.ranges.length && right == this.ranges[endIndex]) {
            spliceCount++;
        }
        else {
            insertNums.push(-right);
        }
    }
    this.ranges.splice(startIndex, spliceCount, ...insertNums);
};

/** 
 * @param {number} left 
 * @param {number} right
 * @return {boolean}
 */
RangeModule.prototype.queryRange = function (left, right) {
    const startIndex = this.binarySearch(left);
    const endIndex = this.binarySearch(right);
    if (startIndex < this.ranges.length) {
        if (isEven(startIndex)) {
            if (left == this.ranges[startIndex]) {
                return startIndex + 1 == endIndex;
            }
        }
        else {
            if (left < Math.abs(this.ranges[startIndex])) {
                return startIndex == endIndex;
            }
        }
    }
    return false;
};

/** 
 * @param {number} left 
 * @param {number} right
 * @return {void}
 */
RangeModule.prototype.removeRange = function (left, right) {
    const startIndex = this.binarySearch(left);
    const endIndex = this.binarySearch(right);
    const insertNums = [];
    let spliceCount = endIndex - startIndex;
    if (isOdd(startIndex)) {
        insertNums.push(-left);
    }
    if (isOdd(endIndex)) {
        if (right == Math.abs(this.ranges[endIndex])) {
            spliceCount++;
        }
        else {
            insertNums.push(right);
        }
    }
    this.ranges.splice(startIndex, spliceCount, ...insertNums);
};

/**
 * Your RangeModule object will be instantiated and called as such:
 * var obj = new RangeModule()
 * obj.addRange(left,right)
 * var param_2 = obj.queryRange(left,right)
 * obj.removeRange(left,right)
 */

```

> 复杂度分析

时间复杂度：O(logn)。

空间复杂度：额外使用了数组来存储，为O(N)。

> 执行

执行用时：332 ms, 在所有 JavaScript 提交中击败了100.00%的用户

内存消耗：50.5 MB, 在所有 JavaScript 提交中击败了100.00%的用户
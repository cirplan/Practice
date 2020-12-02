### 855. 考场就座

> 题目

在考场里，一排有 N 个座位，分别编号为 0, 1, 2, ..., N-1 。

当学生进入考场后，他必须坐在能够使他与离他最近的人之间的距离达到最大化的座位上。如果有多个这样的座位，他会坐在编号最小的座位上。(另外，如果考场里没有人，那么学生就坐在 0 号座位上。)

返回 ExamRoom(int N) 类，它有两个公开的函数：其中，函数 ExamRoom.seat() 会返回一个 int （整型数据），代表学生坐的位置；函数 ExamRoom.leave(int p) 代表坐在座位 p 上的学生现在离开了考场。每次调用 ExamRoom.leave(p) 时都保证有学生坐在座位 p 上。

示例：
```
输入：["ExamRoom","seat","seat","seat","seat","leave","seat"], [[10],[],[],[],[],[4],[]]
输出：[null,0,9,4,2,null,5]
解释：
ExamRoom(10) -> null
seat() -> 0，没有人在考场里，那么学生坐在 0 号座位上。
seat() -> 9，学生最后坐在 9 号座位上。
seat() -> 4，学生最后坐在 4 号座位上。
seat() -> 2，学生最后坐在 2 号座位上。
leave(4) -> null
seat() -> 5，学生最后坐在 5 号座位上。 
```

提示：

1 <= N <= 10^9
在所有的测试样例中 ExamRoom.seat() 和 ExamRoom.leave() 最多被调用 10^4 次。
保证在调用 ExamRoom.leave(p) 时有学生正坐在座位 p 上。

> 思路

先理解清楚题意，与离他最近的人之间的距离达到最大化的座位上，有多个这样的座位，他会坐在编号最小的座位上。所以维护一个数组，存已坐下的位置编号，注意这个要排序。然后就是判断距离，如果两个位置间的距离 / 2 比当前的还要大，则取后一段距离。

> 代码

```js
/**
 * @param {number} N
 */
var ExamRoom = function (N) {
    this.seats = N;
    this.students = [];
};

/**
 * @return {number}
 */
ExamRoom.prototype.seat = function () {
    const { seats, students } = this;
    let _student = 0;

    if (!students.length) {
        students.push(_student);
        return _student;
    }

    let distance = students[0];
    let prev = distance;
    for (let i = 1; i < students.length; i++) {
        let _seat = students[i];
        let d = Math.floor((_seat - prev) / 2);
        if (d > distance) {
            distance = d;
            _student = prev + d;
        }

        prev = _seat;
    }

    if ((seats - 1 - prev) > distance) {
        _student = seats - 1;
    }

    let flag = false;
    for (let i = 0; i < students.length; i++) {
        if (_student < students[i]) {
            students.splice(i, 0, _student);
            flag = true;
            break;
        }
    }

    if (!flag) {
        students.push(_student);
    }

    return _student;
};

/** 
 * @param {number} p
 * @return {void}
 */
ExamRoom.prototype.leave = function (p) {
    const { students } = this;
    for (let i = 0; i < students.length; i++) {
        if (students[i] === p) {
            students.splice(i, 1);
            break;
        }
    }
};

/**
 * Your ExamRoom object will be instantiated and called as such:
 * var obj = new ExamRoom(N)
 * var param_1 = obj.seat()
 * obj.leave(p)
 */
```

> 复杂度分析

时间复杂度：都是O(N)。

空间复杂度：O(N)。

> 执行

执行用时：128 ms, 在所有 JavaScript 提交中击败了100.00%的用户

内存消耗：44.3 MB, 在所有 JavaScript 提交中击败了75.00%的用户
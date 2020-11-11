### 621. 任务调度器

> 题目

给定一个用字符数组表示的 CPU 需要执行的任务列表。其中包含使用大写的 A - Z 字母表示的26 种不同种类的任务。任务可以以任意顺序执行，并且每个任务都可以在 1 个单位时间内执行完。CPU 在任何一个单位时间内都可以执行一个任务，或者在待命状态。

然而，两个相同种类的任务之间必须有长度为 n 的冷却时间，因此至少有连续 n 个单位时间内 CPU 在执行不同的任务，或者在待命状态。

你需要计算完成所有任务所需要的最短时间。

示例 ：
```
输入：tasks = ["A","A","A","B","B","B"], n = 2
输出：8
解释：A -> B -> (待命) -> A -> B -> (待命) -> A -> B.
     在本示例中，两个相同类型任务之间必须间隔长度为 n = 2 的冷却时间，而执行一个任务只需要一个单位时间，所以中间出现了（待命）状态。 
```

提示：

任务的总个数为 [1, 10000]。
n 的取值范围为 [0, 100]。

> 思路

先统计字符出现的次数，再从大到小排序。然后 n + 1 作为一次循环。优先安排出现次数最多的，这样能最节约时间。

> 代码

```js
/**
 * @param {character[]} tasks
 * @param {number} n
 * @return {number}
 */
var leastInterval = function (tasks, n) {
    let taskArray = [];
    const a_char = 'A'.charCodeAt();
    tasks.forEach(task => {
        let index = task.charCodeAt() - a_char;
        taskArray[index] = taskArray[index] || 0;
        taskArray[index]++;
    });
    taskArray.sort((a, b) => b - a);
    
    let time = 0;
    while (taskArray[0] > 0) {
        let i = 0;
        while (i <= n) {
            if (taskArray[0] === 0) {
                break;
            } else if (i < 26 && taskArray[i] > 0) {
                taskArray[i]--;
            }
            time++;
            i++;
        }

        taskArray.sort((a, b) => b - a);
    }

    return time;
};
```

> 复杂度分析

时间复杂度 : O(time)。因为给每个任务都安排了时间，因此时间复杂度和最终的答案成正比

空间复杂度 : O(1)。

> 执行

执行用时：216 ms, 在所有 JavaScript 提交中击败了12.50%的用户

内存消耗：44.4 MB, 在所有 JavaScript 提交中击败了36.90%的用户
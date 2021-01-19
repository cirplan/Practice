### 11. 盛最多水的容器

> 题目

给你 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0) 。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。

说明：你不能倾斜容器。

示例 1：
```
输入：[1,8,6,2,5,4,8,3,7]
输出：49 
解释：图中垂直线代表输入数组 [1,8,6,2,5,4,8,3,7]。在此情况下，容器能够容纳水（表示为蓝色部分）的最大值为 49。
```

示例 2：
```
输入：height = [1,1]
输出：1
```

示例 3：
```
输入：height = [4,3,2,1,4]
输出：16
```

示例 4：
```
输入：height = [1,2,1]
输出：2
```

提示：

n = height.length
2 <= n <= 3 * 104
0 <= height[i] <= 3 * 104

> 思路

可以直接暴力破解。但比较优的方式是使用双指针，重点是怎么移动指针。答案是哪边值比较小，就移动哪边。

> 代码

```js
/**
 * @param {number[]} height
 * @return {number}
 */
var maxArea = function (height) {
    if (height.length <= 1) {
        return 0;
    }

    const len = height.length;
    let max = 0;
    let left = 0;
    let right = len - 1;
    while (left < right) {
        const leftHeight = height[left];
        const rightHeight = height[right]
        const _max = (right - left) * Math.min(leftHeight, rightHeight);

        if (max < _max) {
            max = _max;
        }

        if (rightHeight < leftHeight) {
            right--;
        } else {
            left++;
        }
    }

    return max;
};
```

> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(1)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了87.55%的用户

内存消耗：40.6 MB, 在所有 JavaScript 提交中击败了62.96%的用户
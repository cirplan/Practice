### 149. 直线上最多的点数

> 题目

[链接](https://leetcode-cn.com/problems/max-points-on-a-line/)

> 思路

哈希表？

> 代码

```js
/**
 * @param {number[][]} points
 * @return {number}
 */
var maxPoints = function (points) {
    const n = points.length;
    if (n <= 2) {
        return n;
    }
    let ret = 0;
    for (let i = 0; i < n; i++) {
        if (ret >= n - i || ret > n / 2) {
            break;
        }
        const map = new Map();
        for (let j = i + 1; j < n; j++) {
            let x = points[i][0] - points[j][0];
            let y = points[i][1] - points[j][1];
            if (x === 0) {
                y = 1;
            } else if (y === 0) {
                x = 1;
            } else {
                if (y < 0) {
                    x = -x;
                    y = -y;
                }
                const gcdXY = gcd(Math.abs(x), Math.abs(y));
                x /= gcdXY;
                y /= gcdXY;
            }
            const key = y + x * 20001;
            map.set(key, (map.get(key) || 0) + 1);
        }
        let maxn = 0;
        for (const num of map.values()) {
            maxn = Math.max(maxn, num + 1);
        }
        ret = Math.max(ret, maxn);
    }
    return ret;
};

const gcd = (a, b) => {
    return b != 0 ? gcd(b, a % b) : a;
}
```

> 复杂度分析

时间复杂度：O(n ^ 2 × logm)。

空间复杂度：O(n)。

> 执行

执行用时：108 ms, 在所有 JavaScript 提交中击败了61.48%的用户

内存消耗：40.1 MB, 在所有 JavaScript 提交中击败了61.47%的用户

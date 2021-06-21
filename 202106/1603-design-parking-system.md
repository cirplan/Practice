### 1603. 设计停车系统

> 题目

[链接](https://leetcode-cn.com/problems/design-parking-system/)

> 思路



> 代码

```js
/**
 * @param {number} big
 * @param {number} medium
 * @param {number} small
 */
var ParkingSystem = function(big, medium, small) {
    this.list = [big, medium, small];
};

/** 
 * @param {number} carType
 * @return {boolean}
 */
ParkingSystem.prototype.addCar = function(carType) {
    const _carType = carType - 1;
    if (this.list[_carType]) {
        this.list[_carType]--;
        return true;
    }

    return false;
};

/**
 * Your ParkingSystem object will be instantiated and called as such:
 * var obj = new ParkingSystem(big, medium, small)
 * var param_1 = obj.addCar(carType)
 */
```

> 复杂度分析

时间复杂度：O(1)。

空间复杂度：O(1)。

> 执行

执行用时：164 ms, 在所有 JavaScript 提交中击败了75.69%的用户

内存消耗：44.9 MB, 在所有 JavaScript 提交中击败了40.72%的用户

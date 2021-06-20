### 1600. 皇位继承顺序

> 题目

[链接](https://leetcode-cn.com/problems/throne-inheritance/)

> 思路

> 代码


```js
/**
 * @param {string} kingName
 */
var ThroneInheritance = function (kingName) {
    this.edges = new Map();
    this.dead = new Set();
    this.king = kingName;
};

/** 
 * @param {string} parentName 
 * @param {string} childName
 * @return {void}
 */
ThroneInheritance.prototype.birth = function (parentName, childName) {
    if (!this.edges.has(parentName)) {
        this.edges.set(parentName, []);
    }
    this.edges.get(parentName).push(childName);
};

/** 
 * @param {string} name
 * @return {void}
 */
ThroneInheritance.prototype.death = function (name) {
    this.dead.add(name);
};

/**
 * @return {string[]}
 */
ThroneInheritance.prototype.getInheritanceOrder = function () {
    const ans = [];

    const preorder = (name) => {
        if (!this.dead.has(name)) {
            ans.push(name);
        }
        if (this.edges.has(name)) {
            for (const childName of this.edges.get(name)) {
                preorder(childName);
            }
        }
    }

    preorder(this.king);
    return ans;
};

/**
 * Your ThroneInheritance object will be instantiated and called as such:
 * var obj = new ThroneInheritance(kingName)
 * obj.birth(parentName,childName)
 * obj.death(name)
 * var param_3 = obj.getInheritanceOrder()
 */
```


> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(n)。

> 执行

执行用时：680 ms, 在所有 JavaScript 提交中击败了80.00%的用户

内存消耗：79.5 MB, 在所有 JavaScript 提交中击败了60.00%的用户

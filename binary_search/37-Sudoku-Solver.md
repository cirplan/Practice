### 37. 解数独

> 题目

编写一个程序，通过填充空格来解决数独问题。

一个数独的解法需遵循如下规则：

数字 1-9 在每一行只能出现一次。
数字 1-9 在每一列只能出现一次。
数字 1-9 在每一个以粗实线分隔的 3x3 宫内只能出现一次。
空白格用 '.' 表示。

一个数独。

答案被标成红色。

提示：

给定的数独序列只包含数字 1-9 和字符 '.' 。
你可以假设给定的数独只有唯一解。
给定数独永远是 9x9 形式的。

> 思路

？？？

> 代码

```js
/**
 * @param {character[][]} board
 * @return {void} Do not return anything, modify board in-place instead.
 */
const solveSudoku = (board) => {
  const rows = new Array(9);    
  const cols = new Array(9);    
  const blocks = new Array(9);  
  const options = ['1', '2', '3', '4', '5', '6', '7', '8', '9']; 
  for (let i = 0; i < 9; i++) { 
    rows[i] = new Set(options);
    cols[i] = new Set(options);
    blocks[i] = new Set(options);
  }

  const getBlockIndex = (i, j) => { 
    return (i / 3 | 0) * 3 + j / 3 | 0;  
  };

  for (let i = 0; i < 9; i++) {   
    for (let j = 0; j < 9; j++) {
      if (board[i][j] != ".") {
        rows[i].delete(board[i][j]);
        cols[j].delete(board[i][j]);
        blocks[getBlockIndex(i, j)].delete(board[i][j]);
      }
    }
  }

  const fill = (i, j) => {
    if (j == 9) {     
      i++;
      j = 0;
      if (i == 9) return true;  
    }
    if (board[i][j] != ".") return fill(i, j + 1); 
    const blockIndex = getBlockIndex(i, j); 
    for (let num = 1; num <= 9; num++) {    
      const s = String(num);
      if (!rows[i].has(s) || !cols[j].has(s) || !blocks[blockIndex].has(s)) continue;
      board[i][j] = s;    
      rows[i].delete(s);  
      cols[j].delete(s);
      blocks[blockIndex].delete(s);

      if (fill(i, j + 1)) return true; 
      
      board[i][j] = ".";
      rows[i].add(s);    
      cols[j].add(s);
      blocks[blockIndex].add(s);
    }
    return false;  
  };

  fill(0, 0);  
  return board;
};
```

> 复杂度分析

时间复杂度 : O(9 * 9)。

空间复杂度 : O(1)。

> 执行

执行用时：144 ms, 在所有 JavaScript 提交中击败了38.52%的用户

内存消耗：43.3 MB, 在所有 JavaScript 提交中击败了33.64%的用户

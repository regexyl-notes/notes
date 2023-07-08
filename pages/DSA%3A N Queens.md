- The **n-queens** puzzle is the problem of placing `n` queens on an `n x n` chessboard such that no two queens attack each other.
- Given an integer `n`, return *all distinct solutions to the **n-queens puzzle***. You may return the answer in **any order**.
- Each solution contains a distinct board configuration of the n-queens' placement, where `'Q'` and `'.'` both indicate a queen and an empty space, respectively.
- Examples
	- ![](https://assets.leetcode.com/uploads/2020/11/13/queens.jpg)
	  ```
	  **Input:** n = 4
	  **Output:** [[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]
	  **Explanation:** There exist two distinct solutions to the 4-queens puzzle as shown above
	  ```
- Solution
	- ```python
	  def solveNQueens(self, n: int) -> List[List[str]]:
	      grid = [-1] * n
	      result = []
	  
	      def checkDiagonal(row, col):
	          dev = 1
	          for x in range(row - 1, -1, -1):
	              if (col - dev) >= 0 and grid[x] == col - dev or (col + dev) < n and grid[x] == col + dev:
	                  return False
	              dev += 1
	          return True
	  
	      def checkCol(row, col):
	          for x in range(row):
	              if grid[x] == col:
	                  return False
	          return True
	  
	      def backtrack(row):
	          if row == n:
	              result.append(self.format(grid, n))
	              return True
	  
	          for col in range(n):
	              if checkDiagonal(row, col) and checkCol(row, col):
	                  grid[row] = col
	                  backtrack(row + 1)
	                  grid[row] = -1
	  
	          return False
	  
	      backtrack(0)
	      return result
	      
	      def format(self, placements, n):
	          result = []
	          for p in placements:
	              result.append("." * p + "Q" + "." * (n - 1 - p))
	          return result
	  ```
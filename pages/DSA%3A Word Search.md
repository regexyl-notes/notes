- Given an `m x n` grid of characters `board` and a string `word`, return `true` *if* `word` *exists in the grid*.
- The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.
- Examples
	- ![](https://assets.leetcode.com/uploads/2020/11/04/word2.jpg) 
	  ```
	  Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
	  Output: true
	  ```
	- ![](https://assets.leetcode.com/uploads/2020/11/04/word-1.jpg)
	  ```
	  Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "SEE"
	  Output: true
	  ```
	- ![](https://assets.leetcode.com/uploads/2020/10/15/word3.jpg){:height 250, :width 322}
	  ```
	  Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCB"
	  Output: false
	  ```
- Solution
	- The difference between BFS - aka queue - and backtracking is in the way past 'seen' nodes are stored. Backtracking (i.e. DFS in this case) stores it in only one location, while BFS requires individual 'seen' locations for each node traversal since you don't want that of the previous node to conflict with the next.
	- If I have to use BFS, I'll use bit masking instead of a set to store the indices of seen nodes.
	- BFS
		- ```python
		  from collections import deque
		  
		  def exist(self, board: List[List[str]], word: str) -> bool:
		      queue = deque()
		  
		      for i in range(len(board)):
		          for j in range(len(board[0])):
		              if board[i][j] == word[0]:
		                  queue.append((i, j, 0, 1 << (i * 6 + j)))
		  
		      while queue:
		          i, j, wordIdx, seen = queue.popleft()
		  
		          if wordIdx == len(word) - 1:
		              return True
		  
		          for x, y in [(0,1),(1,0),(0,-1),(-1,0)]:
		              ix, jy = i + x, j + y
		              if ix < 0 or ix >= len(board) or jy < 0 or jy >= len(board[0]):
		                  continue
		  
		              newHash = ix * 6 + jy
		              if (seen >> newHash) & 1:
		                  continue
		              if wordIdx + 1 >= len(word) or word[wordIdx + 1] != board[ix][jy]:
		                  continue
		  
		              queue.append((ix, jy, wordIdx + 1, seen | 1 << newHash))
		  
		      return False
		  ```
	- Backtracking (DFS)
		- ```python
		  def exist(self, board: List[List[str]], word: str) -> bool:
		      seen = set()
		  
		      def backtrack(x, y, wordIdx):
		          if board[x][y] != word[wordIdx] or (x, y) in seen:
		              return False
		          if wordIdx == len(word) - 1:
		              return True
		  
		          seen.add((x, y))
		          for i, j in [(0,1),(1,0),(0,-1),(-1,0)]:
		              xi, yj = x + i, y + j
		              if xi < 0 or xi >= len(board) or yj < 0 or yj >= len(board[0]):
		                  continue
		              if backtrack(xi, yj, wordIdx + 1):
		                  return True
		          seen.remove((x, y))
		  
		      for i in range(len(board)):
		          for j in range(len(board[0])):
		              if backtrack(i, j, 0):
		                  return True
		      return False
		  ```
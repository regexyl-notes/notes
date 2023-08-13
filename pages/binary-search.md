- Advanced algorithms
	- Binary lifting
	  id:: 64d84380-b46c-4a6f-b0f3-6dfd4ec3a43a
		- Works on a binary tree to get access to a parent X number of levels above a node in `O(log(n))` time.
		- TODO Attempt [Kth Ancestor of a Tree Node](https://leetcode.com/problems/kth-ancestor-of-a-tree-node/) again. Brute force in Python doesn't work unlike compiled languages.
		- How it works:
		- ```python
		  class TreeAncestor:
		    steps = 15 # O(log(n)) of the number of nodes in the binary tree, aka height of tree
		    
		    def __init__(self, n: int, parent: List[int]):
		      # Initialize 2D array of parents, such that
		      # each element represents the parents of the nodes
		      # after k levels
		    
		    def getKthAncestor(self, node: int, k: int) -> int:
		      # Start with the max. number of possible steps, calling this x
		      
		      # While there's still more jumps to go + we have not reached a dead end yet
		      while k > 0 and x > - 1:
		        # Try to hop as much as possible using x, if not decrement x by 1
		        # To hop as much as possible, you can use the bitwise left shift operator
		        # and see if k >= 1
		      
		      return kthAncestor
		  ```
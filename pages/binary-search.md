- Advanced algorithms
	- Binary lifting - works on a binary tree to get access to a parent X number of levels above a node in `O(log(n))` time.
		- TODO Attempt [Kth Ancestor of a Tree Node](https://leetcode.com/problems/kth-ancestor-of-a-tree-node/) again. Brute force in Python doesn't work unlike compiled languages.
		- How it works:
		- ```python
		  class TreeAncestor:
		    steps = 15 # O(log(n)) of the number of nodes in the binary tree
		    def __init__(self, n: int, parent: List[int]):
		      # 
		  ```
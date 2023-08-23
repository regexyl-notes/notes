- Aka priority queue
- Time complexities
	- The initialization of a heap of size m usually takes `O(mlog(m))` time, but in Python, it does it in linear time.
- Python syntax
	- Min heap by default - if you want a max-heap, then convert all values into < 0.
	- ```python
	  import heapq
	  heap = heapq.heapify(array)
	  heapq.heappush(heap, new_value)
	  heapq.heappop(heap)
	  ```
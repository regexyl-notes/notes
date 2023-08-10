- Aka priority queue
- Time complexities
	- The initialization of a heap of size m usually takes `O(mlog(m))` time, but in Python, it does it in linear time.
- Python syntax
	- ```python
	  import heapq
	  heap = heapq.heapify(array)
	  heapq.heappush(heap, new_value)
	  heapq.heappop(heap)
	  ```
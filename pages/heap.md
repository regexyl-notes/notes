- Aka priority queue
- Time complexities
	- The initialization of a heap of size m usually takes `O(mlog(m))` time, but in Python, it does it in linear time.
	- `heappush` and `heappop` take `O(logn)` time
		- It takes `O(nlogn)` to push all items onto the heap, but the `heappify` operation
- Python syntax
	- Min heap by default - if you want a max-heap, then convert all values into < 0.
	- ```python
	  import heapq
	  heap = heapq.heapify(array)
	  heapq.heappush(heap, new_value)
	  heapq.heappop(heap)
	  ```
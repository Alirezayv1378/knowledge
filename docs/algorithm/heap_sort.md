# Heapsort Algorithm
- Runs in:$$O(n\log n)$$
- Builds a [[heap|max-heap]] then do:
```python
def heap_sort(numbers: lit[int]) -> list[int]:
	max_heap = build_max_heap(numbers)
	index = len(max_heap)
	ordered_numbers = []
	while index > 0:
		ordered_numbers.append(max_heap.pop(0))
		max_heap = max_heapify(max_heap, 0)		 
		i = i-1
	return ordered_numbers
```
![[heapsort.png]]
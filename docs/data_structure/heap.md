# Heap
- A nearly complete tree which is completely filled on all levels except possibly the lowest, which is filled from the left up to a point.
- We have two kind of heaps:
	1. **Max-heaps:** Every parent is greater than it's child in the tree.$$A[Parent(i)] \ge A[i]$$
	2. **Min-heaps:** Every parent is smaller than it's child in the tree.$$A[Parent(i)] \le A[i]$$
![[heap.jpg]]
- There is a simple way to compute indices of a parent, left child, and right child.
```python
A = [16, 14, 10, 8, 7, 9, 3, 2, 4, 1]
ROOT = A[1]
def parent(i: int):
	return math.floor(i/2)

def left(i: int):
	return 2*i

def right(i: int):
	return 2*i + 1
```

## Heap Algorithm growth
- MAX-HEAPIFY procedure, runs in $O(\log n)$ 
- The BUILD-MAX-HEAP, runs in linear time.
- The [[heap_sort|HEAPSORT]] procedure, runs in $O(n\log n)$
```python
def max_heapify(numbers: list[int], i: int) -> list[int]:
	l = left(i)
	r = right(i)
	if l <= len(numbers) and numbers[l] > numbers[i]:
		largest = l
	else:
		largest = i
	
	if r <= len(numbers) and A[r] > A[largest]:
		largest = r
	if largest != i:
		numbers[i], numbers[largest] = numbers[largest], numbers[i]
		return max_heapify(numbers, largest)

def build_max_heap(numbers: list[int]) -> list[int]:
	count_numbers = len(numbers)
	index = math.floor(count_number/2)
	while index > 0:
		max_heapify(numbers, index)
		i = i - 1
	return numbers
```

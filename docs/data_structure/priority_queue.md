# Priority Queue
- A **priority queue** is a data structure for maintaining a set S of elements, each with an associated value called a **key**.  A **max-priority queue** supports the following operations:
	1. **INSERT(S, x, k)** inserts the the element *x* with key *k* into the set *S*, which is equivalent to the operation $S = S \cup \{x\}$
	2. **Maximum(S)** returns the element of S with the largest key.
	3. **EXTRACT-MAX(S)** removes and returns the element of S with the largest key.
	4. **INCREASE-KEY(S, x, k)** increases the value of element *x*'s key to the new value *k*, which is assumed to be at least as large as *x*'s current key value.
```python
def max_heap_maximum(numbers: list[int]):
	if len(numbers) < 0:
		raise Exception("heap underflow")
	return numbers[0]

def max_heap_extract_max(numbers: list[int]):
	max_num = max_heap_maximum(numbers)
	numbers = numbers.remove(max_num)
	max_heapify(numbers, 0)
	return max_num

def max_heap_increase_key(numbers: list[int], index: int, key: int):
	if key < numbers[index]:
		raise Exception("new key is smaller than current key")
	numbers[index] = key
	while index > 0 and numbers[parent(index)] < numbers[index]:
		numbers[index], numbers[parent(index)] = numbers[parent(index)], numbers[index]
		index = parent(index)

def max_heap_insert(numbers: list[int], key:int):
	numbers.append(float("-inf"))
	last_num_index = len(numbers) - 1
	max_heap_increase_key(numbers, last_num_index, key)
```



### Related docs:
1. [[heap]]
2. [[heap_sort]]
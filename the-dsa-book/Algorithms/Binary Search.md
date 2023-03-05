The binary search is the fastest searching algorithm with it's `O(log n)` time complexity and `O(1)` space complexity. It's only useful when dealing with sorted collections (mostly stored in contiguous fashion).
It works by using a technique similar to the [[Sliding Window]]. Initially we define the window starting from the first element to the last. We then take the element in the middle of the window and check if we found the element. If so we return it's index. Else we have two scenarios.
1. The middle element is greater than the target. If so, reduce the window by moving the rightmost pointer to the index of the middle element - 1 (this is because middle is greater than the target, so we exclude it).
2. The middle element is smaller than the target. In this case we're going to move the leftmost pointer to the index of the middle element + 1 (this is because middle is smaller than the target, so we exclude it)
We iterate until we either find a match or the two pointers switch place.
Here is the pseudo code of the algorithm
```
given: pointer to nums[], target

define low = 0, high = last index of nums

loop until low is greater than high
	define middle = (low + high) / 2
	if nums at middle is less than target
		low = middle + 1
	else if nums at middle is greater than high
		high = middle - 1
	else
		return middle
end.
```
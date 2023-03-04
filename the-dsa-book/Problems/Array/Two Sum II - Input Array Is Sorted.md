## Description
Given a **1-indexed** array of integers `numbers` that is already **_sorted in non-decreasing order_**, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index1]` and `numbers[index2]` where `1 <= index1 < index2 <= numbers.length`.

Return _the indices of the two numbers,_ `index1` _and_ `index2`_, **added by one** as an integer array_ `[index1, index2]` _of length 2._

The tests are generated such that there is **exactly one solution**. You **may not** use the same element twice.
#medium #leetcode

[Two Sum II - Input Array Is Sorted (leetcode #167)](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

## Constraints
1. Space complexity: `O(1)` at most
2. Array is **sorted in ascending order**
3. Array size starts **from 2 elements, up to 30.000**
4. Array items are **signed numbers**
5. There will always exist **exactly one solution**
6. Index are 1 based (this means that the first element has index 1)

## Goal
Come up with an algorithm that satisfies the following computation specifications:
* Time complexity: `O(n)`
* Space complexity: `O(1)`

## Solution
We already have an [[array]] sorted in ascending order. This means the greater the value, the higher the index. We can use this information to our advantage and use the [[Two pointers]] technique.
We can declare two "pointers", one of which is pointing at the first element of the array (smallest value) and the other pointing to the last one (greatest value). If the sum of the two is greater than the target value, we must decrease the biggest value, so, in this specific case, we're going to decrease the pointer to the end. What is going to happen is that we either find an equal value, or q smaller value. Similarly, in the case of a sum smaller than the target, we're simply going to move to the right the pointer to the start. In the last case, the sum is equal to the target, so we return the pair of indexes (by the 6ᵗʰ constraint, index + 1).
Here is the pseudo code solution
```
given: pointer to nums[], target

declare low = 0, high = last index of nums

loop until low equals high
	declare sum = nums[low] + nums[high]
	if sum is less than target
		low = low + 1
	else if sum is greater than target
		high = high - 1
	else
		return low, high
end.
```
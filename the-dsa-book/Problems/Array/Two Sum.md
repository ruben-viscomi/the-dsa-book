## Description
Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.
#easy #leetcode

[Two Sum (leetcode #1)](https://leetcode.com/problems/two-sum/)

## Constraints
1. The given array can has a **minimum size of 2 elements** and a **maximum size of 10.000 elements**.
2. The **array items are signed numbers**. This means that **they can either be positive or negative**.
3. **Only one valid answer exists** (always)

## Goal
Come up with an algorithm that satisfies the following computation specifications:
* Time complexity: `O(n)`
* Space complexity: `O(n)` at most

## Bruteforce approach
This approach get's the job done and is the easiest to develop. It solves the problem in `O(n²)` time complexity and `O(1)` space complexity.
We're going to take any existing pair of items. We sum them toghether and we compare the result with the target. If the sum matches the target, we return the indices of the pair, else we continue until we find a solution.
Here a pseudo code solution (to better understand).
```
given: pointer to nums[], target

for each i in (0 to last index of nums - 1)
	for each j in (i + 1 to last index of nums)
		if (nums at i) + (nums at j) equals target
			return i, j
end.
```

## The better approach
This approach involves the use of a [[HashMap]] and gives a time complexity of `O(n)`, as well as a space complexity of `O(n)`. We're basically sacrificing space for performance.
How does this approach work? Well... If we think of it, we can say that if we want to reach a target value and we already have a number, we also know the second number, in order to have a sum that matches the target (`n2 = target - n1`).
In more detail we can declare an [[HashMap]] and store as key, the difference between the target and the current scanned item, and as value the index of the item.
On each loop iteration, we check if the current item value is stored as key in the [[HashMap]], if so, we can return the pair of the value in that key (present in the [[HashMap]]) and the index of the current item. Else we can continue adding elements in the [[HashMap]], until a result is found.
Here a pseudo code solution.
```
given: pointer to nums[], target

declare map as HashMap of (number to number)

for each i in (0 to last index of nums)
	if map contains (nums at i)
		return (map at (nums at i)), i
	else
		map at (target - (nums at i)) = i
end.
```
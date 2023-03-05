## Description
You are given an `m x n` integer matrix `matrix` with the following two properties:

-   Each row is sorted in non-decreasing order.
-   The first integer of each row is greater than the last integer of the previous row.

Given an integer `target`, return `true` _if_ `target` _is in_ `matrix` _or_ `false` _otherwise_.

You must write a solution in `O(log(m * n))` time complexity.
#medium #leetcode 

[Search a 2D Matrix (leetcode #74)](https://leetcode.com/problems/search-a-2d-matrix/)

## Constraints
1. Time complexity `O(log(m∙n))` at most
2. matrix is of size `m` ⨯ `n`
3. both `m` and `n` can assume a minimum size of 1 and a maximum size of 100

## Goal
Come up with an algorithm that satisfies the following computation specifications:
* Time complexity: `O(log(m∙n))`
* Space complexity: `O(1)`

## Solution
Both problem description and constraints are suggesting the use of [[Binary Search]]. One of the solutions might be to consider the [[Matrix]] as an [[Array]] of size `m∙n`. This way we compute the middle of this "virtual" array and convert the value into a row-column pair. The algorithm is basically a modified [[Binary Search]] that returns a boolean value and performs extra computations to compute row index and column index.
Here is the pseudo code solution
```
given: pointer to matrix[][], target

define rows = size of matrix
define columns = size of (matrix at 0)
define low = 0, high = rows * columns

loop until low is greater than high
	define middle = (low + high) / 2
	define row = middle / columns
	define column = middle - (row * columns)
	
	if matrix at row, column is less than target
		low = middle + 1
	else if matrix at row, column is greater than target
		high = middle - 1
	else
		return true

return false
end.
```
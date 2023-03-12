## Description
Given a binary tree `root`, a node _X_ in the tree is named **good** if in the path from root to _X_ there are no nodes with a value _greater than_ X.

Return the number of **good** nodes in the binary tree.
#medium #leetcode 

[Count Good Nodes in Binary Tree (leetcode #1448)](https://leetcode.com/problems/count-good-nodes-in-binary-tree/)

## Constraints
* The number of nodes in the binary tree is in the range `[1, 10^5]`.
* Each node's value is between `[-10^4, 10^4]`.

## Goal
Come up with an algorithm that satisfies the following computation specifications:
* Time complexity: `O(n)`
* Space complexity: `O(n)`

## Solution (iterative)
#TODO 
```
given: root

define toProcess as Stack
push into toProcess, (root, value of root)
define count = 0

loop until toProcess is empty
	node, pathMax = pop from toProcess
	define max = pathMax
	if value of node is equal or greater than max
		count = count + 1
		max = value of node

	if right of node is not empty
		push into toProcess, right of node

	if left of node is not empty
		push into toProcess, left of node

return count
end.
```
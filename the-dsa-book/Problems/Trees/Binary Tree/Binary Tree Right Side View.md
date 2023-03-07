## Description
Given the `root` of a binary tree, imagine yourself standing on the **right side** of it, return _the values of the nodes you can see ordered from top to bottom_.
#medium #leetcode 

[Binary Tree Right Side View (leetcode #199)](https://leetcode.com/problems/binary-tree-right-side-view/description/)

## Constraints
1. The number of nodes in the tree range from `0` to `2000`

## Goal
Come up with an algorithm that satisfies the following computation specifications:
* Time complexity: `O(n)`
* Space complexity: `O(n)`

## Solution #1 (BFS)
This problem is very similar to [[Binary Tree Level Order Traversal]]. In terms of that problem, we can say that the solution to this one is always the last iterated element of the visited level.
How to solve this, then...
In this solution, we're going to use the [[Breadth First Search]]. We're going to declare our [[queue]] and push into it our root, we're then going to iterate until the [[queue]] is empty and inside each iteration, we're simply going to say that the number of elements present in the scanned level is non-other than the size of the [[queue]], where the first element is the left-most node and the last, the righ-most. Said so, we can dequeue every node and push their children inside the [[queue]] for the next scan. For the last dequeued node, we know that this is the one that will be visible from the right side, so, we're going to push it in our solution [[array]]. After iterating through all the levels, we can simply return our solution.
Here is the implementation
```
given: root

if root is empty
	return empty array

declare result[]
declare queue as Queue

enqueue into queue, root

loop until queue is empty
	declare nOfNodes = size of queue
	
	loop nOfNodes times
		declare node = dequeue queue
		
		if (is last iteration)
			add to result, value of node
			
		if left child of node is not empty
			enqueue into queue, left child of node
		if right child of node is not empty
			enqueue into queue, right child of node

return result
end.
```
<div align="center" style="opacity: 0.5"><font size="-1">This is the iterative solution</font></div>
#TODO 
```
TODO
```
<div align="center" style="opacity: 0.5"><font size="-1">This is the recursive solution</font></div>

## Solution #2  (DFS)
#TODO 
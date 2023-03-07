## Description
Given the `root` of a binary tree, return _the level order traversal of its nodes' values_. (i.e., from left to right, level by level).
#medium #leetcode 

[Binary Tree Level Order Traversal (leetcode #102)](https://leetcode.com/problems/binary-tree-level-order-traversal/)

## Constraints
1. The number of nodes in the tree range from `0` to `2000`

## Goal
Come up with an algorithm that satisfies the following computation specifications:
* Time complexity: `O(n)`
* Space complexity: `O(n)`

## Solution #1 (BFS)
The problem is clearly asking to group all nodes by their level. This implies that we must totally traverse a level before moving to the next one. There is 1 well known algorithm that does exactly this... It's the [[breadth first search]]. We can start by pushing to the [[queue]] the root element, if present. We're then going to loop until the [[queue]] is empty.
Let's quickly think about the next moves.
In the first iteration we're going to have exactly 1 element in the [[queue]]. The root node.
In the second iteration, the size of the [[queue]] will be exactly the number of child nodes of the root.
Let's pay closer attention.
At level 0 (or 1, depending on the indexing philosophy), the root level, the [[queue]] size equals the number of elements of that level.
At level 1, children of root, the [[queue]] size equals the number of elements in the level.
To keep this behavior, which is what we want, we can store the size of the [[queue]] (which equals the number of nodes in the level) in a variable. We then dequeue n times, where n is the [[queue]] size and each time push the result in the level elements. For any dequeue, we push into the [[queue]] the child nodes of the dequeued node. At the end of this n iterations, we're going to push our level in the solution.
Here is the pseudo code solution.
```
given: root

if root is empty
	return empty array

declare result[]
declare queue as Queue

enqueue into queue, root

loop until queue is empty
	declare nOfNodes = size of queue
	declare nodesInLevel[]

	loop nOfNodes times
		declare node = dequeue queue
		add to nodesInLevel, value of node
		if left child of node is not empty
			enqueue into queue, left child of node
		if right child of node is not empty
			enqueue into queue, right child of node
	add to result, nodesInLevel

return result
end.
```
<div align="center" style="opacity: 0.5"><font size="-1">This is the iterative solution</font></div>
#TODO 
```
TODO
```
<div align="center" style="opacity: 0.5"><font size="-1">This is the recursive solution</font></div>

## Solution #2 (DFS)
#TODO Depth first search
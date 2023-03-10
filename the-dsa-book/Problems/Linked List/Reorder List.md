## Description
You are given the head of a singly linked-list. The list can be represented as:

```
L0 → L1 → … → Ln - 1 → Ln
```

_Reorder the list to be on the following form:_

```
L0 → Ln → L1 → Ln - 1 → L2 → Ln - 2 → …
```

You may not modify the values in the list's nodes. Only nodes themselves may be changed.
#medium #leetcode 

[Reorder List (leetcode #143)](https://leetcode.com/problems/reorder-list/)

## Constraints
* The number of nodes in the list is in the range `[1, 5 * 104]`.
* `1 <= Node.val <= 1000`

## Goal
Come up with an algorithm that satisfies the following computation specifications:
* Time complexity: `O(n)`
* Space complexity: `O(1)`

## Solution
In order to perform the kind of ordering that the problem is asking, we must split the list in half and the second half must be reversed, then we insert nodes alternating from the first half and the reversed half. How can we do it? To find the middle node of the [[Linked List]] we have 2 possible ways
1. loop till the last node and keep track of the size, then loop again till the node at `size / 2`.
2. use a slow and a fast pointer. As soon as the fast pointer or its next is going to be pointing to a null pointer, the slow node will be the element in the middle.
The most efficient method is 2, because it is the fastest and the more readable (less verbose).
After that we're going to reverse the [[Linked List]], see the [[Reverse Linked List]] problem.
Now that we have both first half and reversed second half of the [[Linked List]], we're going to perform the reordering. Be very careful with the pointers.
Here is the the pseudo code solution.
```
given: head

if head is empty or next node of head is empty
	return.

declare slow as ListNode = head
declare fast as ListNode = head
loop until fast is empty or next node of fast is empty
	slow = next node of slow
	fast = next of next node of fast

declare previous as empty ListNode
declare current as ListNode = head
loop until current is empty
	declare next as ListNode = next node of current
	next node of current = previous
	previous = current
	current = next

current = head
alias current as firstHalf
alias previous as lastHalf

loop until next node of firstHalf is empty or next node of lastHalf is empty
	declare nextOfFirstHalf = next node of firstHalf
	next node of firstHalf = lastHalf
	declare nextOfLastHalf = next node of lastHalf
	next node of secondHalf = nextOfFirstHalf
	firstHalf = nextOfFirstHalf
	lastHalf = nextOfLastHalf

end.
```
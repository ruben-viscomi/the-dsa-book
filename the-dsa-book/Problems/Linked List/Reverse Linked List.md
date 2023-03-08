## Description
Given the `head` of a singly linked list, reverse the list, and return _the reversed list_.
#easy #leetcode 

[Reverse Linked List (leetcode #206)](https://leetcode.com/problems/reverse-linked-list/)

## Constraints
*   The number of nodes in the list is the range `[0, 5000]`.
*   `-5000 <= Node.val <= 5000`

## Goal
Come up with an algorithm that satisfies the following computation specifications:
* Time complexity: `O(n)`
* Space complexity: `O(1)`

## Solution (iterative)
Reversing a [[linked list]] is pretty simple, but a bit trick by dealing with pointers.
The main idea here is to keep track of previus and next nodes, make the current point to the next and update accordingly all the pointers
Here is the pseudo code implementation
```
given: head

declare previous as empty ListNode
declare current as ListNode = head

loop until current is empty
	decllare next as ListNode = next node of current
	next node of current = previous
	previous = current
	current = next
return previous
end.
```

## Solution (recursive)
To reverse a [[linked list]] through the use of recursion you must find the way of thinking, considering we're only given the head. We know that the new head must be the last node and that node must point to the n-1, which points to n-2, so on...
This makes us think of a head recursion. We're basically going to do the opposite of the iterative solution by getting to the last node and working our way down. To ease things up, it's good to think in terms of a [[Linked List]] containing 2 elements.
As soon as we hit the return phase by returning the last node, we're going to make this last pointer point to the current element. We can do this, because the last node of the returned head is actually being pointed to by the current one (the next of it is `curr.next.next`), then we're going to point the current head to a null pointer. I know it's a bit tricky, but it's easier in code.
Here is the pseudo code implementation
```
define reverse, given head as ListNode
	return head, if head is empty or next node of head is empty

	define newHead as ListNode = reverse, next node of head
	next of next node of head = newHead
	next node of head = empty

	return newHead
end.
```
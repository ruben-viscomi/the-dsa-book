## Description
Given the `head` of a linked list, remove the `nth` node from the end of the list and return its head.
#medium #leetcode 

[Remove Nth Node From End of List (leetcode #19)](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

## Constraints
* The number of nodes in the list is `size`.
* `1 <= size <= 30`
* `1 <= n <= size`

## Goal
Come up with an algorithm that satisfies the following computation specifications:
* Time complexity: `O(n)`
* Space complexity: `O(1)`

## Solution
If we're going for a one pass approach, we must to take the right approach.
Finding the right node in one pass, will certainly require to know ahead of time where to stop, but we son't know the size of the [[linked list]], how to proceed then?
Well, if we think about it (even though it might not be so trivial), we can think of moving `n` times from the start, then we can take another pointer from the start and move the first one, until it becames null. This way we're going to end up on the node we want to delete. This is because the distance between the first pointer (`fast`) and the last pointer (`slow`) is exactly `n`.
This is good, because we must now find a strategy to end up on the node before the one we want to delete.
We have to ways to safely achieve this...
1. Use another pointer which will always point to the previous of `slow`
2. Use a dummy node that points to the head of the [[linked list]] and start moving `slow` from there. This way we know that the distance between `slow` and `fast` will be of (`n + 1`).
In order to use the classical techniques used in the [[Linked List]], we're going to use the second strategy, the dummy pointer.
Found our node placed before the nᵗʰ from the end, we're simply going to set it to point to the next of it's next and return our next pointer of the head. This is to remove our dummy pointer.
Here is the pseudo code solution
```
given: head, n

if head is empty or next node of head is empty
	return empty LinkedList

declare fast as ListNode = head

loop until n equals 0
	fast = next node of fast
	n = n - 1

declare dummy as LinkedList pointing to head with random value
head = dummy

loop until fast is empty
	fast = next node of fast
	dummy = next node of dummy

next node of dummy = next of next node of dummy
return next of head
end.
```
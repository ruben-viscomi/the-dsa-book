## Description
You are given the `head` of a linked list. **Delete** the **middle node**, and return _the_ `head` _of the modified linked list_.

The **middle node** of a linked list of size `n` is the `⌊n / 2⌋th` node from the **start** using **0-based indexing**, where `⌊x⌋` denotes the largest integer less than or equal to `x`.

-   For `n` = `1`, `2`, `3`, `4`, and `5`, the middle nodes are `0`, `1`, `1`, `2`, and `2`, respectively.
#medium #leetcode 

[Delete the Middle Node of a Linked List (leetcode #2095)](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)

## Constraints
-   The number of nodes in the list is in the range `[1, 105]`.
-   `1 <= Node.val <= 105`

## Goal
Come up with an algorithm that satisfies the following computation specifications:
* Time complexity: `O(n)`
* Space complexity: `O(1)`

## Solution
If we're going to use the slow pointer fast pointer technique, we're easily and efficiently going to find the middle element. From there we must point the **previous** node to the next of the middle node. to do so, we're also going to keep track of the previous node. After we have our middle node and it's previous, we're going to perform the deletion.
Here is the pseudo code solution
```
given: head

declare slow as ListNode = head
declare fast as ListNode = head
declare previous as empty ListNode

loop until fast is empty or next node of fast is empty
	previous = slow
	slow = next node of slow
	fast = next of next node of fast

alias slow as middle
next node of previous = next node of middle

end.
```
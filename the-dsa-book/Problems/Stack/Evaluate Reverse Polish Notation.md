## Description
You are given an array of strings `tokens` that represents an arithmetic expression in a [Reverse Polish Notation](http://en.wikipedia.org/wiki/Reverse_Polish_notation).

Evaluate the expression. Return _an integer that represents the value of the expression_.

**Note** that:

-   The valid operators are `'+'`, `'-'`, `'*'`, and `'/'`.
-   Each operand may be an integer or another expression.
-   The division between two integers always **truncates toward zero**.
-   There will not be any division by zero.
-   The input represents a valid arithmetic expression in a reverse polish notation.
-   The answer and all the intermediate calculations can be represented in a **32-bit** integer.
#medium #leetcode 

[Evaluate Reverse Polish Notation (leetcode #150)](https://leetcode.com/problems/evaluate-reverse-polish-notation/)

## Constraints
* there number of given tokens can be as low as 1 and as big as 10.000
* a token can either be an operator between `'+'`, `'-'`, `'*'`, and `'/'` or an integer between `-200` and `200`, extremes included.

## Goal
Come up with an algorithm that satisfies the following computation specifications:
* Time complexity: `O(n)`
* Space complexity: `O(n)` (never actually touching `O(n)`)

## Solution
The Reverse polish notation post pones the operator to the operands, but this doesn't necessary mean that there can't be possible to find 3 or more numbers consequently. In fact in those cases, we're also dealing with nested operations.
Take for instance the following case `["4","13","5","/","+"]`.
This translates to `(4 + (13 / 5)) = 6`.
What we notice is that in such cases we want to first compute the operation between the right-most 2 numbers preceding the first operator. In order to keep track of the preceding numbers, we need a **LIFO** kind of list. Here the [[Stack]] comes in handy.
We're going first to check if the current scanned token is an operator. If not we're going to parse the string into a number (integer in this case) and store the parsed value into the stack. Else, we're going to `pop()` the first two elements present in the [[stack]] (knowing that they're in reverse order) and perform the operation defined by the token. We're then going to `push()` the result into the [[stack]] and we move to the next token. The last item remaining in the stack is our solution
Here the pseudo code solution.
```
given: tokens[]

declare stack

for i in (0 to last index of tokens)
	if token at i is contained in (+, -, *, /)
		b = pop from stack
		a = pop from stack
		when token at i
			is +, push to stack a + b.
			is -, push to stack a - b.
			is *, push to stack a * b.
			is /, push to stack a / b.
	else
		parsedNumber = parse to number token at i
		push to stack parsedNumber
return pop from stack
end.
```
## Description
Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.
#medium #leetcode 

[3Sum (leetcode #15)](https://leetcode.com/problems/3sum/description/)

## Constraints
1. The given list of numbers can have a **minimum size of 3 and a maximum of 3.000 elements**
2. the **solution must not contain duplicates**

## Goal
Come up with an algorithm that satisfies the following computation specifications:
* Time complexity: `O(n²)`
* Space complexity: `O(1)` (or `O(n)` depending on external factors)

## Bruteforce approach
This approach solves the problem in `O(n³)` time complexity and `O(n²)` space complexity.
This approach is using 3 loops, in order to get any possible combination and an [[HashMap]] to check for the duplicates. We also need to convert the found triplets into a [[string]] in order to store in the [[HashMap]], but this is considered an `O(1)` operation, since regardless of the size of the given list, we will always convert the same amount of data (3 numbers)
Here is the pseudo code solution.
```
given nums[]

declare found as HashMap of (string to boolean)
declare response[]

for i in (0 to last index of nums - 2)
	for j in (i + 1 to last index of nums - 1)
		for k in (j + 1 to last index of nums)
			declare sum = nums[i] + nums[j] + nums[k]
			declare threeString = concatenate to string (nums[i], nums[j], nums[k])
			if map contains threeString
				 go to next loop iteration
			else
				add to response (nums at i, nums at j, nums at k)
				found at threeString = true
return response
end.
```

## Solution
This approach will solve the problem in `O(n²)` time complexity and generally `O(1)` space complexity. We know that our triplets must not be duplicated into the solution, so, if we have a sorted array (can be achievable in `O(log n)`), and the lowest of the indexes points to a number that doesn't produce any valid triplet, we can simply skip any instance of that number. Now that we have a non repeating number in the triplet, we can simply say that this isn't anymore a [[3Sum]] problem, but more of a [[Two Sum]]... More specifically a [[Two Sum II - Input Array Is Sorted]] problem, because of the initial sort. Be careful, though. We must now get all the possible [[Two Sum II - Input Array Is Sorted|two sum]] solutions and these must not be repeated. How do we proceed then?
We can lay out the foundations of our [[two pointers]] technique. Inside the loop we're going to check if the sum of the triplet. If it's not valid, we move the pointers accordingly. In case it's a valid solution, we're first going to add the solution to our list of solutions, then w're going to move our two pointers to different values. This is because there might be more valid tuples that added to the first number of the triplet can equal the target (in our case 0). Be careful in this last steps as there are many points where it's possible to generate infinite loops.
Here is the pseudo code solution.

```
given nums[]

sort nums ascending

declare response[]

for each i in (0 to last index of nums - 2)
	if i is greater than 0 and nums at i equals nums at i - 1
		go to next loop iteration

	declare low = i + 1, high = last index of nums
	loop until low equals high
		declare sum = nums at i + nums at low + nums at high
		if sum is greater than 0
			high = high - 1
		else if sum is less than 0
			low = low + 1
		else
			add to response, (nums at i, nums at low, nums at high)
			increment low until nums at low is different than nums at low - 1
			increment high until nums at high is different than nums at high + 1
return response
end.
```
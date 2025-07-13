**Problem Link** : [LC 75](https://leetcode.com/problems/sort-colors/description/)
**Date** : June 18, 2025
**Topic** : [[2.1 Arrays]]
**Difficulty** : #Medium 

---
### Summary Description: 
- Given an array of 0 1 and 2. We need to sort the array without using any in built function. We must sort in-place not returning anything new 
 
## Strategy & Key Insights
 - Use three pointers `low`, `mid`, `high`
 - mid pointer is the most important one. We can imagine this as 3 parts low part should be of 0's, mid of 1's and high of 2's .
 - We will run the mid pointer, if we see 0 we will swap with low and update the current pointer and if we see 2 we will swap with high and update the high pointer else we will only update the mid pointer since we want 1's in mid.
 

## Code (Optimal)
```
low, mid, high = 0, 0, n-1
while mid < high
	if nums[mid] is 0
		swap(low, mid)
		low += 1, mid += 1    (since low is fixed now)
	elif mid is 1
		no swap needed
		mid += 1        (since we want 1 in mid)
	now if mid is 2
		swap(high, mid)
		high -= 1      (since high is fixed)
```
## TC, SC = O(N), O(1)
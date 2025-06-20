**Problem Link** : [LC 42 Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/description/)
**Date** : June 13, 2025
**Topic** : [[2.1 Arrays]]
**Difficulty** : #Hard

---
### Summary Description: 
-  Given an array `height` with some heights of bars (min 0) and width 1 (like a histogram), now we are to find the amount of water that can be stored there.
 
## Strategy / Key Logic
 - Bar needs a *valley* to trap water. i.e., we need larger bars on both side of a certain bar.
 - So *valley* can't be formed using 1 bar, 2 adjacent bars or.
 - So water can only be trapped with min of 3 bars
 - Water can't not be trapped in a sorted array
 - We need pockets to store water
 - **Condition 1** - *We need two larger bars on both sides*
 - min of (left largest & right largest) bars will give the trapped water
 - *How much water will be trapped on the i-th bar?*
	 - `min(larger bars) - height[i]` * `width` = total trapped water
	 - Now the total of all the bars will be the answer
- So we need to find the `left_max` and `right_max`
## Code (Brute-Force)
```
height = [4, 2, 0, 6, 3, 2, 5]
left_max = [0]*n
right_max = [0]*n
left_max[0] = -1 or height[0]
right_max[n-1] = -1 or height[n-1]
for i (1, n):
	leftmax[i] = max(lmax[i-1], height[i-1])

#for right max we have to staert from the right
for i (n-2, -1, -1):
	rightmax[i] = max(right_max[i+1], right_max[i+1])

trapped_at_i = min(right, left) - height_i

ans = sum of only the positives
```
##### TC SC - O(N), O(N)

## Code (Optimal)

### **Pseudocode – Two Pointer Approach**

```
Initialize:
    left = 0
    right = length of height - 1
    left_max = 0
    right_max = 0
    total_water = 0

While left < right:
    If height[left] < height[right]:
        If height[left] >= left_max:
            Update left_max to height[left]
        Else:
            Add (left_max - height[left]) to total_water
        Move left pointer to the right (left += 1)
    
    Else:
        If height[right] >= right_max:
            Update right_max to height[right]
        Else:
            Add (right_max - height[right]) to total_water
        Move right pointer to the left (right -= 1)

Return total_water
```

#### TC SC = O(N), O(1)
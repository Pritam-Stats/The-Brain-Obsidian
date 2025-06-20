- Applied on **Sorted** Array.
- We find and work with the mid of the arr
	- MAIN AIM - Don't need to search the entire array. Optimized TC
- We keep two variables start and end and we keep updating the mid and search through the mid. Since it's sorted arr we can compare and search only the part which is necessary
- **TC** - Everytime our new arr gets a cut of half, 1/2, 1/4, 1/8, ... so it's 
$$
	TC = O (log_{2} N)
$$
#### Applications : problems
1. [[Max Subarray Sum]]
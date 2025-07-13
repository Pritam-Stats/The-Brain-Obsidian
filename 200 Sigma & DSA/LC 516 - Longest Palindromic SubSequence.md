- **Problem Link** : [LC 516](https://leetcode.com/problems/longest-palindromic-subsequence/description/)
- **Date** : July 13, 2025
- **Topic** : [[Dynamic Programming]] [[String]]
- Related: [[LC 1143 - Longest Common SubSequence]]
- **Difficulty** : #Medium 

---
### Summary Description: 
- Given a String return the max subsequence length, which is a palindrome
 
## Strategy & Key Insights
###### Approach 1
- use the `reverse` string as the second string then it will be the same problem as Longest Common SubSequence (LCS)
 
###### Approach 2 (Better)
- Don't create the `rev`.
	- This will also have `O(n^2)` but will have better runtime.
- Run i in reverse order and j from the `i+1, n`
	- check i with j like a palindrome
## PseudoCode
```Python
for i in range(1, n+1):
	for j in range(1, n+1):
		if s[i-1] == rev[j-1]
			dp[i, j] = dp[]
```

## PseudoCode (Better)
```Python
for i in n-1, -1
	for j in i+1, n:
	
		

```

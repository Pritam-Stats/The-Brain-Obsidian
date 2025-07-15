- **Problem Link** : [LC5- Longest  Palindromic SubString](https://leetcode.com/problems/longest-palindromic-substring/description/)
- **Date** : July 14, 2025
- **Topic** : [[String]] [[Dynamic Programming]]
- **Difficulty** : #Medium 

---
### Summary Description: 
- Given a string return the longest substring which is a Palindrome. Substring is Contiguous.
## Strategy & Key Insights
### Approach 1 - Expand Around Center (O($n^2$), O(1))
- A palindrome Mirrors around the center.
- So for each idx we expand around two sides.
	- For even length palindrome : center at `i`
	- For odd-length palindrome : center at mid of `i` and `i+1`
- we expand outwards while two sides matches.
## PseudoCode (Brute-Force)
```

```



## PseudoCode (Optimal)
```

```

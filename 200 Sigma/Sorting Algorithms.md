Topic :  [[]]
**Created** : June 14, 2025 | 10:25 PM
*Tags*: 

---
## [[Bubble Sort]]
- *Idea* : Think like a bubble, we send the large element to the end by **Swapping** with the adjacent.
- `[5, 4, 1, 3, 2]` Consider this array. In bubble sort we keep swapping two items in each turn 
- Turn 1 (iterations)
	- A loop runs
	1. 5 and 4 gets swapped - `4 5 1 3 2`
	2. `4 1 5 3 2`
	3. `4 1 3 5 2`
	4. `4 1 3 2 5` - This will be the there at the end of turn 1
	- So the inner loop ran for `n-1` times
	- So after turn 1, 1 item will get sorted
- So to sort 5 items we need to sort the 4 so n-1
- Outer loop (for turns) `n-1`
#### TC - $O(n^2)$







### Code Block

```

```


]]
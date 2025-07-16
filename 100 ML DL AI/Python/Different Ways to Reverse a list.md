**Topic :  [[2.00 Arrays]]
**Created** : June 12, 2025 | 11:56 PM
*Tags*: #DSA #Easy #python 

---
Great! Let's **compare all the methods that do not require external modules or libraries** (i.e., no `collections`, `functools`, `numpy`, etc.). That gives us **7 methods** to compare.

---

## ✅ **Methods Compared**

|No.|Method|In-Place?|Creates New List?|Time Complexity|Space Complexity|Notes|
|---|---|---|---|---|---|---|
|1|`list.reverse()`|✅ Yes|❌ No|O(n)|O(1)|Fastest in-place method|
|2|Slicing `[::-1]`|❌ No|✅ Yes|O(n)|O(n)|Clean one-liner|
|3|`reversed()` + `list()`|❌ No|✅ Yes|O(n)|O(n)|Returns iterator initially|
|4|Loop with `insert(0, item)`|❌ No|✅ Yes|❌ O(n²)|O(n)|Very inefficient|
|5|List comprehension with `range()`|❌ No|✅ Yes|O(n)|O(n)|Index-based; readable|
|6|`while` loop (new list, append)|❌ No|✅ Yes|O(n)|O(n)|Manual control|
|7|`while` loop (in-place swap)|✅ Yes|❌ No|O(n)|O(1)|Good for algorithm practice|

---

## 🔍 **Quick Takeaways**

- ✅ **Fastest and cleanest**:
    
    - `list.reverse()` (in-place)
        
    - Slicing `[::-1]` (copy)
        
    - `reversed()` (with or without `list()`)
        
- 🧠 **Best for interviews/learning**:
    
    - `while` loop (in-place swap)
        
    - List comprehension with `range()`
        
- ❌ **Avoid for performance**:
    
    - Loop with `insert(0, item)` – extremely slow on large lists due to shifting elements every time.
        

---

Would you like a benchmark chart comparing actual run times for each method with large lists?
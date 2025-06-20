**Problem Link** : [LeetCode 121 - Best Time to Buy & Sell Stock](Paste the Link)
**Date** : June 11, 2025
**Topic** : [[2.1 Arrays]]
**Difficulty** : #Easy

---
### Summary Description: 
- Given an array as Prices of a stock in each day. We have to buy on a certain day and sell in such day that maximizes our profit, if the stock prices are declining continuously we return -1, else we are to return the max possible profit. 

## Strategy
```
price = [7,1,5,3,6,4] 
```
- Most intuitive thought is - 
	- We have to *buy at minimum price* and *sell at max price*
	- But max(price) - min(price) won't work, since we can't buy late and sell at previous day.
	- We can't buy and sell on the same day
- **Approach**
	- Assume each day as a possible *Sell Day*
	- Then, We have to find the best buy day for that sell day
	-  So for a given price of 6 days we will have 5 best buy day
	- Initialize best buy price array with $+\infty$, for sell day 0 	
	- then we calculate the profit for each day and return the max profit
	- For the i-th sell day we will have the min of i-1 days of price
		- We add the min of previous days in the best buy array
		- "On day `i`, what's the best day before this to buy stocks?"
	- And we can't buy on the last day. 


#### What's the purpose of the First approach when the second one is both easy and optimal?

While the **second approach** (`maxProfit2`) is clearly the **optimal** solution in terms of both **time and space**, there are valid **pedagogical reasons** why your instructor may have started with the **first approach**

---

### 🎓 Why the First Approach Is Often Taught First:

#### ✅ 1. **Focuses on Conceptual Understanding**

- The first approach uses an auxiliary array `bestBuy[]`, which explicitly stores the **best price to buy** before each day.
    
- This helps students **visualize and understand** the problem step-by-step:  
    _"On day `i`, what's the best day before this to buy stocks?"_
    
- It reinforces:
    
    - The idea of **dynamic programming-style** tracking
        
    - How to precompute values and reuse them
        

---

#### ✅ 2. **Bridges Toward Optimization**

- It acts as a **transition** from brute force to optimal:
    
    - Brute force would be O(n²): check all pairs (i, j)
        
    - First approach reduces it to O(n) time, O(n) space
        
    - Then the second approach (your `maxProfit2`) reduces it further to O(1) space
        
- It teaches the idea of **space optimization**:  
    _"We only need the previous best, not the whole array."_
    

---

#### ✅ 3. **Easier to Debug or Print Internally**

- You can `print` the `bestBuy[]` array to trace what’s happening — useful for learners.
    
- Students can literally **see the lowest price so far** for each index.
    

---

#### ✅ 4. **Pattern for More Complex Problems**

- This approach mimics the **prefix/min tracking** technique that generalizes well to:
    
    - Problems involving multiple transactions (LeetCode 122)
        
    - Max subarrays with constraints
        
    - Dynamic programming state transitions
        

---

### 🧠 Analogy:

Think of it like **learning long division before a calculator**:

- It’s not the fastest way to get an answer.
    
- But it **teaches the mechanics** underneath the shortcut.
    

---

### ✅ When You Should Use Each:

|Approach|When to Use|
|---|---|
|**First**|Learning phase, tracing logic, debugging|
|**Second**|Interviews, production, contests|

---

### 🔚 Final Thought:

> Your instructor isn’t wrong — they’re teaching you **why** it works before **how** to make it optimal.

You’re now in the perfect position:

- You understand the **logic behind** the approach
    
- And you know how to **optimize it** for real-world use
    

Let me know if you'd like to see how this scales up to variants like **k transactions** or **cooldown problems**!
---

### ✅ Using `std::min` and `std::max`:

```cpp
#include <iostream>
#include <vector>
#include <algorithm>  // for min and max

using namespace std;

int maxProfit(vector<int>& prices) {
    int minPrice = INT_MAX;
    int maxProfit = 0;

    for (int price : prices) {
        minPrice = min(minPrice, price);
        maxProfit = max(maxProfit, price - minPrice);
    }

    return maxProfit;
}
```

---

### ✅ Equivalent Using `if-else`:

```cpp
int maxProfit(vector<int>& prices) {
    int minPrice = INT_MAX;
    int maxProfit = 0;

    for (int price : prices) {
        if (price < minPrice)
            minPrice = price;

        if (price - minPrice > maxProfit)
            maxProfit = price - minPrice;
    }

    return maxProfit;
}
```

---

### 🔍 Comparison:

|Aspect|`min()` / `max()` Version|`if-else` Version|
|---|---|---|
|**Readability**|More concise ✅|Slightly more verbose|
|**Performance**|Essentially same in modern C++ ✅|Might be microscopically faster|
|**Header Needed**|`#include <algorithm>` ✅|No need for `<algorithm>`|
|**Use Case**|Prefer when expressions are simple|Prefer if conditions are complex|

---

### 🧠 Performance in C++:

- In **compiled code**, the difference is often **optimized away** by modern compilers like GCC, Clang, and MSVC.
    
- Any micro-difference is typically not a bottleneck unless in **tight loops with millions of iterations** (e.g., game engines or high-frequency trading systems).

---

### ✔️ Final Verdict:

Both are **correct** and **efficient**. Use:

- `min()` / `max()` for **clean, functional-style code**
    
- `if-else` if you want **fine control**, or are doing **more than just assignment**
---
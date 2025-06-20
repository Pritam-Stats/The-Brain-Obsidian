**Topic :  [[2.1 Arrays]]
**Created** : May 16, 2025 | 6:45 PM
*Tags*: #BinarySearch #problem

---
We already know [[Print all Subarrays]]
## Brute Force
- Go through all the subarray and keep calculating the sum and return the max
### Code Block
$$
TC = O(n^3)
$$
```
#include <iostream>

using namespace std;

  

void subSum(int *arr, int n) {

    int maxSum = INT_MIN;

  

    for (int st = 0; st < n; st++) {

        for (int end = st; end < n; end++) {

            int currSum = 0;     //initialize the sum for each subarray

  

            //Final loop for the sum

            for (int i = st; i <= end; i++) {

                currSum += arr[i];

            }

            cout << currSum << ",";

            maxSum = max(maxSum, currSum);

        }

        cout << endl;

    }

    cout << "Max SubArray Sum = " << maxSum << endl;

}

  

int main() {

    // Your code here

    int arr[] = {2, -3, 6, -5, 4, 2, 9};

    int n = sizeof(arr) / sizeof(int);

  

    subSum(arr, n);

    return 0;

}
```

## Better
We will remove the 3rd loop.

$$
TC = O(n^2)
$$
### Code

```
arr = [2, -3, 6, -5, 4, 2]

  

def maxSub(arr: list) -> int:

    n = len(arr)

    maxSum = float('-inf')

    for st in range(n):

        #fixed start point

        currSum = 0

        for end in range(st, n):

            currSum += arr[end]

            maxSum = max(maxSum, currSum)

  

    return maxSum

  

print(maxSub(arr))
```

## Best - Kadane's Algorithm
- The simplest Algorithm. **TC = O(N)**
- Main intuition - Whenever the currSum values appears less than 0, we re-initialize the variable to zero, since one negative value  won't contribute in max value.

### Code

```
def kadanes(arr:list) -> int:

    n = len(arr)

    maxSum = float('-inf')

    currSum =0

    for i in range(n):

        currSum += arr[i]

        maxSum = max(maxSum, currSum)

  

        #main algo

        if currSum < 0:

            currSum = 0

  

    return maxSum

  

print(kadane(arr= [2, -3, 6, -5, 4, 2]))

print(kadane(arr= [-1, -2, -3, -5]))
```
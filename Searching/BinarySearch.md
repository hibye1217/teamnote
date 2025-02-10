# Binary Search
## Summary
The algorithm to find the specific element in the sorted array in $\mathcal O(\log N)$ time.

## Definitions and Constraints
### Input
The input is the array $A$, and the element $x$ that may or may not be in $A$.

$A$ must be sorted in increasing order i.e. $A_{i-1} \le A_{i}$ for all $i$.

Let $N$ be the length of the $A$.

### Output
Whether or not $x$ is in $A$. Depending on the context, you might also have to find the $i$ such that $A_i = x$ holds.

## Strategy
Let's use the fact that $A$ is sorted. If we compare $x$ with some element $A_{i}$, then we get one of the three results.
- $A_i < x$: In this case, $x$ must be *right* to the $A_i$, as every element left to the $A_i$ will be even smaller than $A_i$, and thus $x$ as well.
- $A_i = x$: Congratulation! You have found the index.
- $A_i > x$: In this case, $x$ must be *left* to the $A_i$, as every element right to the $A_i$ will be even bigger than $A_i$, and thus $x$ as well.

But which element should we compare with? Since we want to be safe and not risk anything, it might be best if we ask the middle of the array.
Which works surprisingly well, as if you keep asking the middle of the array, then you always divide the length of the array by $2$, reaching the end case in $\mathcal O(\log N)$ steps.

## Code
The following code find the index $i$ with $A_{i} = x$, or report that none exist by returning $-1$.
```cpp
int BinarySearch(int* A, int N, int x){
    int st = 0, ed = N-1; while (st <= ed){
        int mid = (st+ed) / 2;
        if (A[mid] == x){ return mid; }
        if (A[mid] < x){ st = mid+1; } // so the searcing part is now [mid+1, ed]
        else{ ed = mid-1; }            // so the searcing part is now [st, mid-1]
    } return -1;
}
```

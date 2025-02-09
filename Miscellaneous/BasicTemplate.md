# Basic Template
Base code that is basically written in every submissions of mine.

## C++
### Base
Code that I use when I'm just doing Problem Solving.
If I'm doing Competitive Programming (with prewritten code allowed), I additionally use the most of the stuffs mentioned below.

```cpp
#include <bits/stdc++.h>
#define endl '\n'
using namespace std;
const int PRECISION = 6;



void Main(){
    
}

int main(){
    ios_base::sync_with_stdio(0); cin.tie(0); cout.tie(0);
    cout.setf(ios::fixed); cout.precision(PRECISION); Main();
}
```

This code includes fastIO (including `endl`) and fixed precision, as well as `<bits/stdc++.h>` and `std`.

### Type Declarations
It's painful to write `long long` every time, so `ll` is surely better, right?
```cpp
using ll = long long;
using ld = long double;
using i128 = __int128;

using pi2 = pair<int, int>;
using pl2 = pair<ll, ll>;
using pd2 = pair<ld, ld>;
#define fr first
#define sc second

template <typename T> using priority_stack = priority_queue< T, vector<T>, greater<T> >;
```

Basically, there are three types of declaration going on here.
- Fast ways to type the basic types.
- Fast ways to type some pairs of basic types, as well as their members `first` and `second`.
- `priority_stack<T>`, which is just `priority_queue<T>` with reversed priority.

### Simple Mathematical Functions
```cpp
inline int sgn(ll x){ return (x > 0) - (x < 0); }
inline ll gcd(ll a, ll b){ return b==0 ? a : gcd(b, a%b); }
inline ll lcm(ll a, ll b){ return a/gcd(a,b)*b; }
```

Self explanatory. It's just a sign of a value, and gcd, lcm of 2 values.

### `std::vector` Manupulations
```cpp
template <typename T> inline void unq(vector<T>& v){
    sort(v.begin(), v.end()); v.erase(unique(v.begin(), v.end()), v.end());
}
template <typename T> inline int cvt(vector<T>& v, T x){
    return lower_bound(v.begin(), v.end(), x) - v.begin();
}
template <typename T> inline void erase(vector<T>& v, const T& x){
    v.erase(remove(v.begin(), v.end(), x), v.end());
}
```

- `unq` sorts, then removes the nonunique elements. Works in $\mathcal O(N \log N)$.
- `cvt` finds the specific element `x` in `v` in $\mathcal O(N)$. This function assumes that `x` is in `v`.
- `erase` removes the `x` in `v`. Works in $\mathcal O(N)$.

## Python
```py
import sys; input = lambda: sys.stdin.readline().rstrip('\n')
from functools import cmp_to_key
sort = lambda arr, cmp: arr.sort(key=cmp_to_key(cmp))
inputs = lambda t, l=tuple: l(map(t, input().split()))
```

Basically...
- `input` is now FastIO.
- `sort(arr, cmp)` sorts `arr` using `cmp` as a compare function.
- `inputs(int)` returns inputted space-seperated integers to tuple.
- ... while `inputs(float, list)` returns real number inputs into list.

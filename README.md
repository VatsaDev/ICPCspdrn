# ICPCspdrn
Speedrunning ICPC topics

*note on printf scanf*
large input/output might need to use printf and scanf for speed purposes, unlikely, but maybe

for `cin` and `cout`, use these lines
```cpp
ios::sync_with_stdio(false);
cin.tie(nullptr);
```
also always end with `'\n'`, not `endl`, its faster

## Divide search and conquer

### Binary Search

quickly find values in sorted arrays
main idea is to split large array by half every time, by check diff indexes

```cpp
#include <bits/stdc++.h>

using namespace std;

int main() {
  int bins(int a[], int n, int target){
    l = 0;
    r = n-1;
    int m;

    while(l <= r){
      m = l + (r-l)/2 // same as (l+r)/2, but no overflow

      if (a[m]==target){
        return m;
      } else if (a[m] < target){
        l = m + 1
      } else {
        r = m - 1
      }
    }

    return -1;
  }
}
```

Exanple, of checking whether any value is a square root of target num or not

```cpp
// make an array from 0 to target/2
#include <bits/stdc++.h>

using namespace std;

int binroot(int target){

    int a[(target/2)];

    for (int i=0; i<(target/2); i++){
        a[i]=i;
    }

    int l = 0;
    int r = (target/2)-1;
    int m;

    while (l <= r){
        m = l+(r-l)/2;

        if (pow(a[m],2)==target){
            return a[m];
        } else if (pow(a[m],2) < target){
            l = m + 1;
        } else {
            r = m - 1;
        }
    }

    return -1;
}

int main(){
    cout << binroot(4096) << "\n";
}
```


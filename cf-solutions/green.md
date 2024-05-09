## 1200
### Math
**Problem Link: https://codeforces.com/contest/1877/problem/C**
Each index inherit from mod of prev. Look at example testcases.
Lets choose some number $x$ at the start. We then mod it by n to get y = x mod n.
As we move along, the mod i will get smaller, but y will stay the same since y < i, until y = i.
Then, it will become 0. Thus, **observation 1: there can be at most 3 distinct values, else its impossible**.
If k = 1, we must make it 0 at the start, since anything else will cause it to have 0 and itself(mod 1 will make it 0), so 2 distinct. So just output 1.
If k = 2, we must pick a number from start, then make it 0(when mod 1 comes). Must have some number between 1 and n inclusive. So, output n.
If k = 3, we can't pick between 1 and n since it'll make it 2, but if we do > n it makes it so that a_n+1 differs from mod differs from 0, so 3. So output m-n.
If k > 3, output 0.
**First mistake:** costed my first WA tc 1. When you do x mod n where x > n, it may just be 0 if x mod n === 0 so there are only 2 numbers instead of 3 even if x > n. Thus, all x such that x > n and x mod n === 0 must also be counted as k = 2. 
This means if k = 2, return n + m/n-1 to account for n itself so -1 and if k = 3, return m-(n + m/n-1).
**Second mistak:** we have to consider when m < n, n + m/n-1  doesn't hold when k = 2. Since we want all numbers possible < n, we must do
min(m, n+m/n-1). 
**Lesson:** must consider all cases, and write out what works and what doesn't. Here, this would've avoided both mistakes
```cpp
void solve(){
    long long n,m,k; cin>>n>>m>>k;
    if(k==1){
        cout<<1<<endl;
    }
    else if(k == 2){
        cout<<min(m,n+m/n-1LL)<<endl;
    }
    else if(k==3){
        cout<<max(0LL,m-n-m/n+1LL)<<endl;
    }
    else{
        cout<<0<<endl;
    }
}
```

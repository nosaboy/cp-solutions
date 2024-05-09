# Green
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

## 1300
### Math
**Problem Link:** https://codeforces.com/contest/1850/problem/F
This is simple since frogs all start from 0. Thus, it will land on x if x is a multiple of a_i. For each value a_i, we find how many frogs has that, then we use the trick n+n/2+n/3+... = nlogn to brute force over all multiples and add the number of frogs to the total frogs that land on that index. We then go through each index from 1 - n and find the one with maximum frogs(which is already stored).






# Cyan

## 1500

### Math

**Problem:** https://codeforces.com/contest/1877/problem/D
Classic **"we get score for each way to choose, find sum over all possible ways"** problem. 
Separate each value individually and count the number of ways that works for that value(score), then multiply it by the value, then sum them up.
For each value n, we see that we will get that value through any set of its divisors of its index(including 1 and itself). Let this be x. We then have 2^x-1 ways
to choose some set of dvivisors of n. Then, let there are y remaining numbers to choose from. The total ways is then (2^x-1) * (2^y).
So we add n * (2^x-1) * (2^y) to ans.
Then, if we now choose any of its divisors, the score will be n which was already counted. Thus, we must eliminate every index from this set of divisors so we
never choose it again, thus the vis array.



### Data Structures

**Problem:** https://codeforces.com/contest/1883/problem/D
CLassic **line intersecting** problem. We need to add and delete lines and find if there are some segements that intersect.
We can use simple greedy method as we just find the largest starting and smallest ending and see if they cross, cause thats the best choice. We use multiset to do these operations in logn.
Sidenote: This shouldve been grey problem.




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

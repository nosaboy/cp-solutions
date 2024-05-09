## 1700
### Greedy
**Problem:** https://codeforces.com/contest/1883/problem/E
Simple greedy observation: to make it non-decreasing, we must increase 2nd element until it's bigger than 1st. Then increase 3rd element until it's than 2nd at the moment and so on. We always increase if prev element is smaller, since that's the only way. 
The hard part is counting how many moves for each, since each number can be increaed by 2^10^5 which will overflow. We use trick to account for this: Compare the two numbers, we want to increase 2nd number so its >= 1st.
Say we know how many moves x the 1st number already made, so right now its a * 2^x. We want b * 2^y >= a * 2^x. We want to know y value. We get 2^y/2^x >= a/b, so 2^{y-x} >= a/b where y is min. y-x >= log_2(a/b), y >= log_2(a/b)+x.
I split into two cases but this can work, its simple greedy + math.


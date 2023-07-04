# June 2023

Date | Things I have learned | Proof
----|----|----|
13 | 1. SOD , NOD <br>2.Solved 20 problem on lightoj | 1. [Problems](https://github.com/piru72/Online_Judge_Solves/commit/ed3be1b558ce148939856d7841cc04eb3384856f) <br>2.  [Problems](https://github.com/piru72/Online_Judge_Solves/commit/d2133a6c3012bd4794ef0843c18cd1771b6eef5d)
14 | 1. LCM ,GCD , Euler Totient , BigMOd , Modular Inverse , Extended GCD <br> 2. Solved 10 problems on light oj | 1. [Study](https://github.com/piru72/ICPC_PREPARATION/commit/1d612e369f5b442dba80d89eeec0193a311153c7) <br> 2. [Problems](https://github.com/piru72/Online_Judge_Solves/commit/4fcac178845c8a86b2e4fb2b0de735d0808f9959)
15 | 1. Solved 8 problems on light oj<br> 2. Combinatronics | 1. [Problems](https://github.com/piru72/Online_Judge_Solves/commit/6ac7b24ebc4b1d6155cfedc97024a43e445f103e)  <br> 2. [Study](https://github.com/piru72/ICPC_PREPARATION/commit/7ae0b04ba46ef92159886a6337ea8738272ee4bf) 
16 | 1. KMP <br> 2. Problems of kmp | 1. [problems](https://github.com/piru72/Online_Judge_Solves/commit/3be15b88c9fcd92c665929887392d54ee4be753a)
17 | 1. Rabin Karp | 1. [Problem](https://github.com/piru72/Online_Judge_Solves/commit/d491d557194912515193479b2d63c1a55e90de91)
18 | 1. Atcode Beginer easy | 1. [Q](https://kenkoooo.com/atcoder/#/training/Boot%20camp%20for%20Beginners/1) [Ans]()
19 | 1.Solved Leetcode , cf | 1. [Q]
20 | 1.Solved Leetcode(neetcode array) , cf(string 1000 , contest) , atcoder(easy)  | 1. [Q]
21 | 1.Solved Leetcode(Neetcode stack) , atcoder(easy) | 1. [Q]



## 1 July 2023

So today I started the day watching video [this]() video. Point I found useful 
1. solving problem randomly will give you a better view to understand all the possible way of solving the problem instead of learning topicwise which will already tell you which approach to choose.
2. Follow someone who is closer to your current stats
3. Upsolve problems
4. Instead of focusing on lots of algos learn few with deep understanding.
5. `learn when you are stuck`
6. `Make your weak point the strongest`

Sovled problem from 1.1 [Practice] Introduction to Competitive Programming
Contest 1: Very Basic Practice

```
1. It's better to use const when the value is constant
2. It is always better to use fixed when you use setprecision
3. Keep check for tle constrains
4. c/c++ division operator does floor division by default IF a and b are integers
5. \n instead of endl
6. isUpper , isAlpha , toLower , toUpper rather than ascii conversion
7. When value is not needed just the decision is needed log can be used for large values
```


## 2 July 2023

sovled problem from 1.1 [Practice] Introduction to Competitive Programming
Contest 2: Loops Practice
```
1. Avoid using long long int when not needed
2. Keep check for tle constrains
3. Always check for lema in case of large constrains . Generate hadnwrittern solves and find the pattern from there
4. Use bitwise where possible for faster execution . For finding base 2 use log2
5. Keep in check for worst case . Calculate problems solution for worst case if mind is emtpy then do bruteforces then try to find pattern and then try to find the solution with efficient algo
6. Keep an eye for perfection 
7. Use stl when possible
```
```cpp

vector<bool> mark(1000000, true);
vector<int> primes;

void sieve(int n)
{

    mark[0] = mark[1] = false; // 0 , 1 is not prime

    for (int i = 4; i <= n; i += 2) // even numbers are not prime
        mark[i] = false;

    primes.push_back(2); // 2 is prime

    for (int i = 3; i <= n; i += 2)
    {
        if (mark[i])
        {
            primes.push_back(i); // i is prime

            if (i * i <= n + 2)
            {
                for (int j = i * i; j <= n; j += i * 2) // cutt off all the multiples of i
                    mark[j] = false;
            }
        }
    }
}
```

 
```cpp
/* 
For doing prime factorization also can be used for finding disticnt prime divisors count

*/
int numberOfPrime(int n)
{
    int primeCount = 0;

    for (int i = 0; i < primes.size(); i++)
    {
        //cnt++;
        int prime = primes[i];
        if (n % prime == 0)
        {
            primeCount++;
            while (n % prime == 0)
            {
                n /= prime;
                //cnt++;
            }
        }
        if (n <= 1)
            break;
    }

    return primeCount;
}


```
 1. Double and pow might give precision issues have to be careful to use them
 2. int can hold upto 2* 10^9 and long long int can hold upto 9*10^18
 3. Whenever using double loops always check for i , j are written properly

 
## 3 July 2023

Well took the class of warm up 3 solved porblems for function and recursion.

1. 0 %2 = 0
2. Using dp in fibonacci reduces the time complexity from exponential to linear from 2 second to 2ms using dp
```cpp
// For getting total time elapsed in code
  cerr << "\n\n\n"<< (float)clock() / CLOCKS_PER_SEC * 1000 << " ms" << endl;
```

```cpp
// For fast io
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
```

## 4 July 2023
`F. Eating Candies cf rating 1100` used suffix and prefix sum to solve the problem. The problem could be sovled using binary search as I could clearly see a monotonic function. But I was not able to implement it. I have to practice more on binary search. So chose to implement it using map to find out if a number occurs twice and as it was in linear time it got solved .

Currently sovling problems from cftracker.

```
!!!!!!!!!! Solved my first ever bit releated problem of rating 1300 !!!!!!!!!!
```
## [Maximal AND](https://codeforces.com/contest/1669/problem/H)


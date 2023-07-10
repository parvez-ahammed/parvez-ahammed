# June 2023

| Date | Things I have learned                                                                                        | Proof                                                                                                                                                                                                                         |
| ---- | ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 13   | 1. SOD , NOD <br>2.Solved 20 problem on lightoj                                                              | 1. [Problems](https://github.com/piru72/Online_Judge_Solves/commit/ed3be1b558ce148939856d7841cc04eb3384856f) <br>2. [Problems](https://github.com/piru72/Online_Judge_Solves/commit/d2133a6c3012bd4794ef0843c18cd1771b6eef5d) |
| 14   | 1. LCM ,GCD , Euler Totient , BigMOd , Modular Inverse , Extended GCD <br> 2. Solved 10 problems on light oj | 1. [Study](https://github.com/piru72/ICPC_PREPARATION/commit/1d612e369f5b442dba80d89eeec0193a311153c7) <br> 2. [Problems](https://github.com/piru72/Online_Judge_Solves/commit/4fcac178845c8a86b2e4fb2b0de735d0808f9959)      |
| 15   | 1. Solved 8 problems on light oj<br> 2. Combinatronics                                                       | 1. [Problems](https://github.com/piru72/Online_Judge_Solves/commit/6ac7b24ebc4b1d6155cfedc97024a43e445f103e) <br> 2. [Study](https://github.com/piru72/ICPC_PREPARATION/commit/7ae0b04ba46ef92159886a6337ea8738272ee4bf)      |
| 16   | 1. KMP <br> 2. Problems of kmp                                                                               | 1. [problems](https://github.com/piru72/Online_Judge_Solves/commit/3be15b88c9fcd92c665929887392d54ee4be753a)                                                                                                                  |
| 17   | 1. Rabin Karp                                                                                                | 1. [Problem](https://github.com/piru72/Online_Judge_Solves/commit/d491d557194912515193479b2d63c1a55e90de91)                                                                                                                   |
| 18   | 1. Atcode Beginer easy                                                                                       | 1. [Q](https://kenkoooo.com/atcoder/#/training/Boot%20camp%20for%20Beginners/1) [Ans]()                                                                                                                                       |
| 19   | 1.Solved Leetcode , cf                                                                                       | 1. [Q]                                                                                                                                                                                                                        |
| 20   | 1.Solved Leetcode(neetcode array) , cf(string 1000 , contest) , atcoder(easy)                                | 1. [Q]                                                                                                                                                                                                                        |
| 21   | 1.Solved Leetcode(Neetcode stack) , atcoder(easy)                                                            | 1. [Q]                                                                                                                                                                                                                        |

# 1 July 2023

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

# 2 July 2023

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


<details>
<summary> sieve</summary>

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

</details>



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

1.  Double and pow might give precision issues have to be careful to use them
2.  int can hold upto 2* 10^9 and long long int can hold upto 9*10^18
3.  Whenever using double loops always check for i , j are written properly

# 3 July 2023

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

# 4 July 2023

`F. Eating Candies cf rating 1100` used suffix and prefix sum to solve the problem. The problem could be sovled using binary search as I could clearly see a monotonic function. But I was not able to implement it. I have to practice more on binary search. So chose to implement it using map to find out if a number occurs twice and as it was in linear time it got solved .

Currently sovling problems from cftracker.

```
!!!!!!!!!! Solved my first ever bit releated problem of rating 1300 !!!!!!!!!!
```

## [Maximal AND](https://codeforces.com/contest/1669/problem/H)

## [Answer the Queries](https://toph.co/p/answer-the-queries)

```
1. Solving approach
We have to keep an eye as there was no update operation needed so we can use a map to store the indices of a value so they are consistant.
Then just use the query to find the maximum value in range and pick out the indices of that value from the map and then we gotta check which indices are in the range to get the answer. which can be done by using uppre and lower bound

2. Mistakes
Also the thing that got me two wa  is this
>> if (l > r) return 0;

as the value could be negative I had to handle the case like this
>> if (l > r) return -1e9;

Also during building the tree it is better to store a single value rather than pair as it will be easier to handle the case of leaf node.

```

## Finding out the maximum value in a range using segment tree

The tree will be built in such a way that the root node will contain the maximum value in the range l to r .The query will return the maxium value in the range l to r .

```cpp
const ll N = 1e5 + 5;
int tree[4 * N];

// Here we are using 1 based indexing

void build(vector<int> arr, int current_node, int left_end, int right_end)
{
    // If the current node is a leaf node then store the value of the array at that index
    if (left_end == right_end)
        tree[current_node] = arr[left_end];

    else
    {
        int mid = (left_end + right_end) / 2;

        // THESE FORMULAS ARE FOR 1 BASED INDEXING
        int left_node = current_node * 2;
        int right_node = current_node * 2 + 1;

        build(arr, left_node, left_end, mid);                        // Build the left subtree
        build(arr, right_node, mid + 1, right_end);                  // Build the right subtree
        tree[current_node] = max(tree[left_node], tree[right_node]); // Update the current node
    }
}

// Query the segment tree for the max elements in range [l, r]
int query(int v, int tl, int tr, int l, int r)
{
    if (l > r) return -1e9;
    if (l == tl && r == tr)
        return tree[v];

    int tm = (tl + tr) / 2;
    return max(query(v * 2, tl, tm, l, min(r, tm)), query(v * 2 + 1, tm + 1, tr, max(l, tm + 1), r));
}
```

# 5 July 2023

## Binary lifting
```
You are given a tree with n nodes numbered from 0 to n - 1 in the form of a parent array parent where parent[i] is the parent of ith node. The root of the tree is node 0. Find the kth ancestor of a given node. 
```
### [Kth Ancestor of a Tree Node](https://leetcode.com/problems/kth-ancestor-of-a-tree-node/)

```
1. Solving approach
Well the first thing I could asume was that I could easily run a dfs to the parent bu again there ar Q queries so doing brute force will just give me cute tle . Now big bro Errichto came to enlighten me with his concept of binary lifting . 

19 -> 10011 so we can basically get 19 by adding up 16+2+1 . in the same way we can just do jumps in power of two to reach that level of anecstor now this wil always be possible because every number can be represented as a sum of power of two . 

So for that each bit that is turned on we will jump upto that level if that is possible. This idea of jumping from one node two another node in power of two is known as binary lifting.

So to do binary lifting we will have to pre process the tree and store the 2^i th ancestor of each node in a dp array . Then we can just jump to the kth ancestor of a node by using the dp array.


```

```cpp
class TreeAncestor {

    vector < vector <int>> up;
    vector < int > depth;
    int LOG  = 20;
public:
    TreeAncestor(int n, vector<int>& parent) {
         
          up = vector < vector <int >> (n , vector<int>(LOG));
          depth = vector <int>(n);
      
          parent[0] = 0;

        // finding the parent of node v and keeping it in the first indice
          for (int i = 0 ; i < n ; i++) up[i][0] = parent[i];

          for (int i= 0 ; i < 100 ;i++)
            {
                for(int j = 1; j < n ; j++)
                    depth[j] = depth[parent[j]] +1;
            }

          for (int j  = 1 ; j  < LOG ; j++)
          {
              // counting rest of the possible jumps from that point in the power of 2 2^1 , 2^2 , 2^2
             
              for (int i = 0 ; i < n  ; i++){
                 up[i][j] = up [ up[i][j-1] ] [j-1];
               } 

          }

    }
  
    
    int getKthAncestor(int node, int k) {
        if (depth[node] < k) 
            return -1;

        for (int i = 0 ; i < LOG ;i++)
        {
            if (k &(1<<i))
                node = up[node][i];
        }

        return node;
    }
};
```
### TLE solution

[Kuriyama Mirai's Stones](https://codeforces.com/contest/433/submission/212149836) This submission has only one issue instead of passing reference to the vector in the function I was passing the whole vector which was basicaly copying the whole vector that took some additional time and gave me tle . 
```
ALWAYS TRY TO PASS REFERENCE TO A FUNCTION INSTEAD OF PASSING THE WHOLE VECTOR
```


# 6 July 2023



## XOR properties
```
1. XOR of a number with itself is 0
2. XOR of a number with 0 is the number itself
3. XOR is commutative and associative
4. XOR of a even number and successive odd number is always 1
5. As xor of two same number is zero this property can be used to find the missing number in an array if it is said that all number comes in pair except one
6. As xor from 1 to n can be found using constant time this property can be used to find xor in a given consecutive range
```
## Finding missing number from an array using xor
<details>
<summary> code </summary>

```cpp
// problem link https://www.spoj.com/problems/OLOLO/en/
#include <bits/stdc++.h>
using namespace std;

int32_t main()
{

    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    int n ,ans = 0, x = 0;
    
    cin >> n;

    // here x = 0 as xor of a number with 0 is the number itself

    for (int i = 0; i < n; i++)
    {
        cin >> x;
        // finding xor of the array
        ans ^= x;
    }

    // why this ? its done in consant space and time complexity
    /*
    test case  :
        7
        2 4 6 4 2 2 2

        output : 6

        2^4^6^4^2^2^2 = 6

        we can get a better view if we sort them  just to understand it 

        2 2 2 2 4 4 6

        so we can see that 2 and 4 comes in pair but 6 is left alone so we can find it using xor

        in binary  they are 

        010
        010
        010
        010
        100
        100 --> upto this level we can see that they are coming in pair so we can just xor them and get 0
        110

    */

    cout << ans << endl;
    return 0;
}
```

</details>


## Finding XOR in range 0< l <= r <= 1e12
<details>
<summary> Code  </summary>
    
```cpp
// https://atcoder.jp/contests/abc121/tasks/abc121_d?lang=en
ll xor0toN(ll n)
{
    ll ans = 0;
    while (n >= 0 and n % 4 != 3)
    {
        ans ^= n;
        n--;
    }
    return ans;
}

ll xor_l_to_r(ll l, ll r)
{
    return ((l > 0 ? xor0toN(l - 1) : 0) ^ xor0toN(r));
}

/* the idea is to find xor from 0 to l-1 and xor from 0 to r and then xor them to get the xor from l to r

now the question is how to find xor from 0 to n in constant time as it can be in worst case 1e12
we can observe a pattern here that

we can observe an pattern here that

1^2 =1  3^4= 1  5^6 = 1 7^8 = 1

so it is basically XOR of an even and successive odd number is always 1 . now we can look a bit deeper

[(1^2 =1)  ^ (3^4= 1) = 0 ]  [(5^6 = 1) ^ (7^8 = 1) = 0] so for each 4 block we are getting 0 now we gotta find the last block which is not 4 
so for that we are iterating backword till we hit the end of the last block end because then we know when the block ends it will always be 0 . so we can just xor the last block with the block before it and get the answer

A detailed explanation can be found in 
https://www.geeksforgeeks.org/find-xor-of-numbers-from-the-range-l-r/

 */


```
</details>


```
1. To find sum in a range in an constant array we can use prefix sum array to find sum from l to r in constant time we can just do prefix[r] - prefix[l-1] to get the sum in that range the code must handle the case of l = 0 as prefix[-1] will give error

2. Passing reference to a function instead of passing the whole vector can save a lot of time and space as passing the whole vector will copy the whole vector and that will take a lot of time and space

3. Right shift operator can be used to divide a number by 2 as it is faster than dividing it by 2

4. Left shift operator can be used to multiply a number by 2 as it is faster than multiplying it by 2

5.Using next_permutation() we can find the next permutation of a string or a vector in lexicographically order


```

## Given an integer N . Find the number of digits in N in the base k
<details>
<summary> Solution </summary>

```cpp
// https://atcoder.jp/contests/abc156/tasks/abc156_b?lang=en
int main()
{
    int n, k;
    cin >> n >> k;
    cout << floor(log2(n) / log2(k)) + 1 << endl;
    return 0;
}

/*
    the idea is to find the log of n in base k and then add 1 to it to get the number of digits in n in base k
    log(n) base k = log(n) / log(k)
    floor(log(n) base k) + 1 = number of digits in n in base k

    why floor ? because log(n) base k can be a decimal number  wehen n is a power of k or logn is divisble by logk and we need to round it down to get the number of digits  
*/
```
</details>


## KMP
<details>
<summary> Code </summary>

```cpp
VI computeLPSArray(string pat, VI lps)
{
    int len = 0;
    lps[0] = len;
    int i = 1;

    while (i < pat.size())
    {
        if (pat[len] == pat[i])
            ++len, lps[i] = len, i++;
        else
            len != 0 ? (len = lps[len - 1]) : (lps[i] = len, i++);
    }

    return lps;
}

int KMPSearch(string txt, string pat)
{
    int PAT_SIZE = pat.size();
    int TXT_SIZE = txt.size();

    VI lps(PAT_SIZE, 0);

    lps = computeLPSArray(pat, lps);

    int count = 0;

    int i = 0;
    int j = 0;
    while ((TXT_SIZE - i) >= (PAT_SIZE - j))
    {
        if (pat[j] == txt[i])
        {
            j++;
            i++;
        }

        if (j == PAT_SIZE)
        {
            count++;
            j = lps[j - 1];
        }

        else if (i < TXT_SIZE && pat[j] != txt[i])
        {
            if (j != 0)
                j = lps[j - 1];
            else
                i++;
        }
    }

    return count;
}
```
</details>

## RABIN KARP
<details>
<summary> Code </summary>

```cpp

ll hashValue(char c)
{
    return ((c - 'a' + 1) * 7);
}

int RABIN_KARP(string text, string pat)
{

    ll desiredHash = 0, currentHash = 0;

    int M = pat.size();
    int N = text.size();

    for (int i = 0; i < M; i++)
        desiredHash += hashValue(pat[i]);

    for (int i = 0; i < M; i++)
        currentHash += hashValue(text[i]);

    int i = 1;

    int count = 0;
    string ans = text.substr(i - 1, M);
    while (i <= (N - M + 1))
    {

        if (currentHash == desiredHash && ans == pat)
            count++;

        currentHash -= hashValue(text[i - 1]);
        currentHash += hashValue(text[i + M - 1]);
        ans.erase(ans.begin());
        ans += text[i + M - 1];

        i++;
    }

    return count;
}
```
</details>
# 7 July 2023
## Random facts 
```
1. 1!  = 1 , 2! = 2 , 3! = 6 , 4! = 24 , 5! = 120 , 6! = 720  from now on each factorial will end with 0 and if when such a case arrive after that each factorial will have a 0 at the end we can use this property to find out b! / a! where b > a and 0<= a <= b <= 1e18 .  We can optimize it a bit considering the fact that to calculate b! / a! we can just calculate (b * b-1 * b-2 ... a+1) [problem](https://codeforces.com/contest/869/submission/212370670)
```

# 8 July 2023

Well saw some videos about dynamic programming from luv and there he discussed about some problems. The main thing i captured was the defination of dp I can go top to bottom or I can go bottom to top. <br>
now in top to bottom we mainly use recursion and we try to decompose the main problem into some simmilar smaller problems. Now while we are claculating a problem we try to store that in a place so that the repetative work gets cancelled out.so that we can just focus on new things. 
consider it with an example.  Suppose you are a traveller and now are travelling to sikkim so for the first time when you will be going there you will obviously not know where to start from or how to get there so you ask a lot of queztion to everyone and finally create a map and list of info about the details and you complete a happy sikkim trip. 
now after a year you are agin going to sikkim. Now what will happen? If you are not an dummy traveller like me you have probably listed all the details about your previous trip and you are ready to go.  However if you did not then you would have to do the same processs again to gather information. So we memorize things or steps and try not to repeat same things twice. This thing in prohramming can be
 reffered as memoization that you memorize a certain things. 

Now you need to go to sikkim but you have again forgot the route. But you havent forgotten the full details you know how to go to shiliguri from dhaka. won't you use this information? just because you dont know the whole route?  Well you will and you should use as much previous knowledge as possible to do less things and do nee things only when required.  so once you arrive shiliguri you can just do a little bit of work to go to shiliguri. In such way we can use dynamic programming. So that's easy? He He easy to say easy to code, tough to understand the problem! best of luck!

# 9 July 2023
learned nothing new saw some podcasts of errichto and mock interview related question from youtube 


# 10 July 2023
Another unproductive day with no real progress
## Random Facts
```
1. Bishop move is only valid if `(abs(x - i) == abs(y - j) && abs(y - j) > 0)` . In some cases this can be furthre modified to `(abs(x - i) == abs(y - j) && abs(y - j) >= 0)` which means that the current place of the bishop is also countable . Else it will be valid only if  a bishop is traveling from (x1,y1) to (x2,y2)
.This move is legal on an empty board if you have that: |x2−x1|=|y2−y1|>0 
You can find more about this from here https://math.stackexchange.com/questions/1566115/formula-that-describes-the-movement-of-a-bishop-in-chess
Sample code is given below
```
<details>
    <summary> From a place x ,y all posssible moves value of a bishop including the current place </summary>
```cpp
// https://codeforces.com/contest/1676/problem/D
ll getVal(int x , int y , vector <vector<int>> &v)
{
    ll ans = 0;
    rep(0 , v.size())
    {
        for (int j = 0 ; j < v[i].size() ; j++)
        {
            abs(x - i) == abs(y - j) && abs(y - j) >= 0 ? ans += v[i][j] : ans += 0;
        }
    }
    return ans;
}

```
</details>

# Fibonacci Sequence
![Fibonacci Sequence](https://images.immediate.co.uk/production/volatile/sites/4/2022/02/The-Fibonacci-Spiral-ea38c86-e1643912587486.jpg?quality=90&webp=true&resize=1800,1151)

$$Fibonacci Sequence$$
---
To find the **nth** term in ***Fibonacci sequence*** with **c++** we can use several methods:

 - **Recursion**
 - **Dynamic Programming**
 - **Space Optimized Method 2**
 - **Using Binet’s formula**
 - **Using power of the matrix {{1, 1}, {1, 0}}**
 - **Optimized Method 1 (Recursion with Memoization)**
---
---
## The 1st Method (Recursion): 
 **The code:**

        #include<iostream>
    using namespace std;
    
    int Fib(int n)
    {
        if (n <= 1)
        {
            return n;
        }
        else
        {
            return Fib(n-1) + Fib(n-2);
        }
    }
    
    int main ()
    {
        int n;
        cin >> n;
        cout << "The " << n << "th number in Fibonacci sequence is " << Fib(n);
        return 0;
    }
  

---
### Time and space complexity:
---
 - **Time Complexity: Exponential,**  as every function calls two other functions. If the original recursion tree were to be implemented then this would have been the tree but now for n times the recursion function is called **Original tree for recursion**. O( $2^{n}$ ).

 - **Extra Space:** O(n) if we consider the function call stack size, otherwise O(1).
---
---
---
## The 2nd Method (Dynamic Programming): 
**The code:**

    #include<iostream>
    using namespace std;
    
    int Fib(int n)
    {
        int F[n+1];
        F[0]=0;
        F[1]=1;
        for (int i=2; i<=n; i++)
        {
          F[i] = F[i-1] + F[i-2];
        }
        return F[n];
    }
    
    int main ()
    {
    	int n;
    	cin >> n;
    	cout << "The " << n << "th number in Fibonacci sequence is " << Fib(n);
    	return 0;
    }
---
### Time and space complexity:
---

 - **Time complexity**: O(n) for given n.
 - **Auxiliary space**: O(n).
---
---
---
## The 3rd Method (Space Optimized Method 2): 
**The code:**

    #include<iostream>
    using namespace std;
    
    int fib(int n)
    {
        int a = 0, b = 1, c, i;
        if( n == 0)
            {
            return a;
            }
        for(i = 2; i <= n; i++)
        {
           c = a + b;
           a = b;
           b = c;
        }
            return b;
    }
    
    int main()
    {
        int n;
        cin >> n;
        cout << "The " << n << "th number in Fibonacci sequence is " << fib(n);
        return 0;
    }
---
### Time and space complexity:
---

 - **Time Complexity:**  O(n).
 - **Extra Space:**  O(1).
---
---
---
## The 4th Method ( Binet’s formula): 
 $$Binet’s formula$$
$$F_{n} =([[sqrt(5)+1]/2]^n)/sqrt(5)$$
**The code:**

    #include<iostream>
    #include<cmath>
    using namespace std;
    
    int Fib(int n)
    {
        double x;
        x = (1+sqrt(5)) / 2;
        x = pow(x,n) / sqrt(5);
        return round(x);
    }
    
    int main()
    {
        int n;
        cin >> n;
        cout << Fib(n);
        return 0;
    }
---
### Time and space complexity:
---

 - **Time Complexity:** O(log(n)), this is because calculating $x^{n}$  takes log(n) time.
 - **Auxiliary Space:** O(1).
---
---
---
## The 5th Method ( Using power of the matrix {{1, 1}, {1, 0}}):


**The code:**

    #include<iostream>
    using namespace std;
    
    
    void multiply(int F[2][2], int M[2][2]);
    void power(int F[2][2], int n);
    
    
    int fib(int n)
    {
        int F[2][2] = { { 1, 1 }, { 1, 0 } };
    
        if (n == 0)
            return 0;
    
        power(F, n - 1);
    
        return F[0][0];
    }
    
    void multiply(int F[2][2], int M[2][2])
    {
        int x = F[0][0] * M[0][0] +
                F[0][1] * M[1][0];
        int y = F[0][0] * M[0][1] +
                F[0][1] * M[1][1];
        int z = F[1][0] * M[0][0] +
                F[1][1] * M[1][0];
        int w = F[1][0] * M[0][1] +
                F[1][1] * M[1][1];
    
        F[0][0] = x;
        F[0][1] = y;
        F[1][0] = z;
        F[1][1] = w;
    }
    
    void power(int F[2][2], int n)
    {
        int i;
        int M[2][2] = { { 1, 1 }, { 1, 0 } };
    
        for(i = 2; i <= n; i++)
            multiply(F, M);
    }
    
    
    int main()
    {
        int n;
    
        cin >> n;
        cout << "The " << n << "th number in Fibonacci sequence is " << fib(n);
    
        return 0;
    }
    
### Time and space complexity:
---

 - **Time Complexity:** O(n).
 - **Extra Space:** O(1).
---
---
---
## The 6th Method ( Optimized Method 1):


**The code:**

    #include <bits/stdc++.h>
    using namespace std;
    int F[100];
    int Fib(int n)
    {
        if (n <= 1)
        {
            return n;
        }
        if (F[n] != -1)
        {
           return F[n];
        }
    
            F[n] = Fib(n-1) + Fib(n-2);
            return F[n];
    }
    
    int main()
    {
    
    for (int i=0; i<101; i++)
    {
        F[i] = -1;
    }
    
    int n;
    
    cin >> n;
    cout << "The " << n << "th number in Fibonacci sequence is " << Fib(n);
        return 0;
    }


---
---
---
## summary:
|The method number |Time complexity|space complexity | 
|--|--------------|-----|
| 1| O( $2^{n}$ ) | O(n)  
| 2| O(n)         | O(n) 
| 3| O(n)         | O(1) 
| 4| O(log(n))    | O(1)
| 5| O(n)         | O(1)
---
---
--- 

## References:

 

 - [geeksforgeeks](https://www.geeksforgeeks.org/program-for-nth-fibonacci-number/)
 - [Memoization code on youtube](https://www.youtube.com/watch?v=UxICsjrdlJA)
 - [my code on the online editor ](https://stackedit.io/app#)
---
---
---
### By:  Arsany Maged Raouf
### Sec: 1
### BN: 7

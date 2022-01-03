# Algorithm


## Question 1

Write a method to generate the $n^{th}$ Fibonacci number


## Solution 

There are three potential approaches: 
* (1) recursive approach 
* (2) iterative approach 
* (3) using matrix math We have described the recursive and iterative approach below, as you would not be expected to be able to derive the matrix-based approach in an interview For the interested math-geeks, you may read about the (most efficient) matrix-based algorithm at
[http://en wikipedia org/wiki/Fibonacci_number#Matrix_form]()



```java
// Recursive Solution:
int fibo(int n) {
    if (n == 0) {
        return 0; // f(0) = 0
    } else if (n == 1) {
        return 1; // f(1) = 1
    } else if (n > 1) {
        return fibo(n-1) + fibo(n-2); // f(n) = f(n—1) + f(n-2)
    } else {
        return –1; // Error condition
    }
}


// Iterative Solution:
int fibo(int n) {
    if (n < 0) return -1; // Error condition.
    if (n == 0) return 0;
    int a = 1, b = 1;

    for (int i = 3; i <= n; i++) {
        int c = a + b;
        a = b;
        b = c;
    }
    return b;
}
```

## Question 1

Implement an algorithm to print all valid (e g , properly opened and closed) combinations of n-pairs of parentheses

EXAMPLE:
* input: 3 (e g , 3 pairs of parentheses)
* output: ()()(), ()(()), (())(), ((()))



### Solution

We can solve this problem recursively by recursing through the string On each iteration, we
have the index for a particular character in the string We need to select either a left or a right
paren When can we use left, and when can we use a right paren?
» Left: As long as we haven’t used up all the left parentheses, we can always insert a left
paren
» Right: We can insert a right paren as long as it won’t lead to a syntax error When will we
get a syntax error? We will get a syntax error if there are more right parentheses than
left
So, we simply keep track of the number of left and right parentheses allowed If there are
left parens remaining, we’ll insert a left paren and recurse If there are more right parens
remaining than left (eg, if there are more left parens used), then we’ll insert a right paren and
recurse






```java
public static void printPar(int l, int r, char[] str, int count) {
    if (l < 0 || r < l) return; // invalid state
    if (l == 0 && r == 0) {
        System.out.println(str); // found one, so print it
    } else {
        if (l > 0) { // try a left paren, if there are some available
            str[count] = '(';
            printPar(l - 1, r, str, count + 1);
        }
        if (r > l) { // try a right paren, if there’s a matching left
            str[count] = ')';
            printPar(l, r - 1, str, count + 1);
        }
    }
}

public static void printPar(int count) {
    char[] str = new char[count*2];
    printPar(count, count, str, 0);
}
```

## Question 3

A child is running up a staircase with n steps and can hop either 1 step, 2 steps, or 3 steps at a time. Implement a method to count how many possible ways the child can run up the stairs.

### Solution

Let's think about this with the following question: What is the very last step that is done ?
The very last hop the child makes-the one that lands her on the nth step-was either a 3-step hop, a 2-step hop, or a 1-step hop.
How many ways then are there to get up to the nth step? We don't know yet, but we can relate it to some subproblems.
If we thought about all of the paths to the nth step, we could just build them off the paths to the three
previous steps. We can get up to the nth step by any of the following:
* Going to the $(n - l)^{st}$ step and hopping 1 step.
* Going to the $(n - 2)^{nd}$ step and hopping 2 steps.
* Going to the $(n - 3)^{rd}$ step and hopping3 steps.

Therefore, we just need to add the number of these paths together.

Be very careful here. A lot of people want to multiply them. Multiplying one path with another would signify
taking one path and then taking the other. That's not what's happening here



**Brute Force Solution**

This is a fairly straightforward algorithm to implement recursively. We just need to follow logic like this:
$countWays(n-1) + countWays(n-2) + countWays(n-3)$

The one tricky bit is defining the base case. If we haveO steps to go (we're currently standing on the step),
are there zero paths to that step or one path?
That is, what is c ountWays(0)? Is it 1 orO?
You could define it either way. There is no"right" answer here.
However, it's a lot easier to define it as 1. If you defined it as 0, then you would need some additional base
cases (or else you'd just wind up with a series ofOs getting added).




```java
// A simple implementation of this code is below.
int countWays(int n) {
    if (n < 0) {
        return 0;
    } else if (n == 0) {
        return 1;
    } else {
        return countWays(n-1) + countWays(n-2) + countWays(n-3);
    }
}
```
Like the Fibonacci problem, the runtime of this algorithm is exponential (roughly O ( $3^n$ ) ), since each call branches out to three more calls.
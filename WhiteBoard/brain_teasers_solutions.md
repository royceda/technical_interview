# Brain Teasers


## Question 1

Write a function to swap a number in place without temporary variables

```java
public static void swap(int a, int b) {
    a = b - a; // 9 - 5 = 4
    b = b - a; // 9 - 4 = 5
    a = a + b; // 4 + 5 = 9

    System.out.println("a: " + a);
    System.out.println("b: " + b);
}

// You can then optimize it as follows:
public static void swap_opt(int a, int b) {
    a = a^b;
    b = a^b;
    a = a^b;

    System.out.println("a: " + a);
    System.out.println("b: " + b);
}
```


## Question 2

Add arithmetic operators (plus, minus, times, divide) to make the following expres-
sion true: 3 1 3 6 = 8 You can use any parentheses you’d like


(The main goal is not to trap the canditate, but to see is his approach of unknown problems)


**A possible Solution** 

```
thinking randomly is not good approach

[CLUE] 
Try approaching this the following way: What sorts of operations would get us to 8? 

I can think of a few:
4 * 2 = 8
16 / 2 = 8
4 + 4 = 8

Let’s start with the first one Is there any way to make 3 1 3 6 produce 4 * 2? 
We can easily notice that 3 + 1 = 4 (the first two numbers) 
We can also notice that 6 / 3 = 2 If we had “3 1 6 3”, 
we’d be done, since (3 + 1)*(6 / 3) = 8 Although it seems a little unconventional to do this, we can, in fact, just flip the 6 and the 3 to get the solution:


(( 3 + 1 ) / 3) * 6 = 8

```


## Question 3

There is a building of 100 floors.
If an egg drops from the Nth floor or above it will break. If it’s dropped from any floor below, it will not break. You’re given 2 eggs 
Find N, while minimizing the number of drops for the worst case.


```md
Observation: Regardless of how we drop Egg1, Egg2 must do a linear search i e , if Egg1
breaks between floor 10 and 15, we have to check every floor in between with the Egg2

The Approach:
A First Try: Suppose we drop an egg from the 10th floor, then the 20th, ...
* If the first egg breaks on the first drop (Floor 10), then we have at most 10 drops total
* If the first egg breaks on the last drop (Floor 100), then we have at most 19 drops total
(floors 10, 20, ,90, 100, then 91 through 99)
* That’s pretty good, but all we’ve considered is the absolute worst case We should do
some “load balancing” to make those two cases more even
Goal: Create a system for dropping Egg1 so that the most drops required is consistent,
whether Egg1 breaks on the first drop or the last drop

1 A perfectly load balanced system would be one in which Drops of Egg1 + Drops of
Egg2 is always the same, regardless of where Egg1 broke

2 For that to be the case, since each drop of Egg1 takes one more step, Egg2 is allowed
one fewer step

3 We must, therefore, reduce the number of steps potentially required by Egg2 by one
drop each time For example, if Egg1 is dropped on Floor 20 and then Floor 30, Egg2
is potentially required to take 9 steps When we drop Egg1 again, we must reduce
potential Egg2 steps to only 8 That is, we must drop Egg1 at floor 39
4 We know, therefore, Egg1 must start at Floor X, then go up by X-1 floors, then X-2, ...,
until it gets to 100

5 Solve for X+(X-1)+(X-2)+...+1 = 100 X(X+1)/2 = 100 -> X = 14
We go to Floor 14, then 27, then 39, ... This takes 14 steps maximum


Another approach, integer programming
```


## Question 4

Write a method which finds the maximum of two numbers You should not use if-else
or any other comparison operator
EXAMPLE
Input: 5, 10
Output: 10

```java
// Let’s try to solve this by “re-wording” the problem We will re-word the problem until we get
// something that has removed all if statements
// Rewording 1: If a > b, return a; else, return b
// Rewording 2: If (a - b) is negative, return b; else, return a
// Rewording 3: If (a - b) is negative, let k = 1; else, let k = 0 Return a - k * (a - b)
// Rewording 4: Let c = a - b 
// (Tricks) Let k = the most significant bit of c Return a - k * c
// We have now reworded the problem into something that fits the requirements The code
// for this is below

int getMax(int a, int b) {
    int c = a - b;
    int k = (c >> 31) & 0x1; // 0x1 is a hex value of 1.
    int max = a - k * c;
    return max;
}
```
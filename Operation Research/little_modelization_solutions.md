# Modelization_easy


## Marathon 

Dominique, Ignace, Naren, Olivier, Philippe, and Pascal
have arrived as the first six at the Paris marathon.
Reconstruct their arrival order from the following
information:
* a) Olivier has not arrived last
* b) Dominique, Pascal and Ignace have arrived before Naren
    and Olivier
* c) Dominique who was third last year has improved this year.
* d) Philippe is among the first four.
* e) Ignace has arrived neither in second nor third position.
* f) Pascal has beaten Naren by three positions.
* g) Neither Ignace nor Dominique are on the fourth position.

### Solution

```
Places:
1: Ignace
2: Dominique
3: Pascal
4: Philippe
5: Olivier
6: Naren
```


## Diet 

Minimize the cost for the products:
| Type of Food                   | Calories   |Chocolate (ounces)   |Sugar (ounces)    |Fat (ounces) | Price (cents) |
|---                             |---         |---          |---      |--  |---    |
| Chocolate Cake (1 slice)       | 400           |3         |2        |2   | 50 |
| Chocolate ice cream (1 scoop)  | 200           |2         |2        |4   | 20 |
| Cola (1 bottle)                | 150           |0         |4        |1   | 30 |
| Pineapple cheesecake (1 piece) | 500           |0         |4        |5   | 80 |



limits for each nutritments :
* Calories 500
* Chocolate 6
* Sugar 100
* fat 8


### Solution

$x_i \in [0, 100] \forall i$

minimize


```
Solver:  CBC
Cost: 90.0
[0, 3, 1, 0]

WallTime: 6
iterations: 0
```



## Chemical Balance 

We are trying to group items in equal sized groups.
Each item has a color and a value. We want the sum of values of each group to
be as close to the average as possible.
Furthermore, if one color is an a group, at least k items with this color must
be in that group.


### Solution

```
Number of variables = 6
Number of constraints = 14
Problem solved in 3.000000 milliseconds
Optimal objective value = 624.873708
  A = 1.542826 
  B = 2.635459 
  C = 0.000000 
  D = 0.000000 
  E = 6.432662 
N_Total: 1319.126292 out of 1944.000000
P2O5: 1016.360517 out of 1166.400000
K2O: 1822.500000 out of 1822.500000
CaO: 833.126292 out of 1458.000000
MgO: 486.000000 out of 486.000000
Fe: 6.432662 out of 9.700000
B: 1.286532 out of 2.400000
```

## Bus Schedule 


### Solution

```
Check for minimun number of buses
x: [0, 8, 2, 5, 7, 4]  num_buses: 26

num_solutions: 1
failures: 28
branches: 51
WallTime: 3

... got  26 buses
All solutions:
x: [0, 8, 2, 5, 7, 4]  num_buses: 26
x: [0, 8, 2, 6, 6, 4]  num_buses: 26
x: [0, 8, 2, 7, 5, 4]  num_buses: 26
x: [0, 8, 2, 8, 4, 4]  num_buses: 26
x: [0, 8, 2, 9, 3, 4]  num_buses: 26
x: [0, 8, 2, 10, 2, 4]  num_buses: 26
x: [0, 8, 2, 11, 1, 4]  num_buses: 26
x: [0, 8, 2, 12, 0, 4]  num_buses: 26
x: [0, 9, 1, 6, 6, 4]  num_buses: 26
x: [0, 9, 1, 7, 5, 4]  num_buses: 26
x: [0, 9, 1, 8, 4, 4]  num_buses: 26
x: [0, 9, 1, 9, 3, 4]  num_buses: 26
x: [0, 9, 1, 10, 2, 4]  num_buses: 26
x: [0, 9, 1, 11, 1, 4]  num_buses: 26
x: [0, 9, 1, 12, 0, 4]  num_buses: 26
x: [0, 10, 0, 7, 5, 4]  num_buses: 26
x: [0, 10, 0, 8, 4, 4]  num_buses: 26
x: [0, 10, 0, 9, 3, 4]  num_buses: 26
x: [0, 10, 0, 10, 2, 4]  num_buses: 26
x: [0, 10, 0, 11, 1, 4]  num_buses: 26
x: [0, 10, 0, 12, 0, 4]  num_buses: 26
x: [1, 7, 3, 4, 8, 3]  num_buses: 26
x: [1, 7, 3, 5, 7, 3]  num_buses: 26
x: [1, 7, 3, 6, 6, 3]  num_buses: 26
x: [1, 7, 3, 7, 5, 3]  num_buses: 26
x: [1, 7, 3, 8, 4, 3]  num_buses: 26
x: [1, 7, 3, 9, 3, 3]  num_buses: 26
x: [1, 7, 3, 10, 2, 3]  num_buses: 26
x: [1, 7, 3, 11, 1, 3]  num_buses: 26
x: [1, 8, 2, 5, 7, 3]  num_buses: 26
x: [1, 8, 2, 6, 6, 3]  num_buses: 26
x: [1, 8, 2, 7, 5, 3]  num_buses: 26
x: [1, 8, 2, 8, 4, 3]  num_buses: 26
x: [1, 8, 2, 9, 3, 3]  num_buses: 26
x: [1, 8, 2, 10, 2, 3]  num_buses: 26
x: [1, 8, 2, 11, 1, 3]  num_buses: 26
x: [1, 9, 1, 6, 6, 3]  num_buses: 26
x: [1, 9, 1, 7, 5, 3]  num_buses: 26
x: [1, 9, 1, 8, 4, 3]  num_buses: 26
x: [1, 9, 1, 9, 3, 3]  num_buses: 26
x: [1, 9, 1, 10, 2, 3]  num_buses: 26
x: [1, 9, 1, 11, 1, 3]  num_buses: 26
x: [1, 10, 0, 7, 5, 3]  num_buses: 26
x: [1, 10, 0, 8, 4, 3]  num_buses: 26
x: [1, 10, 0, 9, 3, 3]  num_buses: 26
x: [1, 10, 0, 10, 2, 3]  num_buses: 26
x: [1, 10, 0, 11, 1, 3]  num_buses: 26
x: [2, 6, 4, 3, 9, 2]  num_buses: 26
x: [2, 6, 4, 4, 8, 2]  num_buses: 26
x: [2, 6, 4, 5, 7, 2]  num_buses: 26
x: [2, 6, 4, 6, 6, 2]  num_buses: 26
x: [2, 6, 4, 7, 5, 2]  num_buses: 26
x: [2, 6, 4, 8, 4, 2]  num_buses: 26
x: [2, 6, 4, 9, 3, 2]  num_buses: 26
x: [2, 6, 4, 10, 2, 2]  num_buses: 26
x: [2, 7, 3, 4, 8, 2]  num_buses: 26
x: [2, 7, 3, 5, 7, 2]  num_buses: 26
x: [2, 7, 3, 6, 6, 2]  num_buses: 26
x: [2, 7, 3, 7, 5, 2]  num_buses: 26
x: [2, 7, 3, 8, 4, 2]  num_buses: 26
x: [2, 7, 3, 9, 3, 2]  num_buses: 26
x: [2, 7, 3, 10, 2, 2]  num_buses: 26
x: [2, 8, 2, 5, 7, 2]  num_buses: 26
x: [2, 8, 2, 6, 6, 2]  num_buses: 26
x: [2, 8, 2, 7, 5, 2]  num_buses: 26
x: [2, 8, 2, 8, 4, 2]  num_buses: 26
x: [2, 8, 2, 9, 3, 2]  num_buses: 26
x: [2, 8, 2, 10, 2, 2]  num_buses: 26
x: [2, 9, 1, 6, 6, 2]  num_buses: 26
x: [2, 9, 1, 7, 5, 2]  num_buses: 26
x: [2, 9, 1, 8, 4, 2]  num_buses: 26
x: [2, 9, 1, 9, 3, 2]  num_buses: 26
x: [2, 9, 1, 10, 2, 2]  num_buses: 26
x: [2, 10, 0, 7, 5, 2]  num_buses: 26
x: [2, 10, 0, 8, 4, 2]  num_buses: 26
x: [2, 10, 0, 9, 3, 2]  num_buses: 26
x: [2, 10, 0, 10, 2, 2]  num_buses: 26
x: [3, 5, 5, 2, 10, 1]  num_buses: 26
x: [3, 5, 5, 3, 9, 1]  num_buses: 26
x: [3, 5, 5, 4, 8, 1]  num_buses: 26
x: [3, 5, 5, 5, 7, 1]  num_buses: 26
x: [3, 5, 5, 6, 6, 1]  num_buses: 26
x: [3, 5, 5, 7, 5, 1]  num_buses: 26
x: [3, 5, 5, 8, 4, 1]  num_buses: 26
x: [3, 5, 5, 9, 3, 1]  num_buses: 26
x: [3, 6, 4, 3, 9, 1]  num_buses: 26
x: [3, 6, 4, 4, 8, 1]  num_buses: 26
x: [3, 6, 4, 5, 7, 1]  num_buses: 26
x: [3, 6, 4, 6, 6, 1]  num_buses: 26
x: [3, 6, 4, 7, 5, 1]  num_buses: 26
x: [3, 6, 4, 8, 4, 1]  num_buses: 26
x: [3, 6, 4, 9, 3, 1]  num_buses: 26
x: [3, 7, 3, 4, 8, 1]  num_buses: 26
x: [3, 7, 3, 5, 7, 1]  num_buses: 26
x: [3, 7, 3, 6, 6, 1]  num_buses: 26
x: [3, 7, 3, 7, 5, 1]  num_buses: 26
x: [3, 7, 3, 8, 4, 1]  num_buses: 26
x: [3, 7, 3, 9, 3, 1]  num_buses: 26
x: [3, 8, 2, 5, 7, 1]  num_buses: 26
x: [3, 8, 2, 6, 6, 1]  num_buses: 26
x: [3, 8, 2, 7, 5, 1]  num_buses: 26
x: [3, 8, 2, 8, 4, 1]  num_buses: 26
x: [3, 8, 2, 9, 3, 1]  num_buses: 26
x: [3, 9, 1, 6, 6, 1]  num_buses: 26
x: [3, 9, 1, 7, 5, 1]  num_buses: 26
x: [3, 9, 1, 8, 4, 1]  num_buses: 26
x: [3, 9, 1, 9, 3, 1]  num_buses: 26
x: [3, 10, 0, 7, 5, 1]  num_buses: 26
x: [3, 10, 0, 8, 4, 1]  num_buses: 26
x: [3, 10, 0, 9, 3, 1]  num_buses: 26
x: [4, 4, 6, 1, 11, 0]  num_buses: 26
x: [4, 4, 6, 2, 10, 0]  num_buses: 26
x: [4, 4, 6, 3, 9, 0]  num_buses: 26
x: [4, 4, 6, 4, 8, 0]  num_buses: 26
x: [4, 4, 6, 5, 7, 0]  num_buses: 26
x: [4, 4, 6, 6, 6, 0]  num_buses: 26
x: [4, 4, 6, 7, 5, 0]  num_buses: 26
x: [4, 4, 6, 8, 4, 0]  num_buses: 26
x: [4, 5, 5, 2, 10, 0]  num_buses: 26
x: [4, 5, 5, 3, 9, 0]  num_buses: 26
x: [4, 5, 5, 4, 8, 0]  num_buses: 26
x: [4, 5, 5, 5, 7, 0]  num_buses: 26
x: [4, 5, 5, 6, 6, 0]  num_buses: 26
x: [4, 5, 5, 7, 5, 0]  num_buses: 26
x: [4, 5, 5, 8, 4, 0]  num_buses: 26
x: [4, 6, 4, 3, 9, 0]  num_buses: 26
x: [4, 6, 4, 4, 8, 0]  num_buses: 26
x: [4, 6, 4, 5, 7, 0]  num_buses: 26
x: [4, 6, 4, 6, 6, 0]  num_buses: 26
x: [4, 6, 4, 7, 5, 0]  num_buses: 26
x: [4, 6, 4, 8, 4, 0]  num_buses: 26
x: [4, 7, 3, 4, 8, 0]  num_buses: 26
x: [4, 7, 3, 5, 7, 0]  num_buses: 26
x: [4, 7, 3, 6, 6, 0]  num_buses: 26
x: [4, 7, 3, 7, 5, 0]  num_buses: 26
x: [4, 7, 3, 8, 4, 0]  num_buses: 26
x: [4, 8, 2, 5, 7, 0]  num_buses: 26
x: [4, 8, 2, 6, 6, 0]  num_buses: 26
x: [4, 8, 2, 7, 5, 0]  num_buses: 26
x: [4, 8, 2, 8, 4, 0]  num_buses: 26
x: [4, 9, 1, 6, 6, 0]  num_buses: 26
x: [4, 9, 1, 7, 5, 0]  num_buses: 26
x: [4, 9, 1, 8, 4, 0]  num_buses: 26
x: [4, 10, 0, 7, 5, 0]  num_buses: 26
x: [4, 10, 0, 8, 4, 0]  num_buses: 26

num_solutions: 145
failures: 175
branches: 348
WallTime: 33
```

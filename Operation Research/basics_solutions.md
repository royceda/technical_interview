# Operation Research (Basic)


## Question 1

Give at least 3 basics problems of Operations Research?


### Solution 

* bin packing
* Knapsack
* TSP / CVRP
* Lot Sizing
* localization problem
* Cover


## Question 2

Explain quickly at least 2 resolution methods for Knapsack problem and their complexities ?

### Solution 

* Dynamic programming 
* Branch and bound
* Integer programming (but solved by solver which uses advanced branch and bound)

## Question 3

Define the bin packing problem and describe a method to solve bin packing problem without a solver ?

HARD : Apply lagrandian relaxation on this problem and explain why it will be easier to solve it? 

### Solution
* branch and bound by using a lower bound . got thanks to an heuristic
* Lagragian relaxation by getting a problem similar to Knapsack. A unique constraint will remain to the sub problem.


A possible [[Integer programming|integer linear programming]] formulation of the problem is:

***

minimize $ \sum_{j=1}^n y_j$

subject to:

(1) $\sum_{i \in I}^n s(i) x_{ij} \leq B y_j,$ $\forall j \in \{1,\ldots,n\}$

(2) $\sum_{j=1}^n x_{ij} = 1,$ $\forall i \in I$

$ y_j \in \{0,1\},$
$\forall j \in \{1,\ldots,n\}$

$ x_{ij} \in \{0,1\},$
$\forall i \in I \, \forall j \in \{1,\ldots,n\}$

where 
* $ y_j = 1$ if bin $j$ is used
* $ x_{ij} = 1$ if item $i$ is put into bin $j$
* $s(i)$ size of item $i$
* $B$ bin capacity


## Question 4

Explain duality concept. Why is it useful ?


### Solution 

useful : 
* get interesting bounds (lower bounds)
* proof of optimality ( Strong duality theorem)

**Primal**

minimize $c^T . x$

subject to :

$A.x \ge b$

$x \ge 0$
___

***transformation***

if $x^∗$ optimal, $y^T Ax$ is a general
linear combination of equations, if we can select y so
that

$y^T A.x^* = c^T.x^*$ and $c^T.x^* \ge y^T.b$


the best lower bound for any x

maximize $b^T . y$

subject to :

$A^T.y = c$

$y \ge 0$

____
**Dual**

maximize $b^T . y$

subject to :

$A^T.y \le c$

$y \ge 0$

___


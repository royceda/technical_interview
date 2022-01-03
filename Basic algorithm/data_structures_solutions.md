# Data Structures

# I. Array

## Question 1

Write a method to decide if two strings are anagrams or not

### Solution 

```java
// Solution #1: Sort the strings
boolean anagram(String s, String t) {
    return sort(s) == sort(t);
}


// Solution #2: Check if the two strings have identical counts for each unique char.
public static boolean anagram(String s, String t) {
    if (s.length() != t.length()) return false;
    int[] letters = new int[256];
    int num_unique_chars = 0;
    int num_completed_t = 0;
    char[] s_array = s.toCharArray();
    
    for (char c : s_array) { // count number of each char in s.
        if (letters[c] == 0) ++num_unique_chars;
        ++letters[c];
    }
    for (int i = 0; i < t.length(); ++i) {
        int c = (int) t.charAt(i);
        if (letters[c] == 0) { // Found more of char c in t than in s.
            return false;
        }

        --letters[c];
        if (letters[c] == 0) {
            ++num_completed_t;
            if (num_completed_t == num_unique_chars) {
                // it’s a match if t has been processed completely
                return i == t.length() - 1;
            }
        }
    }
    return false;
}
```

# II. Linked List


## Question 2

Design a linked list (C++ / Java or pseudo code) with a method you wish among delete_element, add_element or update_element

```java
// An example
class Node {
    Node next = null;
    int data;
    public Node(int d) { data = d; }
    void appendToTail(int d) {
        Node end = new Node(d);
        Node n = this;
        while (n.next != null) { n = n.next; }
        n.next = end;
    }
}


Node deleteNode(Node head, int d) {
    Node n = head;
    if (n.data == d) {
        return head.next; /* moved head */
    }
    while (n.next != null) {
        if (n.next.data == d) {
            n.next = n.next.next;
            return head; /* head didn’t change */
        }
        n = n.next;
    }
}

```

## Question 3

Write code to remove duplicates from an unsorted linked list
FOLLOW UP

(/!\ HARD) How would you solve this problem if a temporary buffer is not allowed?

**Solution :**

```java
// If we can use a buffer, we can keep track of elements in a hashtable and remove any dups:


public static void deleteDups(LinkedListNode n) {
    Hashtable table = new Hashtable();
    LinkedListNode previous = null;
    while (n != null) {
        if (table.containsKey(n.data)) previous.next = n.next;
        else {
            table.put(n.data, true);
            previous = n;
        }
        n = n.next;
    }
}



Without a buffer, we can iterate with two pointers: “current” does a normal iteration, while
“runner” iterates through all prior nodes to check for dups Runner will only see one dup
per node, because if there were multiple duplicates they would have been removed already

public static void deleteDups2(LinkedListNode head) {
    if (head == null) return;
    LinkedListNode previous = head;
    LinkedListNode current = previous.next;
    while (current != null) {
        LinkedListNode runner = head;
        while (runner != current) { // Check for earlier dups
            if (runner.data == current.data) {
                LinkedListNode tmp = current.next; // remove current
                previous.next = tmp;
                current = tmp; // update current to next node
                break; // all other dups have already been removed
            }
        runner = runner.next;
        }
        if (runner == current) { // current not updated - update now
            previous = current;
            current = current.next;
        }
    }
}
```


# III. Stack & Queue

## Question 4

Implement a stack and a queue with their basic methods

```java
class Stack {
    Node top;
    Node pop() {
        if (top != null) {
            Object item = top.data;
            top = top.next;
            return item;
        }
        return null;
    }

    void push(Object item) {
        Node t = new Node(item);
        t.next = top;
        top = t;
    }
}
```


```java
class Queue {
    Node first, last;

    void enqueue(Object item) {
        if (!first) {
            back = new Node(item);
            first = back;
        } else {
            back.next = new Node(item);
            back = back.next;
        }
    }

    Node dequeue(Node n) {
        if (front != null) {
            Object item = front.data;
            front = front.next;
            return item;
        }
        return null;
    }
}

```

## Question 5

Describe how you could use a single array to implement three stacks



**Approach 1:**

Divide the array in three equal parts and allow the individual stack to grow in that limited
space (note: “[“ means inclusive, while “(“ means exclusive of the end point)
* for stack 1, we will use [0, n/3]
* for stack 2, we will use [n/3, 2n/3]
* for stack 3, we will use [2n/3, n]

This solution is based on the assumption that we do not have any extra information about
the usage of space by individual stacks and that we can’t either modify or use any extra
space With these constraints, we are left with no other choice but to divide equal


**Approach 2:**

In this approach, any stack can grow as long as there is any free space in the array
We sequentially allocate space to the stacks and we link new blocks to the previous block
This means any new element in a stack keeps a pointer to the previous top element of that particular stack

In this implementation, we face a problem of unused space For example, if a stack deletes
some of its elements, the deleted elements may not necessarily appear at the end of the ar-
ray So, in that case, we would not be able to use those newly freed spaces.

To overcome this deficiency, we can maintain a free list and the whole array space would be given initially to the free list For every insertion, we would delete an entry from the free list.

In case of deletion, we would simply add the index of the free cell to the free list
In this implementation we would be able to have flexibility in terms of variable space utilization but we would need to increase the space complexity.



# IV. Trees and Graph (Basics)


## Question 6

Describe a Binary Tree methods / find a node / delete a node / other well known algorithm


## Question 7

Describe Graph Taversal methods 

* **Depth First Search**: DFS involves searching a node and all its children before proceeding to its siblings

* **Breadth First Search**: BFS involves searching a node and its siblings before going on to any children
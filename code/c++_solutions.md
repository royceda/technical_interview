#  C++


## Question 1

what do the syntaxes mean ?

```c++
int *p; // Defines pointer.
p = &q; // Sets p to address of q.
v = *p; // Set v to value of q.
Foo *f = new Foo(); // Initializes f.
int k = f->x; // Sets k equal to the value of f’s member variab
```

## Question 2

write a class with an attribute (whatever the type) and a method which updates this attribute.

### Solution

```c++
class MyClass {
    private:
        double var;
    public:
        MyClass(double v) {var = v; }
        ~MyClass() {};
        double Update(double v);
};

double MyClass::Update(double v) {
    var = v; return v;
}
```


## Question 4

What is the differences between a Java and C++ (3 is already excellents) ?

### Solution
* Java runs in a virtual machine
* C++ natively supports unsigned arithmetic
* In Java, parameters are always passed by value (or, with objects, their references are
passed by value) In C++, parameters can be passed by value, pointer, or by reference
* Java has built-in garbage collection
* C++ allows operator overloading
* C++ allows multiple inheritance of classes


## Question 5

How do virtual functions work in C++ ?

### Solution

A virtual function depends on a “vtable”or “Virtual Table” If any function of a class is declared as virtual, a v-table is constructed which stores addresses of the virtual functions of this class.

The compiler also adds a hidden vptr variable in all such classes which points to the vtable of that class. If a virtual function is not overridden in the derived class, the vtable of the derived class stores the address of the function in his parent class The v-table is used to resolve the address of the function, for whenever the virtual function is called Dynamic binding in C++ is therefore performed through the vtable mechanism.

Thus, when we assign the derived class object to the base class pointer, the vptr points to the vtable of the derived class This assignment ensures that the most derived virtual function gets called.

```c++
class Shape {
    private:
        int edge_length;
    public:
        virtual int circumference () {
            cout << “Circumference of Base Class\n”;
            return 0;
        }
};

class Triangle: public Shape {
    public:
        int circumference () {
            cout<< “Circumference of Triangle Class\n”;
            return 3 * edge_length;
        }
};

void main() {
    Shape * x = new Shape();
    x->circumference(); // prints “Circumference of Base Class”
    Shape *y = new Triangle();
    y->circumference(); // prints “Circumference of Triangle Class”
}
```

In the above example, circumference is a virtual function in shape class, so it becomes virtual in each of the derived classes (triangle, rectangle) C++ non-virtual function calls are resolved at compile time with static binding, while virtual function calls are resolved at run time with dynamic binding


## Question 6

Write a smart pointer (smart_ptr) class

### Solution

Smart_ptr is the same as a normal pointer, but it provides safety via automatic memory.

It avoids dangling pointers, memory leaks, allocation failures etc The smart pointer must maintain a single reference count for all instances.


```c++
template <class T> class SmartPointer {
    public:
    SmartPointer(T * ptr) {
        ref = ptr;
        ref_count = (unsigned*)malloc(sizeof(unsigned));
        *ref_count = 1;
    }

    SmartPointer(SmartPointer<T> & sptr) {
        ref = sptr.ref;
        ref_count = sptr.ref_count;
        ++*ref_count;
    }

    SmartPointer<T> & operator=(SmartPointer<T> & sptr) {
        if (this != &sptr) {
            ref = sptr.ref;
            ref_count = sptr.ref_count;
            ++*ref_count;
        }
        return *this;
    }

    ~SmartPointer() {
        --*ref_count;
        if (*ref_count == 0) {
            delete ref;
            free(ref_count);
            ref = NULL;
            ref_count = NULL;
        }
    }

    T getValue() { return *ref; }
    protected:
    T * ref;
    unsigned * ref_count;
};


```
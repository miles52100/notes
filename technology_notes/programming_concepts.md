# Programming Concepts

Documentation on miscellaneous concepts in programming
With particular emphasis on programming theory - being 
agnostic to any particular language.

## static variables

The computer science bit

    A `static variable` is a variable that has been allocated "statically", meaning that its lifetime (or "extent") is the entire run of the program. Contrast to automatic variables, whose storage is stack allocated and deallocated on the call stack; and in contrast to objects whose storage is dynamically allocated and deallocated in heap memory.


## call stack

The computer science bit

    A stack data structure that stores information about the active subroutines of a computer program. Also known as an execution stack, program stack, control stack, run-time stack or machine stack

## stack

The computer science bit

    Abstract data type with a *push* and *pop* methods to add or remove elements, think of a giant stack of plates to be washed. It's a LIFO data structure (c.f. Queue - a FIFO data structure)

## heap memory

The computer science bit

    Memory areas allocated to each program. Memory allocated to heaps can be dynamically allocated, unlike memory allocated to stacks.
    As a result the heap segment can be requested and released whenever the program needs it.

    It's global which means it can be accessed and modified from wherever in the program it is allocated instead of being localised by the function in which it is allocated. 
    
    Dynamically allocated memory is referenced using pointers. This leads to a slight performance degradation over the use of local variables (on the stack)

More [here](https://www.geeksforgeeks.org/what-is-a-memory-heap/)

## heap

The computer science bit

    A heap is a specialised tree-based data structure that satisfies the heap property.
    heap property:
    In a max heap: if P is parent to C then key of P > key of C.
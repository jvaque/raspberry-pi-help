# C/C++

This is a brief reminder guide for c/c++

## Pointers

A pointer is an object that stores a memory address.

The quick overview of pointers is as follows:

```c
int x           // Declaring variable x as an integer
int *ptr        // Decalring variable ptr as a pointer to an integer
&x              // Get memory address of variable x
*ptr            // Derreference ptr (go to memory address stored on ptr)
                //  (follow pointer to get the value on ptr memory address)
```

Example of using pointers:

```c
int x = 69;     // Declare variable x as an integer and assign value 69 to it
int *ptr = &x;  // Declare pointer to an integer ptr, and assign it the memory
                //  address value of variable x
*ptr = 420;     // Go to the memory address ptr is holding and change the value
                //  to 420
```
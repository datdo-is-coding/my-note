**Dynamic memory allocation techniques** give programmer control of memory when to allocate, how much to allocate and when to de-allocate.
- We can allocate memory at runtime, allows us to handle data of varying sizes.
- The memory is allocated on the heap memory instead of the stack. 
Dynamic memory allocation is possible in C by using the following 4 lib function provided by  `<stdlib.h>` library

## malloc()
The **malloc** (stands for memory allocation) function is used to allocate a single block of contiguous memory on the heap at runtime. The memory allocated by **malloc** is uninitialized, meaning it contains garbage values.

**SYNTAX:** `malloc(size)`
where **size** is the number of byte to allocate
This function returns a void pointer to the allocated memory that needs to be converted to the pointer of required type to be usable. If allocation fails, it return NULL pointer

E.g: `int* ptr = (int*)malloc(sizeof(int)*5);`

## calloc()

The **calloc** (stands for contiguous allocation) function is similar to **malloc()**, but it initializes the allocated memory to zero.
`calloc(n,size)`
where n is the number of elements and size is the size of each element in bytes.
E.g  `int* ptr = calloc(5,sizeof(int))`
This function returns **a void pointer** to the allocated memory that is converted to the pointer of required type to be usable. If allocation fails, it returns NULL pointer.

## free()
The **free()** function is used to release dynamically allocated memory back to the operating system. It is essential to free memory that is no longer needed to avoid memory leaks.
`free(prt)`
We should set the pointer to NULL to avoid a "dangling pointer", which points to a memory location that has been deallocated.

## realloc()
**realloc()** function is used to resize a previously allocated memory block. It allows you to change the size of an existing memory allocation without needing to free the old memory and allocate a new block.
`int* ptr = (int *)malloc(5*sizeof(int))`
`ptr = (int *)realloc(ptr,10*sizeof(int))`

It is important to note that if **realloc()** fails and returns NULL, the original memory block is not freed, so you should not overwrite the original pointer until you've successfully allocated a new block. To prevent memory leaks, it's a  good practice to handle the NULL return value carefully.
`int* ptr = (int*) calloc(5,sizeof(int));

    int* tmp = (int*) realloc(ptr,10*sizeof(int));

    if(tmp==NULL) printf("Memory reallocation failed");

    else ptr = tmp;

## ISSUES
- memory leaks: failing to free dynamically allocated memory leads to memory leaks, exhausting system resources.
- dangling pointers: using a pointer after freeing its memory can cause undefined behavior or crashes.
- **fragmentation** : repeated allocations and deallocations can fragment memory, causing inefficient use of heap space.
- **allocation failures** : if memory allocation fails, the program may crash unless the error is handled properly.


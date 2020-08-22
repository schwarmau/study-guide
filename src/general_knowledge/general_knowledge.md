# General Knowledge

### Bitwise Operations

- & = AND
- | = OR
- ~ = NOT
- ^ = XOR
- << = left shift (new bits are 0)
- \>> = right shift (new bits are 0)

### Bit Manipulation Tricks

- Check if an integer is even
```
return x & 1 == 0;
```
- Check if an integer is a power of 2
```
return x && !(x & (x - 1));
```
- Swap two numbers
```
a = 1; b = 2;
a = a ^ b;
b = a ^ b;
a = a ^ b;
// a = 2, b = 1
```
- Flip the bits of an integer (language-dependent)
```
int allOnes = ConvertToInt("111..."); // use as many 1s as there are bits in x
return allOnes - x;
```

### HTTP Request Methods

- GET = Retrieve data.
- HEAD = GET, but without the response body (just the metadata and header).
- POST = Tell a URI to handle some data.
- PUT = Set the resource at the given URI.
- DELETE = Delete the specified resource.

There are others, but these are the most commonly used.

### Git Commands

- init - creates a new local repository
- clone - downloads an existing project/repo
- diff - shows unstaged file differences
- commit - records the current state of files to version history
- reset - undoes all commits after the provided one
- branch - creates a new branch
- checkout - switches to a specified branch
- merge / mergetool - combine target branches
- stash - temporarily store current file changes
- fetch - downloads repo history
- pull - downloads branch history
- push - uploads local branch commits

There are others, but these are the most commonly used.

### Memory

Memory can be allocated on the stack or the heap.

Stack allocation happens in a contiguous block of memory, and the compiler pre-determines the required space.

Heap allocation happens during the execution of the program as per the instructions of the programmer. 

The key difference is that programmers are responsible for allocating and deallocating heap memory.
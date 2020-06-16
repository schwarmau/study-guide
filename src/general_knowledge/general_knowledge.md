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

- init
- clone
- diff
- commit
- restore
- reset
- branch
- checkout
- merge / mergetool
- stash
- fetch
- pull
- push
- cherry-pick
- rebase

There are others, but these are the most commonly used.
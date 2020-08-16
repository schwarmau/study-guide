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

### Other

There aren't many common attacks that developers will have to actively defend against on a regular basis. From an application design standpoint you could encourage features such as 2-factor authentication, but at the end of the day it's not up to developers whether or not a feature is added. One attack developers will have to actively defend against is the injection attack. Defending against an injection attack is as simple as not letting user input go unchecked to a database query. This means _sanitizing_ and _parameterizing_ user input. Man-in-the-middle attacks are also something that needs to be addressed by developers. The defense against man-in-the-middle attacks is not letting sensitive information travel between services in a manner that makes the information easy to decrypt. In other words: sensitive information should always be encrypted before crossing services, and encrypted information should not travel with or near any information that could aid in decrypting it. While you might not personally have to deal with either of these things, it's not all that common to see a basic injection attack question in an interview (e.g. "What's wrong with this code?").
# Sequence

### Find the \\( k^{th} \\) smallest element in an unordered sequence (Quickselect)

Quickselect operates on bounds and a pivot, with the first bounds being the first and last indices of the sequence. A pivot is chosen at random from within the bounds, then the sequence is iterated through and moves elements smaller than the pivot to the front of the list. Once the sequence is iterated through, it is read from last-to-first until a value smaller than the pivot is found, at which point the pivot is placed there in the sequence (so now the pivot is in the correct position as if the sequence was sorted). Now, if the pivot is in position _k_, then it is returned. Otherwise, if the pivot is in a position greater than _k_, the process is repeated with the current pivot as the new right bound and the start of the sequence as the left bound; if the pivot is in a position less than _k_, the process is repeated with the current pivot as the new left bound and the end of the sequence as the right bound. In either non-_k_ situation, a new pivot is chosen.

Quickselect runs in \\( O(n) \\) time on average, but \\( O(n^2) \\) time in the worst case. It is able to be implemented in-place (i.e. without needing to use an auxilliary data structure), and is used frequently in real-world applications.

### Find an item in an unordered sequence (Linear/Sequential/Brute Force Search)

A most basic of algorithms: if your item is not the first item, then check the next item and repeat. \\( O(n) \\) time. Included to illustrate brute forcing.

### Randomly shuffle a finite set (Fisher-Yates/Knuth Shuffle)

The Fisher-Yates shuffle (A.K.A. the Knuth shuffle) is an algorithm for generation a random permutation of a finite sequence. The basic idea is as follows:
```
function shuffle(arr[n])
    for i = 0...n-2
        pick a random number j between i and n-1 (inclusive)
        swap arr[i] and arr[j]
```

Simple enough and \\( O(n) \\) time.

### Find the sequence alignment between two strings that results in the shortest Levenshtein distance, using whitespace as a buffer (Hirschberg's Algorithm, Needleman-Wunsch Algorithm)

Recall that the Levenshtein distance between two strings is the amount of single-character edits (insertion, deletion, or substitution) required to transform one string into the other.

Hirschberg's algorithm is a divide & conquer twist on the classic dynamic programming model of the Needleman-Wunsch algorithm (which has a worse space requirement of \\( O(nm) \\)).

The Needleman-Wunsch algorithm is as follows:

```
function getLevenshteinDistance(str1, str2)
    initialize dist[n][m]
    for i -> 0...n
        for j -> 0...m
            if i is 0
                dist[i][j] = 0
            else if j is 0
                dist[i][j] = 0
            else
                dist[i][j] = min(dist[i-1][j-1], dist[i-1][j], dist[i][j-1])
                if (str1[i] != str2[j])
                    dist[i][j] = dist[i][j] + 1
    return dist[n-1][m-1]
```

To get the steps required to transform one string into another, you can follow the path of minimum values (going vertically, horizontally, or diagonally) from `dist[n-1][m-1]` down to `dist[0][0]`. When the values of the strings in those positions are the same, no change is needed. When _i_ and _j_ are different then, if _i_ is less than _j_, make an insertion between str1[i] and str1[i + 1], and if _i_ is greater than _j_, make an insertion between str2[j] and str2[j + 1]. When the values are the same then a substitution is required.

The Hirschberg algorithm seeks to apply divide and conquer on the Needleman-Wunsch algorithm (finding the distance between the first half of the first string and first half of the second, and combining the with the results of the other halves, recursively) in order to save space. It takes \\( O(nm) \\) time and uses \\( O(min(n,m)) \\) space, where _n_ is the length of the first string, and _m_ is the length of the second.

### Determine whether a string contains another given string (Boyer-Moore Algorithm)

The traditional method of finding a substring within a string is as follows:

```
function hasSubstring(str, substr)
    if (substr.length > str.length)
        return false
    for (i = 0...m)
        if (str[i] != substr[i])
            return hasSubstring(str[1->n], substr);
    return true;
```

Which runs in \\( O(nm) \\) time.

The Boyer-Moore algorithm improves upon that by changing the recursive calls. The realization is that if you compare the substring to the string from back-to-front instead of from front to back then you can optimize the shift you make for the recursive call if the substring is not a match. The worst case runtime remains the same, but with the application of something known as the Galil rule, it can be reduced to linear time. More information about the Boyer-Moore algorithm is [here](https://en.wikipedia.org/wiki/Boyer%E2%80%93Moore_string-search_algorithm).

BONUS: A similar question is: does this string contain the characters of this other string in order?

The algorithm is as follows:

```
function hasCharsInOrder(str, chars)
    if chars.length > str.length
        return false
    else if str[0] == chars[0]
        return hasCharsInOrder(str[1->n], chars[1->m])
    else
        return hasCharsInOrder(str[1->n], chars)
```

It runs in \\( O(n + m) \\) time.
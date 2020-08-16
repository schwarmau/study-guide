# Sorting

All the algorithms in this chapter accomplish the same goal by different means: sort the elements of a list.

### Bubble Sort

Bubble sort is a pretty rudimentary algorithm primarily used for educational purposes (which is what this guide is for, so it appears here). It's a very straightforward process. Go through the list; if the current element is greater than the next element then swap them, else continue. Repeat that process until the list is sorted. Even in the average case it still takes \\( O(n^2) \\) time.

### Quicksort

Quicksort is very common sorting algorithm in the real world. It is a divide and conquer algorithm that starts by selecting a pivot element from the list and then going through the list, categorizing all other elements as "less than", "equal to", or "greater than" the pivot element. The sub-arrays are then sorted recursively, and combined at the end:

```
function quicksort(arr)
    pivot = random i in 0 -> n-1
    left = new array
    center = new array
    right = new array
    for each element in arr
        if element < pivot:
            left.add(element)
        else if element > pivot:
            right.add(element)
        else:
            center.add(element)
    return quicksort(left) + center + quicksort(right)
```

Quicksort has an \\( O(n^2) \\) worst case, \\( O(n) \\) best case, and \\( O(n \log n) \\) average case. It also has to use \\( O(\log n) \\) auxilliary space.

### Insertion Sort

Insertion sort is compared to the way people usually sort a hand of playing cards.

The premise is to go through the list one-by-one and examine the element at that index. If it is less than the element to its left, then swap the two elements and repeat, otherwise (or if it is at position 0) stop and move on to repeat this process with the next element in the list.

```
function insertionsort(arr)
    for i = 1...n-1
        val = arr[i]
        for j = i-1...0
            if arr[j] > val
                arr[j+1] = arr[j]
            else
                arr[j+1] = val
                break
```

It has an \\( O(n^2) \\) runtime, although it is perhaps the best sorting algorithm for a list that is alread mostly sorted. It can also be performed in place.

### Merge Sort

Merge sort is one of the common real-world sorting algorithms. It is a divide and conquer algorithm, which starts by dividing the list in n sublists of one element each. A single-element list is, of course, sorted by default. From there, pair up each sublist with another and merge them together with the logic as follows:

```
function merge(arr1, arr2)
    i = 0
    j = 0
    result = new arr
    while (i < n || j < n)
        if j == n || arr1[i] <= arr2[j]
            result.add(arr1[i])
            i += 1
        else
            result.add(arr2[j])
            j += 1
    return result
```

The process of pairing up and merging sublists is repeated until there is only one list (the final, sorted list).

This takes \\( O(n \log n) \\) time in the worst case, and uses \\( O(n) \\) auxilliary space.

### Timsort

Timsort was originally developed for use in the python programming language. It is a stable algorithm, meaning if two equivalent (equal by comparison, but different, perhaps by reference), values are in the list, their relative ordering will be maintained in the final product.

It is heavily based on merge sort and insertion sort. More information [here](https://en.wikipedia.org/wiki/Timsort).

In the worst case it takes \\( O(n \log n) \\) time. It has an advantage over quicksort when sorting object references or pointers.

### Bucket Sort

Bucket sort works by creating _k_ buckets representing a value or range of values. The list is then iterated through, placing the values in their relevant buckets, and then at the end the buckets are combined in order to create the sorted (or semi-sorted in the case that buckets represent ranges) list.

In most cases this is an inefficient sorting algorithm, taking at worst \\( O(n^2) \\) time, and on average \\( O(n + \frac {n^2} k + k) \\) time. In the case that _k_ = _n_ the runtime can be \\( O(n) \\), but the higher _k_ is, the more space is used. The worst-case space complexity would be \\( O(n \cdot k) \\).

This algorithm is most useful when the length of the list exceeds the possible values. For instance, sorting a large amount of people by age.

### Radix Sort

Radix sort is a form of bucket sort that avoids comparisons by bucketing based on the radix of the list elements, starting either at the most significant digit or the least significant.

It runs in \\( O(w \cdot n) \\) time, and has equivalent space complexity, where _w_ is the number of bits required to store the keys for the elements based on their radix. More info [here](https://en.wikipedia.org/wiki/Radix_sort).

### Selection Sort

Selection sort is an in-place sorting algorithm.

It is inefficient on large lists, and generally performs worse than both insertion sort and heapsort, but has advantages in its simplicity.

The general process is starting at index 0, find the smallest element and swap it with that index, then move to index 1 and repeat with the remaining unsorted elements.

It runs in \\( O(n^2) \\) time.

### Heapsort

Heapsort is an improvement upon selection sort. In the step where selection sort finds the smallest element, heapsort keeps the remaining (unsorted) elements in a heap so as to make the process of finding the minimum unsorted value much faster. The worst case scenario is improved to \\( O(n \log n) \\). Because it uses an array implementation of a heap on the remaining unsorted sequence, it only needs to use a constant of auxilliary space.
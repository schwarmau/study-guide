# Asymptotic Analysis

## Big-O Notation
Asymptotic analysis is usually expressed in Big-O notation. This notation is usually used to describe the upper bound on a growth rate.

Formally, it is said that \\( f(x) = O(g(x)) \\) if there exists a positive real number \\( m \\) such that \\( \left\lvert f(x) \right\rvert \leq m \cdot g(x) \\) as \\( x \to \infty \\). Alternatively, \\( f(x) = O(g(x)) \\) if such an \\( m \\) exists that makes \\( \lim_{x \to \infty} \frac{\left\lvert f(x) \right\rvert}{m \cdot g(x)} \lt \infty \\) true.

For example: \\( x^2 \\) is \\( O\left(x^3\right) \\) and \\( 4x^2 + 3x + 2 \\) is \\( O\left(x^2\right) \\).

## Other Notations
Big-\\( \Omega \\) notation can be interpreted as the "opposite" of Big-O notation in computer science; \\( f(x) = \Omega(g(x)) \\) if and only if \\( g(x) = O(f(x)) \\). Alternatively, \\( f(x) = \Omega(g(x)) \\) if there exists a positive real number \\( m \\) such that \\( \lim_{x \to \infty} \frac{f(x)}{m \cdot g(x)} \gt 0 \\).

For example: \\( x^3 \\) is \\( \Omega\left(8x^2\right) \\). It is also possible for the second example above to hold: \\( 4x^2 + 3x + 2 \\) is \\( \Omega\left(x^2\right) \\).

Big-\\( \Theta \\) notation is defined simply as: \\( f(x) = \Theta(g(x)) \\) if and only if \\( f(x) = O(g(x)) = \Omega(g(x)) \\).

Using the example above: \\( 4x^2 + 3x + 2 \\) is \\( \Theta\left(x^2\right) \\).

## Algorithm Analysis
In computer science, Big-O notation is commonly used to describe the performance of algorithms, either in terms of run time or memory usage. Usually when run time or memory usage are analyzed, we want to know the worst-case, so we make the assumption that conditional statements always pass. Take the following function for example:

```
def myFunc(someArray)
{
    count = 0;

    foreach (element in someArray)
    {
        if (element != null)
            count = count + 1;
    }
}
```

Line-by-line:
- `count = 0;` is an assignment operation, and has a constant run time, so this is an \\( O(1) \\) operation.
- `foreach (element in someArray)` loops through each element of the array, so this tells us that whatever happens inside this loop will happen n times, where n is the length of the array.
- `if (element != null)` is a conditional statement (constant time) using an equality comparer (also constant time), thus an \\( O(1) \\) operation.
- `count = count + 1;` is an assignment and increment (both constant time). Since we're analyzing the worst case scenario, we assume this will always be hit, even though it's only conditionally hit in practice. Either way, it is an \\( O(1) \\) operation.

In total, we have a run time of \\( O(1) + (O(n) \cdot (O(1) + O(1))) \\). This can be condensed to \\( O(1 + (n \cdot (1 + 1))) = O(1 + n) = O(n) \\).

If we were to add another for loop inside the existing one then we would get a runtime of \\( O\left(n^2\right) \\), and so on.

### Amortized Analysis
An alternative to worst-case performance analysis is amortized analysis, which is roughly "average-case" performance analysis. There are 3 primary methods to analyze an algorithm like this:
1. Run the algorithm \\( n \\) times with different inputs, calculating their operational costs each time. Take the upper bound of the sum of all operational costs and divide by \\( n \\).
2. [The accounting method](https://en.wikipedia.org/wiki/Accounting_method_(computer_science))
3. [The potential method](https://en.wikipedia.org/wiki/Potential_method)

Amortized analysis is usually how certain performance gains are found, especially when the possible input set of an algorithm is limited. For example, quick sort is the most commonly implemented sorting algorithm, but it's actually faster to sort a mostly sorted collection using insertion sort. Similarly, quick sort in and of itself has a worst-case of \\( O(n) \\), even though it's _usually_ more performant than other sorting algorithms with better worst-case analyses.

### The Master Theorem
Sometimes it is difficult to analyze algorithms, especially when they implement recursion, such as in Divide & Conquer algorithms. This is where the master theorem comes into play. Divide & Conquer algorithms can be expressed as \\[ T(n) = a \cdot T\left(\frac{n}{b}\right) + f(n) \\] where \\( T(n) \\) is an upper bound on the run time of the algorithm, \\( n \\) is the input size, \\( a \\) is the number of recursive calls that each individual call makes, \\( \frac{n}{b} \\) is the input size of the recursive calls, and \\( f(n) \\) is the the run time of the final call (the base case). Additionally, let \\( c_{crit} = \frac{\log(number of subproblems)}{\log(relative subproblem size)} = \log_b a \\).

Given the above, the master theorem says that
- If there exists a \\( c \lt c_{crit} \\) such that \\( f(n) = O\left(n^c\right) \\), then \\( T(n) = \Theta\left(n^{\log_b a}\right) \\).
- If there exists a \\( k \geq 0 \\) such that \\( f(n) = \Theta\left(n^{c_{crit}} log^k n\right) \\), then \\( T(n) = \Theta\left(n^{c_{crit}} log^{k+1} n \right) \\).
- If there exists a \\( c \gt c_{crit} \\) such that \\( f(n) = \Omega\left(n^c\right) \\), _and_ there exists a \\( k \lt 1 \\) and sufficiently large \\( n \\) such that \\( a \cdot f\left(\frac{n}{b}\right) \leq k \cdot f(n) \\), then \\( T(n) = \Theta(f(n)) \\).
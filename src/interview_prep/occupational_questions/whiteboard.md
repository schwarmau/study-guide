# Whiteboard

Competitive tech companies are notorious for giving computer science applicants a barrage of whiteboard problems. The thing that distinguishes these problems from other common interview problems is their long form and focus on critical thinking, as opposed to rote memorization. These come in the form of "here's what you know, here's what you want to know, write an algorithm to find out what you want to know." You probably wont be given a computer, you probably wont be allowed to use your phone, and you probably wont be given a piece of paper; It's just you and a whiteboard.

Even if you're well-acquainted with the algorithms chapter you may still find these problems difficult, but there are some steps you can take alleviate the challenge and impress the interviewer:
- Know the inputs, outputs, requirements, and constraints. 
    - Ask the interviewer about these if you are unsure.
    - Usually you aren't given the method signature of the solution. Instead, the question might be simply, "Given a list of people, sort them by age". Here, you can ask questions like, "What should a person object look like?" (they might just have you create it to see what you come up with). Such questions can apply to outputs as well. Even better, you could ask, "Can I assume that the maximum age of a person is 150?" That question could be the difference between implementing quick sort and implementing bucket sort.
    - Common requirements and constraints might revolve around runtime, complexity, memory usage, etc. It's likely that you wont receive such requirements/constraints if they are not mentioned by the interviewer. However, if you solve the problem quickly, they may try to expand upon the question by asking you to solve it under certain constraints or with certain requirements.
- Think out loud. Interviewers want to hear your thought process, and sometimes they might correct your course if they can tell you're going down the wrong path.
- Don't try to write syntactically correct programs (unless asked). Write pseudo-code. It's faster, and you reduce the risk of syntactical errors ruining your solution.
- If you can't think of a solution immediately, then start by trying to recall any algorithms that might solve the problem with a little transformation. A well-known example of this is the bipartite matching problem, which can be transformed into a maximum flow problem, which has a known algorithmic solution.
- If you can't recall an algorithm that matches this problem, then pick a top-level algorithm and design a new algorithm yourself (refresher: top-level algorithms include brute force, divide & conquer, greedy method, and dynamic programming).
- Don't forget about recursion. Interviewers seem to love recursion. If you can solve a problem in a simple way with recursion, do it!
- Address all possible inputs. Usually edge cases can be solved with simple `if` statements, so it can be beneficial to address them last if time is a concern.
    - Remember: negatives, zeros, positives, minimums, maximums. Aside from those, it's situational (e.g. if using division with a variable denominator, you need to check that the denominator can never be 0).
- If you solve a problem quickly, and you notice that there are places in the solution that an exception could be thrown if it were converted to real code on a machine, then you might sound smarter if you ask if you should handle possible exceptions. This is rarely encountered, and rarely a requirement, just something to keep in mind if you breezed through the problem.

### Activity Selection

### Huffman Encoding Tree

### Closest Pair of Points

### Longest Increasing Subsequence

### Longest Common Subsequence

### Hamming Distance

### Levenshtein Distance

### Bipartite Matching

### Graph Coloring

### Topological Sorting

### Point Containment

### Point Containment 2

### Closest Point

### Value Swap

### Knapsack

### FizzBuzz
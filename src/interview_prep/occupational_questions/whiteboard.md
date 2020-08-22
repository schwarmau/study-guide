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

NOTE: Problems covered in the algorithms chapter and in the general knowledge chapter are not included (e.g. Traveling Salesman, Levenshtein Distance, Value Swap).

### Activity Selection

Given _n_ activities and their start/end times, determine the maximum number of activities (and which activities those are) that a single person can participate in, assuming they cannot do multiple activities at once.

A variation of this would be to not maximize the number of activities, but rather minimize the time in which you are not participating in an activity.

### Huffman Encoding Tree

A Huffman code is a type of prefix code used for lossless compression.

Given a set of symbols and their weights, find a set of codewords with minimum expected length (a tree with minimum weighted path length from the root).

Basically, you want to create a tree where each leaf node is one of the symbols given. This is most easily made as a binary tree on paper, and generating the code for a symbol would thus involve treating left branches as adding a 0 and right branches as adding a 1. In general, you would like symbols weightest heaviest to have the smallest code, since they will be encountered the most often when compressing a file. 

It is also essential that codes cannot be confused. For example, if one symbol had the code 00 and another had the code 001 and another 1, then it would be impossible to tell in an encoding whether it means two symbols (00 and 1) or one (001). For this reason, the symbols will all need to be leaves in the tree.

For example: given a = 0.1, b = 0.15, c = 0.30, d = 0.16, and 3 = 0.29, then the huffman codes would be 010, 011, 11, 00, and 10, in that order.

### Closest Pair of Points

Given a set of points in a two dimension plane, determine which pair of points is the closest. 

You can, of course, challenge yourself to do this in 3-dimensional space, or beyond.

### Longest Increasing Subsequence

Given an array of numbers, determine the start and stop index of the longest sequence of increasing numbers in the array (index _i_ must be greater than index _i - 1_ for each _i_ in the sequence).

### Longest Common Subsequence

Given two strings, determine the longest substring the two share.

### Hamming Distance

Perhaps a bit trivial: Given to equal-length strings, determine how many substitutions it would take to convert one to the other.

### Bipartite Matching

Given _n_ applicants and _m_ jobs, as well as the knowledge of which jobs the applicants have applied to, determine the maxmimum number of applicants that can end up with jobs, and to which job each applicant would go in that case.

### Graph Coloring

Given a graph and _n_ colors, find a way to color each vertex of the graph such that no adjacent vertices share a color.

### Topological Sorting

List the vertices of a directed acyclic graph in such a way that, for every edge _uv_, vertex _u_ comes before vertex _v_. There can be more than one correct solution for some graphs.

### Point Containment

Given a series of points on a 2-dimensional plane, determine the corners of the smallest box that encapsulates all points.

Can you extend this to 3-dimensional space?

### Point Containment 2

Given a polgyon in a 2-dimensional plane, and a point, determine if the point is within the polgyon.

Can you extend this to 3-dimensional space?

### Closest Point

Given a starting point in 2-dimensional space and a list of other points in that space, determine which of the "other" points is closest to the starting point.

Can you extend this to 3-dimensional space?

### Knapsack

Given a weight limit and a list of objects that have a value and a weight, determine the maximum value of objects you can take without exceeding the weight limit.

### FizzBuzz

Print the numbers from 1 to 100, except print "fizz" instead of multiples of 3, print "buzz" instead of multiples of 5, and print "fizzbuzz" instead of multiples of both 3 and 5.

### Parentheses Validation

Given a string containing only parentheses, determine if each parenthese is matched correctly.

For example: `(()())((()))` is correct, but `)(())()(` is not. Essentially, each open parenthese must have a closed parenthese after it, and each close parenthese must have an open parenthese before it (not necessarily _immediately_ before or after).

### Generate Parentheses

Given an integer, _n_, generate a list of all possible strings with _n_ correctly matched parentheses.

For example: When \\( n = 3 \\), the possible strings will be `((()))`, `(()())`, `(())()`, `()(())`, and `()()()`.

### Reverse Integer

Given an integer, _n_, reverse its digits.

For example: When _n_ is `321`, its reverse would be `123`.

### Factor Combinations

Given a number, _n_, find all combinations of factors of _n_, besides 1 and _n_, that can multiply to produce it.

For example: When _n_ is `12`, the factor combinations are `(6, 2)`, `(3, 4)`, and `(2, 2, 3)`, because each of those lists contain only factors of 12, and when they are multiplied together they produce 12. NOTE: `(6, 2)` and `(2, 6)` are considered equivalent for this matter, so only one is included.

### Fraction to Recurring Decimal

Given a fraction with a recurring decimal, \\( \frac a b \\), output the decimal value, using an underscore (`_`) to represent the start of the repeating decimal.

For example: When _a_ is `1` and _b_ is `3`, output `0.3_`

### Anagrams

Given two strings, determine if they are anagrams (two words that contain exactly the same letters, and the same amount of each letter to boot).

As an additional challenge: Given an array of strings, determine if they are all anagrams.

### Longest Non-Redundant Substring

Given a string, determine the starting and ending index of the longest contiguous sequence of distinct characters in the string.

For example: In the string `abacdbca`, we find the longest sequence of distinct characters at `acdb` (start index 2, end index 5), as well as `dbca` (start index 4, end index 7).

As an additional challenge: Find the longest substring with _at most k_ distinct characters.

### Minimum Path Sum

Given an _m_ x _n_ grid of non-negative numbers, find a path from top left to bottom right which minimizes the sum of all the numbers touched along the path.

For example, the minimum path through

```
[
    [1,3,1],
    [1,5,1],
    [4,2,1]
]
```

is (0, 0) -> (0, 1) -> (0, 2) -> (1, 2) -> (2, 2).

### Tower of Hanoi

Given _m_ pegs and _n_ discs (smallest to largest from top to bottom) which start on the first peg, determine what steps must be taken to move the discs to peg _k_ and have them end up stacked in the same order in which they began.

There are rules for what steps you can perform, though:
- Only one disc can be moved at a time
- You may only move the top-most disc on a peg
- You may only place a disc on top of a larger disc

The tower of hanoi problem specifically dictates _m_ is 3, although you can challenge yourself to consider more (the same algorithm can be reused, but it could also be made more efficient).

### Dining Philosophers

Five silent philosophers sit at a round table with bowls of spaghetti. Forks are placed between each pair of adjacent philosophers.

Each philosopher must alternately think and eat. However, a philosopher can only eat spaghetti when they have both left and right forks. Each fork can be held by only one philosopher and so a philosopher can use the fork only if it is not being used by another philosopher. After an individual philosopher finishes eating, they need to put down both forks so that the forks become available to others. A philosopher can only take the fork on their right or the one on their left as they become available and they cannot start eating before getting both forks.

Eating is not limited by the remaining amounts of spaghetti or stomach space; an infinite supply and an infinite demand are assumed.

The problem is how to design a discipline of behavior (a concurrent algorithm) such that no philosopher will starve; i.e., each can forever continue to alternate between eating and thinking, assuming that no philosopher can know when others may want to eat or think.

This is more of a conceptual problem, as most programming languages have the functionality to achieve this built-in (you just have to know how to use it correctly). Concurrency was not discussed much in this guide, aside from small explaination in the design patterns chapter. For help you can research _semaphores_, _mutexes_, and _locks_.

### Eight Queens

Place _n_ queens on an _n_ x _n_ chessboard such that no two queens threaten each other (no two queens share the same column, row, or diagonal).

If you figure out the solution by hand then it will be straightforward to convert to code, so don't try to solve the problem with guess and check as that would defeat the purpose; try to come up with an algorithmic way of arriving at the solution. Of course, reverse engineering is a valid skill so you could just ignore this advice.

### Two Generals

The two generals' problem is another real-world problem, except this time it is merely food for thought, as the problem has no solution. It is therefore not _really_ a whiteboard problem, but you might still be asked about this at an interview and tricked into trying to solve it just to see your thought process.

Suppose there are two generals and their armies on either side of a castle, and they would like to coordinate to plan their attack, as they cannot win if only one army attacks at a time. However, it is a risky venture to contact one another as they will have to send someone through the castle grounds to the other side, and there's no guarantee that the person makes it. One general would like to start the joint attack at 8:00 am, so they send a messenger to the other general and decide "if my messenger does not come back then I will send another, otherwise if my messenger comes back then I know the other general got the message". The other general receives the message and tells the messenger to return once it has responded to the first general, "if the messenger does not come back then I don't know if the other general got my response--I will have to send another messenger". And so you see the conundrum. Neither general can have complete certainty that the other general is certain about the plan.

### Scheduling

Given _n_ students and _m_ classes with a capacity and a start/end time, and each student has a known ranking of classes they would like to take, attempt to maximize total happiness amongst by assigning students to classes. The only rules are that the classes cannot exceed their capacity, and students cannot take two classes at the same time.

A variation of this problem says that students need _k_ minutes between classes to travel from classroom to classroom. Another says that some classes are dependent on others...this is a real-world problem so it can be extended in a lot of ways.

### Jump Game

Given an array of positive integers, determine whether the "jump game" will end given a starting point, _i_.

The jump game is where you move a number of "spaces" forward in the array equal to the current position you are at. The game ends if you can reach the last element of the array. The game cannot end if you are unable to move to a valid space, or if you are on a 0 which is not the last position of the array.

There are several variations of this problem that you can tackle:
- The array can contain negative integers, which will cause you to move backwards.
- You can move a number of spaces _up to_ the amount shown on your current space (absolute value to the left if using negative numbers).
- You are allowed to move _past_ the end of the array, and wrap around to the other side (in which case the game will only fail to end if you encounter a 0 or a loop).
- You get to choose whether you want to move that many spaces forward or backward.
- You are not only given a starting index, _i_, but also an ending index, _j_ (the same rules apply, except the game only ends if you can land on _j_).
- The game only ends when you land on a 0.

The most complex ruleset for a challenge would be one in which you are given the choice of whether to move forward or backward, as well as the ability to loop around the array, as well as a target ending index.

### Bit Reversal

Given an integer, _n_, reverse its bits.

### String Permuations Around Capitals

Given a string, output all permutations of the string wherein capitalized letters remain in the same position.

For example: The string `abCd` can be permuted as itself and as `adCb`, `baCd`, `bdCa`, `daCb`, and `dbCa`.

A variation of this problem may have you only move numbers around within the confines of their surrounding capital letters. Other common variations simply change the pivot criteria (instead of keeping capital letters in the same place, you have to keep hyphens in the same place, and so on).

### Find Duplicates

Given an array of integers, find all duplicates (the 2nd or greater instance) of numbers in the array.

Challenge yourself to do this in \\( O(n) \\) time and \\( O(1) \\) wasted/extra space.

### Tic-Tac-Toe

Implement Tic-Tac-Toe with an _N_ x _N_ board. What this means is to produce the following outputs and take the following inputs:

```
Output: What is N?
Input [integer]
Output: Would you like to play as X (go first) or O (go second)?
Input: [X or O]
// if user selects O, the program goes first and marks an empty space--in the challenge variation of this problem, the program will always make an optimal move
Output: // after every move the program should print the current state of the NxN board
// after every move the program should analyze whether there are N of one value (X or O) in a row, and if there are, output the winner
Output: Where would you like to place your mark?
Input: [(i, j), where i is the row, and j is the column]
```

A variation of this problem is: Given an _N_ x _N_ Tic-Tac-Toe board state, determine whether there is a guaranteed way to win for the player whose turn it is (no matter how the opponent plays, the player can win from this position). Traditionally this variation is only given for 3x3 Tic-Tac-Toe, so you can start with the assumption that _N_ is always 3, and then try to program for a generic _N_.

### Indexed Binary String

Given an index, _k_, find the \\( k^{th} \\) digit in a binary string. The binary string will be defined as follows:

```
binString = "0";
binString = binString + ~binString; // recall ~ is the NOT operator in some languages
binString = binString + ~binString;
// etc.
```

Thus the binary string ends up being 0 -> 01 -> 0110 -> 01101001 -> 0110100110010110...

To provide a more formal definition of the binary string _is_ the problem.

### Relationships

Consider the following code (this intentionally contains oddities that don't exist in most langauges):

```
Class Person {
    Public Person mom;
    Public Person dad;
    Public Person children[];

    Public static bool areRelated(Person p1, Person p2, int gens) {
        /* gens = number generations removed the two people must be within in order to be considered "related" */
    }
}
```

Your goal is to implement areRelated(...). It should return whether or not the two people are related, based on the generational threshold.

The simple solution to this may yield a lot of wasted space or extraneous recursive calls for high values of `gens`. Try to think of a way to minimze that cost (of course, you may have already done it in your first solution, so don't spend too much time on this if you can't figure it out!).

### PHP Exploit

Consider the following code:

```
$pin = $_GET['PIN'];
$cmd = 'sudo testcode.py $pin;';
exec($cmd);
```

How can someone remove all files from the host machine if a web app contains this code?

Followup question: How do you know the system will allow you to run this code without prompting you for an admin password?

### Prime Sum

Given an even number greater than 2, validate that it is the sum of 2 primes (this is a true fact) by finding those 2 primes and printing them. NOTE: 1 is not considered a prime number.

### Odd One Out

Given a sorted list within which there are exactly two copies of each element, except for one, find which element is the one without a copy.

There is a simple solution to this problem that can be performed in \\( O(n) \\) time. Your goal is to solve this problem in \\( O(\log n) \\) time.

### Greatest Common Denominator

Find the greatest common denominator of 2 numbers.
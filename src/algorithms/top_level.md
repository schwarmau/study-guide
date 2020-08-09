# Top-Level

Top-level algorithms encompass the general approaches to solving problems in computer science. These don't necessarily have an accompanying problem, and they're used as a foundational piece of most common algorithms.

### Brute Force

The most straight-forward approach to problem-solving: Try everything. Many people think of password cracking when they think of brute force algorithms; If you are trying to figure out the passcode to a 4-digit combination lock with no guess limit, you can simply try every combination of 4 digits. Such is the essence of brute force.

### Greedy Method

The greedy method is when you "prefer" something in an algorithmic approach to problem solving. 

For instance, if you want to maximize the number of items you can take on your trip in your suitcase without concern for their value, you might pack your items in order from smallest to largest. In that case, you are preferring small items, so you're using a greedy method. Such a problem also demonstrates the drawback of the greedy method: Often times, it is not perfect. In that scenario, at some point it may no longer becomes optimal to pack the smallest item because its shape might prevent you from adding anything more, even though 2 slightly larger items would have fit.

### Divide & Conquer

Like the name suggests, the premise of divide and conquer algorithms is to divide the problem into sub-problems, solve the sub-problems, and then merge the solutions together to form the solution to the initial problem.

### Dynamic Programming

Dynamic programming can be difficult to conceptualize, but don't worry, there are examples in other sections of this guide. 

Similar to the divide and conquer approach, dynamic programming seeks to define sub-problems and solve them before merging them to create a solution to the base problem. The difference between the two approaches is that dynamic programming requires that the sub-problems are overlapping. 

So what, exactly, is an overlapping sub-problem? Consider the Fibonacci series: \\( F_i = F_{i-1} + F_{i-2} \\), with the base case \\( F_1 = F_2 = 1 \\). In order to solve for \\( F_{10} \\) we generate two sub-problems, \\( F_{10} = F_9 + F_8 \\). We thus need to solve another sub-problem, \\( F_9 = F_8 + F_7 \\), and so we see that the solution for \\( F_{10} \\) and \\( F_9 \\) have an overlapping sub-problem of \\( F_8 \\) (and \\( F_7 \\), etc.). If we were to take a divide and conquer approach then we'd be solving \\( F _8 \\) twice, which dynamic programming seeks to optimize against.

The dynamic programming approach is usually to create a k-dimensional table for sub-problems and their solutions, where k is the number of sub-problems each problem has. There are 2 common ways to go about this:
- Top-down: Upon observing a sub-problem, check the table to see if it has already been solved. If it has already been solved, then use it, otherwise we solve it and add its solution to the table.
- Bottom-up: Create a table of sub-problems, then start at the most refined sub-problem(s) (ones which do not have any further sub-problems, like \\( F_1 \\) and \\( F_2 \\) in the Fibonacci series), adding solutions to the table until you arrive at the original problem. 

The top-down approach may save more space, but you have to check the table for a sub-problem in each step. The bottom-up approach avoids the lookup tax, but might solve more sub-problems than it needs to. The top-down approach is usually done recursively, whereas the bottom-up approach is usually done iteratively. In programming this amounts to whether a function calls itself or whether it uses a `for` loop.

### Monte Carlo

This type of algorithm solves a problem by randomly sampling the solutions to related problems. For example: if you know that a certain problem with variables has a solution of 0 5% of the time and a solution of 1 99% of the time, then the monte carlo approach to figuring out where the next solution will lie could be to just randomly sample the set of known solutions and pick the result of the random sampling. This does not guarantee accuracy, but it is very fast (fixed time) and the probability you are correct is high. When repeated in massive quantities you can simulate very complex things like fluid dynamics.

### Las Vegas

A Las Vegas algorithm is another randomized algorithm, but in contract to the Monte Carlo approach, it will always produce the correct result (or inform you of failure) at the cost of an uncertain runtime. It is generally applicable to problems where "you'll know the solution when you see it." In essence, you randomly pick a possible solution, and if that solution is correct you return it, otherwise you repeat the process, failing after some threshold of attempts.

### Hill Climbing

Hill climbing algorithms apply to algorithms that have many solutions, and it is a strategy taken to find the _optimal_ solution. For example, if you want to find the fastest path between two cities, you could find many paths, and optimize their speed over team via hill climbing.

The general premise is to arbitrarily pick a solution to start at, then make an incremental change to it. If the incremental change produces a better solution, then repeat the process. You can tune the algorithm in ways such as the amount of incremental changes that are attempted before giving up, or _how_ incremental the changes actually are. In general, this will lead the optimal solution for problems with a convex (hill-shaped) solution set. However, for problems with multiple "hills", you might only find the local optima.
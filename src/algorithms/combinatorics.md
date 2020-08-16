# Combinatorics

### Find a cycle in function value iterations (Brent's Algorithm)

[Brent's Algorithm](https://en.wikipedia.org/wiki/Brent%27s_method)

### Solve the stable matching problem (Gale-Shapley Algorithm)

The stable matching problem is as follows: Given _n_ students and _n_ internships, and each participant has an ordering or ranking for which students/internships they would prefer, generate a stable matching for each participant. All matches are stable if there are no cases such that a student would prefer an internship they weren't matched with, _and_ that intership would also prefer that student to the one they were matched with. Note that you can replace "students" and "internships" with any entities that need to be matched and have preferences.

The Gale-Shapley algorithm starts by trying to match each student with the internship they prefer most. Each intership with a match offer will then choose among the students that matched to them the one they most prefer, and reject the others. Then, each unmatched student will try to match with their 2nd-most preferred intership, and the interships will then repeat the process of choosing only the student they most prefer (if they prefer a student among their new offers to the one they currently are matched with--if they have a match--then they will take the new student). This process repeats until there are no unmatched students.

The runtime complexity of the algorithm is \\( O(n^2) \\).

### Generate a pseudorandom number (Mersenne Twister, Linear Congruential Generator, Blum Blum Shub)

[Mersenne Twister](https://en.wikipedia.org/wiki/Mersenne_Twister)

[Linear Congruential Generator](https://en.wikipedia.org/wiki/Linear_congruential_generator)

[Blum Blum Shub](https://en.wikipedia.org/wiki/Blum_Blum_Shub)
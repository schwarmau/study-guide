# Short Answer

Note: In addition to what is provided here, you may be asked questions about anything you have put on your resume (e.g. How does X work in the Y programming language?).

__Q:__ What is \\( 2^x \\)? Note: \\( x \\) will rarely be more than 12.

<details>
<summary>Answer</summary>
2, 4, 8, 16, 32, 64, etc.
</details>

<br>

__Q:__ What is the difference between a struct and a class, and what might you use a struct for? Note: This is somewhat language-dependent (not all languages even have both).

<details>
<summary>Answer</summary>
Structs usually give their properties and methods public modifiers by default, and in some modern languages they represent value types as opposed to reference types. Usually structs are used for simple objects or types, which don't need complex methods. In general, a struct might be appropriate when the data type is going to be small, and either it is expected to be short-lived or it is expected to be frequently embedded in other objects.
</details>

<br>

__Q:__ What is a static class/method/variable?

<details>
<summary>Answer</summary>
<ul>
<li>Class: A static class is one which cannot be instantiated.</li>
<li>Method: A static method is one which is not tied to an instance of an object.</li>
<li>Variable: A static variable is one which is shared across instances of an object.</li>
</ul>
</details>

<br>

__Q:__ What do the 'public', 'protected', 'private', and 'internal' keywords denote?

<details>
<summary>Answer</summary> 
These keywords refer to the accessibility of their subjects:
<ul>
<li>Public: Anyone can access this from anywhere.</li>
<li>Protected: When present in languages, it usually means only child classes can access this, and they can do so from anywhere.</li>
<li>Private: Only this object can access this.</li>
<li>Internal: When present in languages, it usually means anyone can access this, but only from within this package/library.</li>
</ul>
</details>

<br>

__Q:__ What does being immutable entail, and what keywords can modify mutability?

<details>
<summary>Answer</summary>
If something is immutable then it cannot be changed.
<ul>
<li>The 'const' keyword can make its subject immutable at compile time (in addition to being static).</li>
<li>The 'readonly', when present in a language, can make its subject immutable at run time. Its value can still only be set once, and usually only in the constructor of a class.</li>
</ul>
</details>

<br>

__Q:__ What does the 'final' keyword denote?

<details>
<summary>Answer</summary>
When present in a language, it prevents a class or method from being inherited or overriden, respectively.
</details>

<br>

__Q:__ What is idempotence?

<details>
<summary>Answer</summary>
A function is said to be idempotent if repeated function calls with the same input will only change the state of the state of the application once.
<ul>
<li>For example: getting a value and setting a value are idempotent, the end result is always the same after the first call is made, regardless of repetition. However, adding to a list is not idempotent, because repeated calls to add will keep modifying the list further.</li>
<li>In mathematical terms, a function \\( f \\) is idempotent if \\( f o f = f \\).</li>
</ul>
</details>

<br>

__Q:__ What is lazy bind/loading?

<details>
<summary>Answer</summary>
Waiting until a resource is needed before you bind/load it.
</details>

<br>

__Q:__ What is reflection?

<details>
<summary>Answer</summary>
Code's ability to inspect itself or other code in the same program.
</details>

<br>

__Q:__ What are the 4 pillars of object-oriented design?

<details>
<summary>Answer</summary>
<ul>
<li>Abstraction: The process of showing only the necessary features of an object to other code.</li>
<li>Inheritance: The ability to make a hierarchy of classes wherein child classes acquire certain properties and behaviors of parent classes.</li>
<li>Polymorphism: The ability of a child class to both share and extend the properties and behavior of a parent class.</li>
<li>Encapsulation: The process of wrapping properties and behavior in an object so that access to each property and function can be controlled, and so that properties and behavior can be related to each other.</li>
</ul>
</details>

<br>

__Q:__ What's the difference between inheriting and interfacing?

<details>
<summary>Answer</summary>
Inheritance defines what an object is, whereas interfacing defines what an object can do.
</details>

<br>

__Q:__ What is a pure function?

<details>
<summary>Answer</summary>
A function with no side-effects that always returns the same output for a given input.
</details>

<br>

__Q:__ What is NP-Completeness?

<details>
<summary>Answer</summary>
A problem is said to be NP if it has a non-deterministic polynomial-time solution, and a problem is said to be NP-Hard if every NP problem can be transformed into it in polynomial time. For a problem to be NP-Complete means that it is both NP and NP-Hard.
</details>

<br>

__Q:__ What is a lock/mutex?

<details>
<summary>Answer</summary>
A mechanism for controlling access to a resource. Unlike semaphores, only one task can gain access to a lock/mutex at a time in order to access the resource.
</details>

<br>

__Q:__ What is a semaphore?

<details>
<summary>Answer</summary>
A variable used to signal the availability of a resource. Unlike locks/mutexes, a semaphore can allow multiple tasks to access a resource; a semaphore value of 0 indicates that no other tasks are allowed access to the resource, and a value of more than 0 allows that many more tasks to access the resource. Consequently, a binary semaphore (a semaphore only allowed to be 0 or 1) can be used to implement a lock/mutex.
</details>

<br>

__Q:__ Explain Agile software development.

<details>
<summary>Answer</summary>
Agile software development is a practice that promotes self-organization and cross-functionality within teams. It puts an emphasis on continual improvement and constant interactions with end users to be able to adjust the product as needed.
</details>
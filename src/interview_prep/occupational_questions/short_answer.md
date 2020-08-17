# Short Answer

Note: In addition to what is provided here, you may be asked questions about anything you have put on your resume (e.g. How does X work in the Y programming language?).

__Q:__ What is \\( 2^x \\)? Note: \\( x \\) will rarely be more than 12.

__A:__ 2, 4, 8, 16, 32, 64, etc.

<br>

__Q:__ What is the difference between a struct and a class, and what might you use a struct for? Note: This is somewhat language-dependent (not all languages even have both).

__A:__ Structs usually give their properties and methods public modifiers by default, and in some modern languages they represent value types as opposed to reference types. Usually structs are used for simple objects or types, which don't need complex methods. In general, a struct might be appropriate when the data type is going to be small, and either it is expected to be short-lived or it is expected to be frequently embedded in other objects.

<br>

__Q:__ What is a static class/method/variable?

__A:__
- Class: A static class is one which cannot be instantiated.
- Method: A static method is one which is not tied to an instance of an object.
- Variable: A static variable is one which is shared across instances of an object.

<br>

__Q:__ What do the 'public', 'protected', 'private', and 'internal' keywords denote?

__A:__ These keywords refer to the accessibility of their subjects:
- Public: Anyone can access this from anywhere.
- Protected: When present in languages, it usually means only child classes can access this, and they can do so from anywhere.
- Private: Only this object can access this.
- Internal: When present in languages, it usually means anyone can access this, but only from within this package/library.

<br>

__Q:__ What does being immutable entail, and what keywords can modify mutability?

__A:__ If something is immutable then it cannot be changed.
- The 'const' keyword can make its subject immutable at compile time (in addition to being static).
- The 'readonly', when present in a language, can make its subject immutable at run time. Its value can still only be set once, and usually only in the constructor of a class.

<br>

__Q:__ What does the 'final' keyword denote?

__A:__ When present in a language, it prevents a class or method from being inherited or overriden, respectively.

<br>

__Q:__ What is idempotence?

__A:__ A function is said to be idempotent if repeated function calls with the same input will only change the state of the state of the application once.
- For example: getting a value and setting a value are idempotent, the end result is always the same after the first call is made, regardless of repetition. However, adding to a list is not idempotent, because repeated calls to add will keep modifying the list further.
- In mathematical terms, a function \\( f \\) is idempotent if \\( f o f = f \\).

<br>

__Q:__ What is lazy bind/loading?

__A:__ Waiting until a resource is needed before you bind/load it.

<br>

__Q:__ What is reflection?

__A:__ Code's ability to inspect itself or other code in the same program.

<br>

__Q:__ What are the 4 pillars of object-oriented design?

__A:__
- Abstraction: The process of showing only the necessary features of an object to other code.
- Inheritance: The ability to make a hierarchy of classes wherein child classes acquire certain properties and behaviors of parent classes.
- Polymorphism: The ability of a child class to both share and extend the properties and behavior of a parent class.
- Encapsulation: The process of wrapping properties and behavior in an object so that access to each property and function can be controlled, and so that properties and behavior can be related to each other.

<br>

__Q:__ What's the difference between inheriting and interfacing?

__A:__ Inheritance defines what an object is, whereas interfacing defines what an object can do.

<br>

__Q:__ What is a pure function?

__A:__ A function with no side-effects that always returns the same output for a given input.

<br>

__Q:__ What is NP-Completeness?

__A:__ A problem is said to be NP if it has a non-deterministic polynomial-time solution, and a problem is said to be NP-Hard if every NP problem can be transformed into it in polynomial time. For a problem to be NP-Complete means that it is both NP and NP-Hard.

<br>

__Q:__ What is a lock/mutex?

__A:__ A mechanism for controlling access to a resource. Unlike semaphores, only one task can gain access to a lock/mutex at a time in order to access the resource.

<br>

__Q:__ What is a semaphore?

__A:__ A variable used to signal the availability of a resource. Unlike locks/mutexes, a semaphore can allow multiple tasks to access a resource; a semaphore value of 0 indicates that no other tasks are allowed access to the resource, and a value of more than 0 allows that many more tasks to access the resource. Consequently, a binary semaphore (a semaphore only allowed to be 0 or 1) can be used to implement a lock/mutex.

<br>

__Q:__ Explain Agile software development.

__A:__ Agile software development is a practice that promotes self-organization and cross-functionality within teams. It puts an emphasis on continual improvement and constant interactions with end users to be able to adjust the product as needed.
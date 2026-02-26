# Python Developer Interview Guide (1 Year Experience)

------------------------------------------------------------------------

# 1. Core Python Concepts

## 1.1 Mutable vs Immutable

Mutable objects can be changed after creation. Examples: list, dict, set

Immutable objects cannot be changed after creation. Examples: int,
float, str, tuple

Why it matters: - Mutable objects can cause side effects when passed to
functions. - Immutable objects are safer for multi-threading.

------------------------------------------------------------------------

## 1.2 is vs ==

== checks value equality. is checks memory identity.

Example: a = \[1,2\] b = \[1,2\] a == b -\> True a is b -\> False

------------------------------------------------------------------------

## 1.3 Deep Copy vs Shallow Copy

Shallow copy copies references of nested objects. Deep copy creates full
independent copies.

Use: import copy copy.copy() copy.deepcopy()

------------------------------------------------------------------------

## 1.4 Decorators

A decorator modifies behavior of a function without changing its code.

Example: def decorator(func): def wrapper(): print("Before function")
func() print("After function") return wrapper

Used in: - Logging - Authentication - Caching

------------------------------------------------------------------------

## 1.5 Generators

Generators use yield instead of return. They generate values one at a
time.

Benefits: - Memory efficient - Used for large datasets

------------------------------------------------------------------------

## 1.6 GIL (Global Interpreter Lock)

GIL allows only one thread to execute Python bytecode at a time.

Impact: - Threads are not truly parallel for CPU tasks. -
Multiprocessing is used for CPU-bound tasks.

------------------------------------------------------------------------

# 2. OOP Concepts

## 2.1 Four Pillars

1.  Encapsulation
2.  Abstraction
3.  Inheritance
4.  Polymorphism

------------------------------------------------------------------------

## 2.2 MRO (Method Resolution Order)

Defines the order in which base classes are searched when executing a
method.

Python uses C3 Linearization.

------------------------------------------------------------------------

# 3. Django / Flask

## 3.1 ORM

Object Relational Mapping allows interacting with database using Python
objects instead of SQL.

Benefits: - Cleaner code - Database abstraction - Prevents SQL injection

------------------------------------------------------------------------

## 3.2 Migrations

Migrations track changes in database models and apply them safely.

------------------------------------------------------------------------

# 4. Database Concepts

## 4.1 Indexing

Indexes improve query performance by reducing lookup time.

Trade-off: - Faster reads - Slower writes

------------------------------------------------------------------------

## 4.2 Normalization

Process of organizing data to reduce redundancy.

Normal Forms: 1NF, 2NF, 3NF

------------------------------------------------------------------------

## 4.3 ACID Properties

Atomicity Consistency Isolation Durability

------------------------------------------------------------------------

# 5. REST API Concepts

## 5.1 REST Principles

-   Stateless
-   Client-Server
-   Cacheable
-   Uniform Interface

------------------------------------------------------------------------

## 5.2 PUT vs PATCH

PUT replaces entire resource. PATCH updates partial resource.

------------------------------------------------------------------------

## 5.3 JWT Authentication

JWT = JSON Web Token

Used for stateless authentication.

Structure: Header.Payload.Signature

------------------------------------------------------------------------

# 6. Coding Round Important Questions

1.  Reverse a string
2.  Palindrome check
3.  Find duplicates
4.  Second largest element
5.  Two Sum problem
6.  FizzBuzz
7.  Count word frequency

------------------------------------------------------------------------

# 7. Time Complexity

Big-O Notation measures algorithm performance.

Common Complexities: O(1) - Constant O(n) - Linear O(n\^2) - Quadratic
O(log n) - Logarithmic

------------------------------------------------------------------------

# 8. Behavioral Questions

-   Explain your project architecture.
-   Describe a production issue you solved.
-   How do you optimize slow API?
-   How do you handle debugging?

------------------------------------------------------------------------

End of Guide.

The pitch
---------

### C++ - the Newest Old Language

C++ is an old language only used by the unfortunate few that absolutely have to, right?

Wrong!

C++ is not the language it used to be: clunky, error-prone and lacking in tooling. A lot has changed in the last decade: three new language revisions, new compilers and all-new tooling and diagnostics. Memory leaks and segmentation faults are all but a distant memory!

In this talk, Matt will cover some of the things that make C++ a great choice for a wide variety of applications. He'll cover the best of the new bits of the language, and demonstrate how modern tooling makes coding in C++ fun again.

The intended audience is both C++ folks who might want to catch up on the latest and greatest, but also anyone who think C++ is a write-off and isn't used any more.

Ideas
-----

* slot is 45 minutes, so I guess aim for 30m, plus 10-15 for questions?
* Needs a good call to action
* Needs good argument for "Why C++"



C++ !

* C++ is an old language!
  Nobody uses it, right?
* Stats/list of peope that use it!
* Are they crazy?
* No! C++ is a modern, evolving language. It's not what how you remember
  * Dinosaur graph strata of C++
* C++ is a good choice. You should check it out it has changed!
* Its strengths:
  * Value types
  * Clear object lifetimes -- RAII
  * Performance
    * Many zero cost abstratctions?
    * Don't pay for what you don't use

Value types
* Wrap meaningful types with useful behaviour over data. with *no* memory overhead
  Copied by VALUE - no funny reference semantics to worry about
  Works for small and large objects.
  Examples, Price, Qty
  Control how serialised, etc. Control if they can be copied at all (segue to move semantics?)
  Static typing though.

RAII/lifetime
* `FILE *f = fopen(...)` etc
* log enter/exit? stopwatch measurements?
* memory
  * `unique_ptr` `shared_ptr`
* How do I pass a uptr to someone? Can't! Useless? No! need to move!
* talk about it being a feature to reason about your lifetimes. shared`_`ptr smell?

Performance
* constexpr

And more!
* if constexpr
* if init
* constness of object?


NRVO?

------------------
When you think of C++ you might think:
show Dreadful code?
Not an attack on othr languages
What is it good for?
Examples (? how many are new vs old school)


Dinosaur image?
* C++ History
  * Pleistocene, c-front, 98, 11, 14, 17, 20?
* Pre '11
  * C++ the good
    * C compat/interop
    * Low level
    * Speed/intrinsics
  * C++ the bad
    * Macros, arcane knowledge
    * Memory leaks
    * Memory splats
    * Use after free
    * Threading pain
    * Arcane error messages?
    * (maybe find a slide of "bad code" to show how tricky)
* Enter C++ 11
  * Atomics
  * Rvalue refs
  * Lambdas
  * constexpr
  * Auto
  * UDLs
  * (library stuff?)
* C++14
  * Auto ret deduction
  * Generic lambdas
  * Init capture lambdas
  * Binary literals
  * (library stuff?) UDLs for string
* C++17 features
  * Library: optional, `string_view`, any, variant, byte
  * `if constexpr`
  * Template type deduction
  * Structured bindings
  * `[[fallthrough]]`, `[[maybe_unused]]` and `[[nodiscard]]`
* Tooling
  * Sanitizers ubsan, asan, tsan
  * IDEs
* C++ strengths
  * Not what you’d imagine!
  * Value types
  * RAII (need better name for this)
  * Forces you to think about lifetime. A feature!
  * “You only pay for what you use”
  * const-ness (const methods, const refs, constexpr)
* C++ weaknesses
  * Without discipline, some very sharp edges
  * No one true build system
  * No one true package management system
* Maybe a rant on `shared_ptr`?
* So who still uses C++?
  * Obvious stuff
  * JVM
  * v8
  * Chrome
  * clang & gcc
  * Low latency folks
  * Big data
  * low level access
  * games
* Would be nice to find an example snippet of code, showing how much better things get over time? "Make C++ fun again"
  * ray tracer? everyone loves that? threading, fast code, async await? `co_await` in 20 even?

```cpp
void add(Object obj); // I get an object, that's great. But concrete?
void add(Object &&obj); // This object is mine now, ownership transfer
void add(Object *obj); // copy? do I own? can it be null?
void add(Object &obj); // not null at least...I get to change it. who else has this?
void add(const Object &obj); // ok, fab I don't get to change it. Someone else might though...
void add(unique_ptr<Object> obj); // Aha! I get to own this
void add(shared_ptr<Object> obj); // Ok, I get to share this object, hope nobody changes it
void add(shared_ptr<const Object> obj); // wow that's great
```

# Scala Essentials for Data Engineers
* Understanding functional programming
* Understanding objects, classes, and traits
* Higher-orderfunctions (HOFs)
* Examples of HOFs from the Scala collection library
* Understanding polymorphic functions
* Variance
* Option types
* Collections
* Pattern matching
* Implicits in Scala

## Understanding functional programming
Functional programming is based on the principle that programs are constructed using only **pure functions**. A pure function does not have any side effects and only returns result. Examples of side effects are:
* modifying a variable
* modifying a data structure in place
* performing I/O

Example of pure function - length function on a string object. It only returns the length of the string and does nothing else.

Two important aspects of funcational programming are:
* referential transparency (RT)
* substitution model

### Referential Transparency (RT)
An expression is referentially transparent if all of its occurrences can be substituted by the result of the expression without altering the meaning of the program.

Example 1.1
```scala
scala> val x: String = "hello"
x: String = hello
scala> val r1 = x + " world!"
r1: String = hello world!
scala> val r2 = x + " world!"
r2: String = hello world!
```

if we replace x with the expression referred by x, r1 and r2 will be the same. So expression **hello** is referentially transparent.

```scala
scala> val x = new StringBuilder("who")
x: StringBuilder = who
scala> val y = x.append(" am i?")
y: StringBuilder = who am i?
scala> val r1 = y.toString
r1: String = who am i?
scala> val r2 = y.toString
r2: String = who am i?
```

If we substitute **y** with the expression it refers to (**val y = x.append(" am i?")**), **r1** and **r2** will no longer be equal

```scala
val x = new StringBuilder("who")
val r1 = x.append(" am i?").toString
val r2 = x.append(" am i?").toString
```

So, the expression **x.append(" am i?")** is not referentially transparent.

#### Advantages
* Allows you to apply local reasoning without having to worry about whether it updates any globally accessible mutable state.
* Since no variable in the global scope is updated, it considerably simplifies building a multi-threaded application.
* pure functions are also easier to test as they do not depend on ay state apart from the inputs supplied, and they generate the same output for the same input values.
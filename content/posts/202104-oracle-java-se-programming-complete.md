---
title: "Notes on Oracle's Java SE: Programming Complete"
date: 2021-04-03T15:00:00-04:00
toc: true
categories:
 - dev
tags:
 - training
 - java
 - Oracle
 - certification
---

These are the notes that I took while watching the [Oracle's Java SE: Programming Complete](https://education.oracle.com/java-se-11-programming-complete/courP_62197845) course, so I left out most of the things I already knew and noted things that raised an eyebrow.

Note that the course is currently [free for the 25 years of Java](https://education.oracle.com/java-25th-anniversary-discount-redemption).

## Preamble

Oracle indicates that this course prepares for the [Oracle Certified Professional: Java SE 11 Developer certification (1Z0-819)](https://education.oracle.com/oracle-certified-professional-java-se-11-developer/trackp_OCPJAV11).

For people new to Java and Programming, Oracle offers the free [Java Explorer learning path](https://learn.oracle.com/ols/learning-path/java-explorer/40805/79726).

## Course Overview

 The free course is a filmed presentation done by Vasily Strelnikov from Oracle who I thought presents really clearly and goes into the appropriate level of details to cover the program of the course. I have noted a couple of instances where he gets flustered and just goes back to the beginning of the sentence as if that would be edited out (turns out that did not) which I thought was funny.

1. [Introduction to Java](#introduction-to-java)
1. [Primitive Types, Operators, and Flow Control Statements](#primitive-types-operators-and-flow-control-statements)
1. [Text, Date, Time and Numeric Objects](#text-date-time-and-numeric-objects)
1. Classes and Objects
1. [Improved Class Design](#improved-class-design)
1. [Inheritance](#inheritance)
1. [Interfaces](#interfaces)
1. [Arrays and Loops](#arrays-and-loops)
1. [Collections](#collections)
1. [Nested Classes and Lambda Expressions](#nested-classes-and-lambda-expressions)
1. [Java Streams API](#java-streams-api)
1. [Handle Exceptions and Fix Bugs](#handle-exceptions-and-fix-bugs)
1. [Java IO API](#java-io-api)
1. [Java Concurrency and Multithreading](#java-concurrency-and-multithreading)
1. [Open Module Content](#open-module-content)
1. [Annotations](#annotations)
1. [Java Database Connectivity](#java-database-connectivity)
1. [Java Security](#java-security)
1. [Advanced Generics](#advanced-generics)
1. [Oracle Cloud Deployment](#oracle-cloud-deployment)

The free course has lab exercise sessions where the trainer presents exercises and code them live in NetBeans ("to keep things nihilistic"). The resource for the exercises (document, lab environment) are *not* accessible for free (they are available through [live virtual classes](https://education.oracle.com/java-se-11-programming-complete/courP_62197845)). Following those exercises using the filmed sessions from the free course and replicating what is going on in your environment is easy enough though. What you will need is: a JDK 11 installed, a text editor/IDE.

## Notes

### Introduction to Java
Java was originally designed as a language for consumer electronics (!).
The unit of code for Java is a *Class*, core concept in object-oriented programming, it will attributes, operations (method/function).
An *Object* is an instance of a Class (*RR: intriguing as it is also the name of the base class in Java*).

Subclasses *inherit* all attributes and behaviors from their parents and can define more specific attributes and behaviors, the purpose of this being code readability (avoids repeating logic). The JDK provides hundreds of classes for many purposes.

#### Java Keywords, Reserved Words and a Special Identifier
`true`, `false`, `null` are reserved words for literal values.

`strictfp` is mentioned as a reserved keyword but is not particularly covered. [It stands for strict floating-point (calculation)][1] and specifies that floating-point calculation in an annotated class (and its inheritors)/method/interface will be *platform-independent* (otherwise the JVM is free to use any extra precision available on the target platform hardware).

[1]: https://www.baeldung.com/java-strictfp

`const` and `goto` are reserved but the compiler will give an error if one tries to use them. Reserved keywords and literals cannot be used as identifiers.

`var` is a special identifier added in Java 10 (will be covered later on).

#### Create Main Application Class

The main entry point for executing a class `public static void main(String[] args)`.
```bash
javac -cp /project/classes -d /project/classes /project/sources/demos/Whatever.java
java -cp /project/classes demos.Whatever Jo John "A Name Jane"
```

Java 11 introduced being able to run single-file source code without having to compile: 
```bash
java /project/sources/demos/Whatever.java
```

#### Variable Names
Variable names forbid number as first character.
`$`, `_` can be used in addition to Unicode letters and digits characters (dollar and underscore are allowed if they are not the only character in the variable name, it is a convention to not use the dollar character).

### Primitive Types, Operators, and Flow Control Statements
Default values are applied to class attributes (which implies that variables always need to be initialized).

#### Operators
The tilde `~` operator is the bitwise complement unary operator: `~a` gives `-(a+1)`.

#### Using the Math class
`Math.round` rounding can handle octal, hexadecimal, ...

#### Flow Control Using if/else Construct
`else if...` does not have a particular meaning, it's just `else { if... }`.

### Text, Date, Time and Numeric Objects
`char` represents a character and is represented as code point/ASCII code/Unicode code.

For `java.lang.String` initialization, one should prefer double quotes vs. `new` because the former will leverage `intern()` for optimization (as opposed to recreating an object in memory).

One needs to be careful when choosing to use a wrapper class or a primitive type in particular with respect to auto-boxing, auto-unboxing.

I like the Date and Time API `java.time` a lot \o/ especially since it comes with immutability!
`java.time.Duration` represents an amount of time in nanoseconds, `java.time.Period` represents an amount of time in a given unit.

`Locale` uses ISO 639 languages and ISO 3166 or country codes, UN M.49 area codes ("029" Caribbean!) through `Locale.forLanguageTag(...)`.

Localizable Resources are grouped as Bundles which are reflected as a group of properties file such as:
* messages.properties
* messages_en_GB.properties
* messages_ru.properties

### Improved Class Design

* Overload: same return type/method names, different types/number of arguments (used to provide flexibility)
* Encapsulation: embed complexity within an object (method calls/logic) using access modifiers.
* Immutability: immutable object = read-only data, are thread-safe (would have said that it provides simplicity in designs)

#### Instance Initializer!
```java
public class Product {
    private static int maxId = 0;
    private final int id;
    private final String name;
    {id = ++maxId;}
    public Product(String name) {
        this.name = name;
    }
}
```
Use cases for instance initializers: https://softwareengineering.stackexchange.com/a/238824/83953

#### Enums
enum literals are instances of an enum type!
enum constructors must have default/private access.

#### Java Memory
Stack is a memory context of a thread, may contain only primitive and object references.
Heap is a shared memory area (has class instances).
Object references are not memory addresses but logical identities instead.
Calling a method passes value (the reference);
https://www.infoworld.com/article/3512039/does-java-pass-by-reference-or-pass-by-value.html
https://stackoverflow.com/a/430958/618156 (pass by reference means: instead of a copy, it is the actual object that is passed in the method call, in newer languages it is obsolete).
Garbage collection is deferred but is done by counting references to objects in heap and cleaning up when there is no longer references to the objects. There is an algorithm for when to trigger the actual garbage collection.

### Inheritance
`child instanceof Parent` returns `true`.
`null instanceof X` always returns `false`.

*Polymorphism* means that when a method is declared in a superclass and is overridden in a subclass, the subclass method takes precedence without casting reference to a specific subclass type (*RR: actually Polymorphism is [larger than this](https://en.wikipedia.org/wiki/Polymorphism_%28computer_science%29), this definition encases both overloading AND overriding*). It simplifies coding (*RR: hmm... it is true compared to checking class and casting*).

The rules for overloading precedence is to go with the closest matching first, see https://stackoverflow.com/a/22591077/618156

`@Override`/Polymorphism can widen the access-level not narrow.

`private abstract`: gives a compiler error.

`hashCode` should return an `int` representing the identity of the Object. If the `equals` method returns true then the `hashCode` should be the same, it must consistently return the same `int` value for the same instance. (*RR: so it should not depend on properties that can change*). If security is necessary one can use secure hashing (`Objects.secureHash()`).

`String` is the only Java object that allows simplified instantiation.

The *Factory* method pattern can hide the use of a specific constructor (dynamically chooses subtype, invoker can remain subtype-unaware, which implies adding new subtypes does not impact invokers).

### Interfaces
Interfaces are similar to `abstract` classes except they can have no variables and no regular concrete method (as opposed to default).
They provide a workaround to object-oriented inheritance which is not very flexible ("how does one choose which parent class's implementation to use? how is it handled in other languages?").
In the case of multiple implemented interfaces, you *have* to override the method.
`private static` methods are allowed.

Generics (Java SE 5) are often used together with Interfaces, provide compile-time type safety. They allow saving effort on type-checking/casting.

`java.lang.Cloneable` is an example of Java interface, it does not have a method defined but `Object.clone()` will check `this instanceof Cloneable`!

The *Composition* pattern allows combining features of multiple classes (working around multiple inheritances which is not allowed).

`@FunctionalInterface` is an annotation that can be used to mark an interface that strictly has one abstract method (can have private/default methods). It allows being provided as a lambda.

### Arrays and Loops
`int[] primes;` or `int primes[];` both work for array declaration!
`Arrays.copyOf` will not not truncate the source array!

In the `for` loop, semi-colons are used to separate declaration, termination condition and iterator. Each of these is optional!
*forEach* is not actual operator or a reserved word but a name that describes a `for` loop that iterates through the array or collection without a need to maintain an index and iterator logic.
More complex `for` loops are possible using multiple declarations for iterators, each separated by a comma.

### Collections
`Deque` is a double-ended queue: first in, first out AND last-in, first-out.

`List.of(...)` vs `Arrays.asList(...)`, the former creates a read-only list (`set(index, ...)` are prevented, it is allowed with `Arrays.asList`).
`add` shifts subsequent elements (`set` to overwrite).
`remove(index)`, `remove(Object)` (removes the first occurrence only).
`indexOf`, `contains`, `get`.
`add(index, Object)` does not allow jumping positions.

The load factor of a `HashSet` instance is configurable: uniqueness uses `hashCode`, buckets are used for performance.

`Deque`, `ArrayDeque` have the following methods `offerFirst` (/`addFirst`), `pollFirst` (get) (/`removeFirst`), `peekFirst` (get but leave it) (/`getFirst`), `offerLast`, `pollLast`, `peekLast`; both implement `Queue` (there is also the legacy `Stack` class).

`Map` has similar methods `Map.of`, `Map.ofEntries(Map.entry(...))`.

#### Thread Safety
*Threads* represent concurrent execution paths.
Thread safety is needed to prevent the corruption of a `Collection`: a thread could be modifying an object and other threads could be observing an incomplete modification state.
If the collection is read-only then they are thread-safe.
To achieve thread safety, there are multiple strategies: we could make the collection synchronized but this is slow and unscalable and also one needs to be careful when looping over the collection.
Making the collection copy-on-write is fast but consumes memory (merges if concurrent modification and handles conflict).

`int[]` is an object and is a valid type (usable as generics).

### Nested Classes and Lambda Expressions
*Nested Classes* constrain the context of their use.
*Member Inner Classes* are associated with the instance context of the outer class.
*Local Inner Classes* are defined in the context of a method, can access local variables / parameters if they are final or effectively final. The use case for these is that they help if the logic should be encapsulated, but one does not want to reuse the logic anywhere else.
*Anonymous Inner Class* are local inner classes that are not named.

A *Lambda expression* is an inline implementation of a functional interface, '`->`' is named lambda token.
Modifiers are applied using specific/locally inferred types.

### Java Streams API
A `Stream` is an *immutable* flow of elements. (*RR: the reason for it: the flow of elements does not change*) but it may represent both finite and *infinite* flows of elements (!).

`DoubleStream`, `IntStream`, `LongStream` avoid unnecessary boxing, unboxing.
Parallel processing is not enabled by default, because not all `Stream` operations are suitable. `Stream` go through pipeline-like processing operations: some are deemed intermediate, others are terminal.

`mapToInt`, `mapToLong`, `mapToDouble` are used to map Objects to primitives.

If one uses `distinct()` before/after calling `map(...)` transforms stream elements then most likely when it is called matters (the documentation indicates `distinct()` is stateful).
`collect(T identity, BiFunction accumulator, BinaryOperator combiner)`: the `combiner` input argument is the function for combining mapped elements (useful for parallel streams).

### Handle Exceptions and Fix Bugs

#### Java Logging API
`java.util.logging.Logger`
```java
module demos {
    requires java.logging;
}
```
Levels go from `SEVERE` to `FINEST`. `logp` allows providing a source class and method name, `logrb` allows providing a resource bundle. Also methods `entering`, `exiting`, `throwing` exist.

Socket logging allows [logging through a network](https://blogs.oracle.com/corejavatechtips/socket-logging).

The Java Logging API is configured through a `logging.properties` file where the root logger is defined as `.level=INFO`.

`Logger` by convention is defined for each class.
`Handler` (*RR: comparable to Log4J `Appender`*) can each have a different destination, can each have a different formatter.

`catch` of a specific exception handler must be placed before generic handler (otherwise the compiler complains).

#### Handling exceptions
`Throwable` is extended by `Error` which differs from `Exception` by the fact that one should not try to catch the former. `Exception` "usually represents genuine problems that a normal functioning program may encounter and thus must be caught". `RuntimeException` "is often an evidence of a bug in one's code, which should be fixed rather than caught".

Auto-closure may produce suppressed exceptions: the `close` method might throw an exception:
if the close fails then an exception might be thrown but if an exception is thrown in the try then the ones thrown by calls to the `close` method are suppressed and are accessed through `Throwable[] suppressedExceptions = ex.getSuppressed();` from the `catch` block.

Assertions are used to *test* the validity of an algorithm: this explains that they are *not* enabled by default.

### Java IO API
`ObjectInputStream` / `ObjectOutputStream` are used for Object deserialization/serialization.

`InputStream` / `OutputStream` are used for a byte representation of data whereas `Reader` / `Writer` are for characters.

Piping an input stream to an output stream can be done through `InputStream#transferTo(OutputStream)`.
```java
try (InputStream in = new FileInputStream("some.xyz"),
     OutputStream out = new FileOutputStream("other.xyz")) {
    byte[] buffer = new byte[1024];
    int length = 0;
    while ((length = in.read(buffer)) != -1) {
        out.write(buffer, 0, length);
    }
} catch (IOException e) { /* logic handling exception here */}
```

```java
Charset utf8 = Charset.forName("UTF-8");
try (Reader in = new FileReader("some.xyz", utf8),
     Writer out = new FileWriter("other.xyz", utf8)) {
    char[] buffer = new char[1024];
    int length = 0;
    while ((length = in.read(buffer)) != -1) {
        out.write(buffer, 0, length);
    }
} catch (IOException e) { /* logic handling exception here */}
```

`InputStreamReader` / `OutputStreamWriter` bridge character streams and byte streams. The former is a `Reader` in that provided with a byte stream it can generate characters. The latter is a `Writer` in that provided with a character stream it will generate a byte stream. Apache Commons has `ReaderInputStream` and `WriterOutputStream` but ["very often the need to use [these classes] is an indication of a flaw in the design of the code. [These classes are] typically used in situations where an existing API only accepts an InputStream or OutputStream)"](https://commons.apache.org/proper/commons-io/javadocs/api-2.5/org/apache/commons/io/input/ReaderInputStream.html).

`java.util.Scanner` / `java.io.Console` allow interacting with `System.console()` if one is available.

Serialization allows swapping objects/sending across network, but should not be used for long-term storage because the object representation may change.

The `transient` keyword is a variable modifier used to indicate that a variable will not be serialized. `Serializable` is a *marker* interface. Serialization uses reflections so logic in accessors/constructors will be skipped.

For serialization one can generate and use a secure object hash instead of writing the serialized object directly. A step-by-step is: serialize object, get a byte array, generate digest out of array `MessageDigest md = MessageDigest.getInstance("SHA-256"); String hash = new BigInteger(1, md.digest(byteArrayStream.toByteArray())).toString(16);`.

Private methods `writeObject`, `readObject` allow performing custom actions when serializing/deserializing. For instance: `transient` attributes can be set there.
`ObjectInputStream`/`ObjectOutputStream` will use those methods using reflection. `private static final long serialVersionUid = 1L;` is used for the version comparison, but it is not mandatory: when a serializable class evolves, one expects this value to change (*RR: because of course it will... not*).

#### `java.nio.file`
`java.io.File` is legacy.

* `Path` represents files and folders.
* `Files` is for operations on these path objects.
* `FileSystem` is for the overall filesystem.
* `FileStore`: represents a storage pool, device, partition, volume, concrete file system or other implementation specific means of file storage.

One should delete temporary dir/files before using them!

Zip archives can be defined as filesystem but writing is not implemented to compress resources.

### Java Concurrency and Multithreading)
Thread is an execution path. `new Thread(la).start();`
Threads can implement handling the interrupt signal: `Thread.currentThread().isInterrupted()`.

The `synchronized` keyword can put a thread in the blocked state (the first thread locks, the second thread is blocked until the first thread releases the lock).

Making a thread wait: `obj.wait()`, they'll need to be notified through `obj.notify()`. Multiple threads waiting will need to each be notified or be notified altogether through `obj.notifyAll()`.

*User (default)/Daemon* threads: as long as one user thread is still running, the JVM waits after it. The JVM can exit when daemon threads run.

* `java.util.concurrent.Executors` provide thread management automations using different `ExecutorService` objects.
* `ExecutorService.shutdown()`: stop accepting new tasks.
* `ExecutorService.awaitTermination()`: grace period, might throw `InterruptedException`, ...
* `ExecutorService.shutdownNow()`: terminate execution.
* `Callable` vs `Runnable`: the former returns something => `ExecutorService.submit()` (vs. `ExecutorService.execute()`), obtained through `Future`.

Funny fact: *Deadlock*: two or more threads are blocked forever, waiting for each other. http://en.wikipedia.org/wiki/Deadlock. *Livelocks* are a special case of resource *starvation*: they are not dead/blocked because they can act but one thread acting causes another thread to stop etc.

The `volatile` keyword means that there will be no caching in a local stack, and updates are always run from the main memory, apply all changes to the main memory that occurred in a thread before the update of the `volatile` variable. Even with `volatile` , it is not possible to predict when the shared heap object is updated.

An action is *atomic* if it is guaranteed to be performed by a thread without interruption which means it cannot be interleaved.
Assignments and usual operations are not atomic.
The `java.util.concurrent.atomic` package provides classes that implement lock-free thread-safe programming of atomic behaviors on single variables. They behave as if they were volatile.

`synchronized(list)` and `Collections.synchronizedList(list)` are almost the same but reading through the list still requires an explicit synchronized block.

A non-blocking concurrency automation is implemented by `CopyOnWriteArrayList` for instance: it is best suited for small collections where read-only operations vastly outnumber mutative operations and it prevents interference among threads during traversal.

Alternative locking mechanisms are available in `java.util.concurrent.locks`: for instance `ReentrantReadWriteLock` pauses whoever reads when writing.

In the exercise: Java EE has implementations of *Stateful* (per thread instances), *Singleton* (one instance multiple threads).
`ConcurrentHashMap` does not do the job: subsequent calls to `remove`/`add` are not thread-safe which explains why one should then use read/write locks.

### Open Module Content
The legacy implementation is that jar files can optionally contain a `MANIFEST.MF` file.

A *Module* is high-level code aggregation.
It is defined in a `module-info.java` (`.class`) file which allows the following keywords:
* `requires [transitive|static] <other module names>`,
* `exports <packages of this module to other modules that require them>`,
* `opens  <packages of this module> to <other modules via reflection>`,
* `uses <services provided by other modules>`, 
* `provides  <services to other modules> with <service implementation>`,
* `version`.

`requires static` can be used for optional dependencies for instance (the dependency is provided at runtime).
`opens ...`: Module containing injectable code should use the `opens` directive because injection works via reflection.

*RR: In a given application, how many `module-info` do you actually need? At least one, as many as the number of 'modular components' that one can define I guess.*

`open module` opens everything.

To load an implementation, one is expected to use `ServiceLoader`:
```java
ServiceLoader<L> sl = ServiceLoader.load(L.class);
```

Multi-release module archives allow supporting different versions of Java: the module root directory may contain either a default version of the module or a non-modularized version of code to be used by Java versions prior to 9.
Versioned descriptors are optional and must be identical to the root module descriptor with two exceptions: they can have different non-transitive requires clauses, they can have different use clauses.
```bash
javac --module-path
jar --create -f --main-class <...> -C <...>
java --module-path <...> --describe-module <...>
```

Non-modular JARs are treated as automatic modules. By default the module's name is the JAR file name. To avoid naming clash, one can specify the automatic module name in `MANIFEST.MF`.
Modular JARs located via class path are treated as non-modular for backward-compatibility. Unnamed modules are a temporary solution for the transition to JPMS.

`jlink` allows creating Java Runtime Image which is a self-contained application in a folder: optimized for space and speed, enables faster search and class loading. The application deployment footprint should be dramatically optimized. Optimization can go further by producing platform-specific images.

### Annotations
`SOURCE` is retained in the source code.
`CLASS` is retained by the compiler.
`RUNTIME` is retained by the JVM.

Annotations can be applicable to:
* `ANNOTATION_TYPE`
* `CONSTRUCTOR`
* `FIELD` (includes enum constants)
* `LOCAL_VARIABLE`
* `METHOD`
* `MODULE`
* `PACKAGE`
* `PARAMETER`
* `TYPE`
* `TYPE_PARAMETER` (generics)
* `TYPE_USE`

`@Repeatable` allows repeated use of the annotated annotation.

Annotations are not inherited by subclasses except if annotated with `@Inherited`.
`@Documented` means that the annotation will show up in the generated javadoc.

`@SafeVarargs` suppresses the heap-pollution warning which might occur in the case of a vararg of generics (because there will actually be no constraint on generics for array elements).


### Java Database Connectivity
```java
try (Connection connection = DriverManager.getConnection(...);
Statement statement = connection.createStatement();
) {
    String query;
    boolean isQuery = statement.execute(query);
    // select query
    // ResultSet results = statement.executeQuery(query);
    // anything else
    // int rowCount = statement.executeUpdate(query);
    boolean isQuery = statement.execute(query);
    if (isQuery) {
        // should be closed
        ResultSet results = statement.getResultSet();
    } else {
        int rowCount = statement.getUpdateCount();
    }
}
```

The interface `java.sql.PreparedStatement` represents pre-compiled SQL statements. It uses 1-indexed parameters (!). `java.sql.CallableStatement` is used for stored procedures or functions.

Transactions (by default connections are in auto-commit mode, `connection.setAutoCommit(false); connection.commit(); connection.rollback();`). Normal closure will commit.

`ResultSetMetaData = ResultSet.getMetaData();` gives `ResultSetType`, `ResultSetConcurrency`, `ResultSetHoldability` which are three properties related to isolation.

### Java Security
Can define `java.policy` files which grant permissions to resources. `java.security.Permission`

```java
DocumentBuildFactory factory = DocumentBuilderFactory.newInstance();
factory.setFeature(XMLConstants.FEATURE_SECURE_PROCESSING, true);
```

### Advanced Generics
You can assign `Drink` to a `Product` array but will get `java.lang.ArrayStoreException` from the runtime if the `Product` array was initialized with `Food` (sibling): arrays are covariant (arrays of a subtype can be assigned to an array of the supertype).

The *Collection API* use generics that are invariant (the collection can only be assigned with a collection of the declared type): code is validated at compile time. Compiler checks are not performed for raw types though.

Mnemonic: **PECS: Producer Extends Consumer Super**

The wildcard <?> type means unknown type: elements are accessed just like in a collection of objects, will effectively be a read-only collection: no value (except `null`) can be added to such a collection, because there is no object of unknown type.

`List<?> listOfUnknownType = listOfProducts;` such an assignment is covariant :-o.

*Upper Bound Wildcard* => makes code into covariant code.
`List<? extends Product>` can be assigned with a subtype collection but will be read-only.

*Lower Bound Wildcard*:
`List<? super Food>` shows the use of contra-variant generics: is writable ie. can be added with `Food`, `Product`, `Object`. *RR: Once you have that, what would one do with these (since you are not able to read)?*

### Oracle Cloud Deployment
This section demonstrates how one can leverage the Oracle tools for cloud deployment:

 * Select transport protocol
 * Decide upon message format
 * Enable application to accept remote requests and produce responses
 * Consider mechanisms to handle concurrent invocations
 * Managing application lifecycle and availability

For instance an architecture could be:
* Host > JVM > Java Server > Application
* Alternatively Host > Docker Container > JVM > Java Server > Application

The following web servers could be considered:
Java EE Server (WebLogic) | Java SE (Helidon (Web server)) | Java MP Server (Helidon)

JImage is an ensemble of files packaged using JLink.
So an architecture for packaging and deploying on the cloud could be: JImage > JVM > jar > server. Alternatively for Java EE: JVM > server > ear

## Final Thoughts
The course covers a good number of topics and is quite adapted to anyone with some knowledge of programming that wants to 'get started' with Java.

The notes that I have taken give a fragmented view of that 30-hour-long course.

<!---
* It is interesting that [JavaFX](https://openjfx.io) is not covered in the course since it has been available since Java 11. The reason must be that it would make the course even longer.
* Why do `while`,... code blocks not end with semi-colon the same as all statements?
* Can't wait for `switch` expression; which java version already?
* Read on FileChannel (what are those already?) 
https://learn.oracle.com/ols/course/practice-exam-java-se-certification/82508/79944/110343#

Need to read on jdeps java.base `order -> java.base` (dependent -> dependency)
Joda Time vs Java Time...
* Resource Bundle priority: the most specific first then incrementally more generic then fallback to the system's default Locale then the 'plain' resource (see https://docs.oracle.com/javase/tutorial/i18n/resbundle/concept.html). Now, the resolution for specific properties will use inheritance (look up the property in the chain of resources), see https://stackoverflow.com/a/55901930/618156.
* `StringBuilder` is not thread-safe because thread-safety is not available by default (why mobilize the resource?).
* Package-private classes are accessible to class in the same package even if in a different filesystem/resource https://stackoverflow.com/a/30436658/618156, but for modules: two modules with the same name cannot coexist: https://stackoverflow.com/a/46574200/618156.
* Check the Object-Oriented Analysis and Design Using UML course
* Child classes are more specific in the sense that they will not share their behavior with sibling classes.

* Casting to a more specific class but in a different hierarchy gives what kind of error? I think it occurs at runtime (not at compilation)
* `Map<? extends Class<?>, Map<UID, ? extends Class<?>>>` same type for the key and the value of the nested maps, how do you handle that?
* Example of Interface + Generics usage: How do you implement `Comparable<T>` that allows comparing a class and its subclasses (current object - parameter object negative = less than, zero = equal to, positive greater than). `Comparator<T>`.
* `Product implements Rateable<Product>`, how does one make this evolve to something that constrains to `ChildClass implements Rateable<ChildClass>`?
* What is `enum`? a keyword. What is an enum? What is an enum type? the 'class'.
* `Arrays.binarySearch(array, value)` https://www.baeldung.com/java-binary-search
* `Iterable` allows iterating and that is it. `Collection` has methods to modify the group of objects it represents.
* `InputStreamReader` / `OutputStreamWriter` bridge character streams to byte streams. Why isn't there something reverted (Apache Commons has it)?
* How do you make something modular compatible with something that's not?
* How do the `opens` `exports` `requires` actually work in the background?
* maven jlink plugin? how does one deploy that?
* How do annotations for modules work?
* How do annotations for packages work?
* How does one protect against people providing `../somepath`?
* Why did I look into `-Xverify:none` or `-noverify` command-line arguments already?
* What would the project gain from Java MP Server? + Modularization? (how does one determine the size of a Docker image?)
-->
---
title: "Java Versions: My Favorite Features"
date: 2021-05-15T14:20:00-04:00
categories:
 - dev
tags:
 - java
series:
 - java features
---

Ever since I tried my hands at the [Java 25th year anniversary Oracle SE 11 Certification](https://education.oracle.com/java-25th-anniversary-discount-redemption),
I wanted to start by listing the features that I like best (or actually just use with intent) and which version (> 8) of Java is associated to those.

## Java 9: An Unfortunate Feature Naming

Am referring to...

Java 9 - Java Platform Module System, `jlink`
: Though rather controversial, modularization serves strong encapsulation and associated to `jlink` is associated to reduced-size distributable runtime applications.

Java 9 - private interface method
: `default` has been a great addition to Java 8, being able to share logic between default methods prevents code duplication which is always great!

I find `jshell` a bit gimmick-y but that probably is because I am used to shells in general.

## Java 10

Java 10 - `var` keyword
: Inferring the type of local variables has the following most obvious benefit:
```java
// Before
VeryLongOrSubjectToChangeClassName variableName = new VeryLongOrSubjectToChangeClassName(...);

// After
var iAmSuchAVeryLongVariableName = new VeryLongOrSubjectToChangeClassName(...);
```
...  but that can lead to funky scenarios such as anonymous class tricks, see https://nipafx.dev/java-var-anonymous-classes-tricks/.

## Java 11
Java 11 - Extending `var` to Lambda Parameters
: The declaration of the type for lambda parameters is only needed in some scenarios but in those you can now use the `var` keyword.
```java
// Before
import java.awt.*;
import java.awt.event.*;

...

Button button = new Button("Click me!");

// Before (yes, you need parentheses)
button.addActionListener((final ActionEvent actionEvent) -> ...);

// After
button.addActionListener((final var actionEvent) -> ...);
```

### Want to read further?
See https://www.marcobehler.com/guides/a-guide-to-java-versions-and-features, https://dzone.com/articles/a-guide-to-java-versions-and-features or https://en.wikipedia.org/wiki/Java_version_history for instance.


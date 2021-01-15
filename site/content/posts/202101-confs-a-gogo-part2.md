---
title: "January 2021 - Conferences A Gogo - Part 2"
date: 2021-01-15T09:09:30-05:00
# draft: true
categories:
 - dev
tags:
 - conferences
 - webinars
 - java
---

This is the second entry to the [series for the January 2021 online conferences](/posts/202101-confs-a-gogo-part1/) which I have attended. 

Today is DawsCon! I had the pleasure to attend [Ken Fogel](https://twitter.com/omniprof)'s talk at the Montreal JUG[^1].

[Venkat Subramaniam - Keynote - This Ain’t Your Parents’ Java](https://youtu.be/tgLNh6_vNFk)
: Cool hands-on review of how Java has evolved in terms of features.

[Simon Ritter - Java at Speed: Building a Better JVM](https://youtu.be/nA8yxwzzhgM)
: Very articulate and in-depth view of Java Virtual Machine optimizations (implemented in [Azul Zing®](https://www.azul.com/resources-hub/data-sheets/zing-data-sheet-8-19v1)).

[David Delabassée - Java and the 40 versions – January 2021 Edition](https://youtu.be/RbxkeTn7aUI)
: Gives a view on the OpenJDK 6-month release process and then the newly-added features in the latest versions of Java.

[Mary Grygleski - Thirst-Quenching Streams for the Reactive Mind](https://youtu.be/JeDgzD5DVU8)
: Reactive development

[Billy Korando - Upgrade Your Automated Tests with JUnit 5](https://youtu.be/VNEWnLveBoo)
: Hands-on and neat features brought by JUnit 5. Thanks to Billy, I realized that [contrarily to what the Maven surefire plugin doc indicates](http://maven.apache.org/surefire/maven-surefire-plugin/examples/junit-platform.html#Running_Tests_in_Parallel) running parallel tests works, it just needs to be configured by setting [`<configurationParameters>`](https://maven.apache.org/surefire/maven-surefire-plugin/examples/junit-platform.html#Configuration_Parameters). Also, I see that fluent assertions as is done in [Assertj](https://assertj.github.io/doc/) is not one of those new features :pensive:

[^1]: [Meetup Page](https://www.montreal-jug.org/meetup/java-programming-best-practices/) and [Java Programming Best Practices on YouTube](https://youtu.be/Jgr8lFU3gMA)
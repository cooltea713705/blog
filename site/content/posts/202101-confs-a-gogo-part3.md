---
title: "January 2021 - Conferences A Gogo - Part 2"
date: 2021-01-18T15:17:30-05:00
# draft: true
categories:
 - dev
tags:
 - conferences
 - webinars
 - java
---

This is the third entry to the [series for the January 2021 online conferences](/posts/202101-confs-a-gogo-part1/) which I have attended.

Back to jChampions!

[Rafael Del Nero - Duke’s Star Trek with Java 15 Code Challenges](https://youtu.be/Poy4cQbo4_g)
: Fun code puzzles presenting features per JDK version. The sources are available at https://github.com/rafadelnero/startrek-javachallengers

[Nikhil Nanivadekar - Getting Started with Kafka](https://youtu.be/zbuAu3ap-ik )
: Hands-on of [Kafka](https://kafka.apache.org)

[Mohamed Taman - Do you use the Optional class as it should be?](https://youtu.be/5kdBZsB563A)
: Best practices for the `Optional` API. I caught on an error in [Code Recipe #10](https://youtu.be/5kdBZsB563A?t=1753) where [`Optional#orElseGet(...)` is not expected to return `Optional.<String>of(...)`](https://docs.oracle.com/en/java/javase/15/docs/api/java.base/java/util/Optional.html#orElseGet(java.util.function.Supplier)), the use of `Optional.or` is correct though.
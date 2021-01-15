---
title: "January 2021 - Conferences A Gogo - Part 1"
date: 2021-01-14T16:10:36-05:00
categories:
 - dev
tags:
 - conferences
 - sessions
# https://www.markdownguide.org/extended-syntax/#definition-lists
---

There are Java developer events all the time, except when they decide to put them all together in a week. :persevere:

So I have registered to [jChampions](https://jchampionsconf.com), [VJUG](http://virtualjug.com)'s talk by Victor Rentea, and [DawsCon](https://www.dawsoncollege.qc.ca/dawscon/). Here are my main takeaways for the sessions that I have actually watched (more or less).

[Richard Warburton - Continuous Profiling in Production: What, Why and How](https://youtu.be/nUwujM7fitE)  
: Profiling in production: what a weird idea! How does one do that? *Statistical* profiler (low overhead) and profile *continuously* (as opposed to ad hoc). To be investigated and tried in practice.

[Gail & Paul Anderson - It's How We Play the Game - JavaFX and GraalVM](https://youtu.be/dGdzM4K1zoQ)  
: Demo/hands-on of [Gluon](https://gluonhq.com) which offers multi-platform JavaFX. Have to say that while rather cool, I have my doubts with multi-platform development in general.

[Mario Fusco - Let's make a contract: the art of designing a Java API](https://youtu.be/6yW-Va1tfLI)  
: Best practices for (Java) API design: dogfeed these APIs as much as possible, `Optional` might be [the mother of bikeshedding](https://stuartmarks.files.wordpress.com/2017/03/optionalmotherofallbikesheds-devoxxbe2016.pdf)[^1] :laughing:. The talk is opinionated (Mario underlined that a couple of times) which is good!

[Victor Rentea - Don't Be Mocked by your Mocks: Listening to your Tests](https://youtu.be/pKBjufM024U)  
: Best practices for the use of mocks, mainly: don't use them except when for legacy code, external systems/libraries, slow/unreliable resources, well defined roles (component/interface with a separate role). Really interesting and would be great to implement.

[Ian Darwin - Flutter is the new Java - or is it?](https://youtu.be/0A1YZAz073w)  
: Hands-on with Flutter which offers a multi-platform development using Dart. Again, I'm meh with multi-platform development.  

[Henri Tremblay - (Let's) Refactor Together](https://youtu.be/hTnrEepswjc)  
: Live refactoring examples. The Q&A at the end is the most interesting part (a bit redundant with Victor's talk about mocks earlier).

[^1]: Bikeshedding = [Arguing for an infinite amount of time on the most trivial matter](https://exceptionnotfound.net/bikeshedding-the-daily-software-anti-pattern/)
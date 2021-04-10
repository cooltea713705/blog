---
title: "Oracle Java SE 11 Developer Certification"
date: 2021-04-09T16:00:00-04:00
toc: true
categories:
 - dev
tags:
 - training
 - java
 - Oracle
 - certification
twitterfeedback: 1380616619962023950
---

I earned the title of [Oracle Certified Professional: Java SE 11 Developer](https://education.oracle.com/java-se-11-developer/pexam_1Z0-819) yesterday! Allow me to present how I got there.

I have mostly been a Java developer since 2011. While looking for a new position, I realized that even if my past experiences taught me a lot, I did not have many quantitative achievements to show. When I saw [Oracle University](https://education.oracle.com)'s announcement that [the certification was discounted to 25 USD for the 25 years of Java](https://education.oracle.com/java-25th-anniversary-discount-redemption), I figured that it would be a cool opportunity especially after [having read the renowned Mala Gupta's (from JetBrains) experience with the Java Programmer certification](https://blogs.oracle.com/oracleuniversity/mala-gupta-success-story-v2).

## 'Oracle Certified Professional: Java SE 11 Developer': What's that?

It is a title (previously also named SCJP or OCJP as in Sun/Oracle Certified Java Programmer) from the [Oracle Certification Program](https://en.wikipedia.org/wiki/Oracle_Certification_Program). It is associated to the [certification exam 1Z0-819](https://education.oracle.com/products/trackp_OCPJAV11).

### More Details About the 1Z0-819 Exam

From the [description page](https://education.oracle.com/products/trackp_OCPJAV11), candidates have *90 minutes* to answer *50 multiple choices questions*. It replaces the *Java SE 11 Programmer I* (*1Z0-815*) and *Java SE 11 Programmer II* (*1Z0-816*) exams which are being retired. In [Oracle's exam overview 'course'](https://learn.oracle.com/ols/course/prepare-for-java-se-certification/82508/79482), it is said that this exam is for "Java developers" (among others) and it is recommended that one has "acquired 12-24 months of industry experience". Even if I have read accounts of students passing the exam (which I think is cool!), I would still go with that recommendation if not just because your employer might pay for your training.[^1]

[^1]: I see "Employers paying for a certification" as a win-win scenario since you get a certification and they get a trained employee. Also the regular price might deter individual attempts.

The exam sessions are organized by [Pearson VUE](https://home.pearsonvue.com/Clients/Oracle.aspx) which has a whole process for doing it at home: more on that further down.

## How did it go?

It took about a bit more than a month overall to get the certification. What I did was:
* follow [Oracle's learning path for Java SE 11 Developer](https://learn.oracle.com/ols/learning-path/java-se-11-developer/40805/79141)
  * it encompasses [studying the Java SE 11: Programming Complete course](/posts/202104-oracle-java-se-programming-complete/) (free at the time, alternatively Oracle has [paid learning subscriptions](https://education.oracle.com/java-programming-learning-subscription/ls_40805))
  * I used the [Forest app](https://www.forestapp.cc) to focus on my learning.
* read online resources about the exam
  * I have found [Scott Selikoff and Jeanne Boyarsky's account of their experience with the certification](https://www.selikoff.net/ocp11-819/) to be very informative
  * also [Scott's blog article for the 'newly' added topic of Java security](https://www.selikoff.net/2020/11/05/819-security/) was helpful.
* take mock exams online
  * [Oracle's own free practice exam](https://learn.oracle.com/ols/module/practice-exam-java-se-certification/40805/79944)
  * I tried [Whizlab's free mock exam](https://www.whizlabs.com/ocpjd-java-se-11-developer-1z0-819/) before but failed :disappointed: (not entirely my fault though as I caught an error in a question).

I write it matter-of-factly but working with Java every day for so long helped a lot.

### The Exam

In a nutshell: even if I was prepared, a number of *surprises* happened.

I chose to do the exam at **home** but it comes with [a number of constraints](https://home.pearsonvue.com/Test-takers/Resources.aspx?ot=collapse544). The first surprise was the *waiting queue*:

The exam was scheduled at 1pm, the check-in opening at 12:30. After cleaning up my daughter's room for the exam (nothing to write on within hand's reach), I checked in at around 12:40, completed all my check-in steps in about 10min at which point I was prompted with "After clicking next, you are not supposed to leave the camera view". So I went to the bathroom, came back and clicked next only to be shown: "You are at the 97th place in the queue, we expect your exam to start within 15 minutes". Even if I was pretty sure that this time would not count against the exam duration (it was not), the wait raised my stress-level a bit. A couple of minutes after 1pm, I got a direct message in the exam application interface from the online proctor notifying me that they would be talking to me. They let me know that all was in order and checked live that the exam splash screen was showing up (it was). It was time to start ("yup, all of the 90 minutes are in the countdown").

"Watch the clock, *mark* difficult questions to come back to them at the end": I paraphrase but the online resources helped me skim through the questions. Some have multiple answers but those are marked explicitly. I cannot share the content but it was pretty on mark. Then the *final surprise rang:*

*"Ding dong"*... my door bell, then again, then my phone: a delivery person had joined the fun. It would not have been too bad except (i) even if on do-not-disturb, my phone was connected (Pearson VUE wants it to be around but not at arm's reach so that they can contact you), (ii) my MacBook Pro is connected to my phone (because why not?) which of course made it ring as well.
Most likely because of the exam application's mechanisms for locking the system, *the bell kept ringing* for a good three minutes until I was able to reach out to the online proctor, explain the problem and them restart my session (which did resolve the issue).

A couple of minutes before the end, I finally submitted my answers and got my result right away: 70% (passing score: 68%). That was a bit too close! especially since I had only marked around 10 questions for review. The result screen does not show the failed questions but gives a list of *failed topics*: it helps getting a vague idea of what one got wrong without giving the actual questions (and the answers even less).

## Final Thoughts

I am glad that the Java SE 11 Developer certification is just *one* exam. I do not know if I would do the exam at home again given the choice: I dread the idea of doing it with my kid at home.
*If I had to do something differently*, it would be to prepare a bit more by doing more mock exams: a lot of the questions rides on detecting details in a piece of code.

The whole studying and certification was a good experience and I learned a number of things Java-wise. I do not know when I will plan another certification (Java SE 17?) but I hope it goes well again!
title: 'Java: Static Variables are WRONG (Almost Always)'
tags:
  - code
  - collections
  - example
  - final
  - framework
  - j2ee
  - java
  - legacy
  - map
  - mock
  - mutable
  - programming
  - spring
  - static
  - testing
  - variables
id: 296
categories:
  - Tech
date: 2011-06-03 02:25:57
---

This topic came up at work recently, and I thought it might be useful to the wider internet audience...

When doing code reviews, I often come across components which utilize static mutable objects. Typically these are static Maps and other Collections.

If you are using the 'static' keyword without the 'final' keyword, this should be a signal to carefully consider your design. Even the presence of a 'final' is not a free pass, since a mutable static final object can be just as dangerous.

I would estimate somewhere around 85% of the time I see a 'static' without a 'final', it is _WRONG_. Often, I will find strange workarounds to mask or hide these problems.

Please don't create static mutables. _Especially_ Collections. In general, Collections should be initialized when their containing object is initialized and should be designed so that they are reset or forgotten about when their containing object is forgotten.

Using statics can create very subtle bugs which will cause sustaining engineers days of pain. I know, because I've both created and hunted these bugs.

If you would like more details, please read on...

### Why Not Use Statics?

There are many issues with statics:

*   Writing Tests
*   Executing Tests
*   Subtle Bugs

### Writing Tests

Code that relies on static objects can't be easily unit tested, and statics can't be easily mocked.

If you use statics, it is not possible to swap the implementation of the class out in order to test higher level components. For example, imagine a static CustomerDAO that returns Customer objects it loads from the database. Now I have a class CustomerFilter, that needs to access some Customer objects. If CustomerDAO is static, I can't write a test for CustomerFilter without first initializing my database and populating useful information.

And database population and initialization takes a long time. And in my experience, your DB initialization framework will change over time, meaning data will morph, and tests may break. IE, imagine Customer 1 used to be a VIP, but the DB initialization framework changed, and now Customer 1 is no longer VIP, but your test was hard-coded to load Customer 1...

A better approach is to instantiate a CustomerDAO, and pass it into the CustomerFilter when it is constructed. (An even better approach would be to use [Spring](http://www.springsource.org) or another [Inversion of Control](http://en.wikipedia.org/wiki/Inversion_of_control) framework.

Once you do this, you can quickly [mock](http://www.jmock.org/) or stub out an alternate DAO in your CustomerFilterTest, allowing you to have more control over the test,

Without the static DAO, the test will be faster (no db initialization) and more reliable (because it won't fail when the db initialization code changes). For example, in this case ensuring Customer 1 is and always will be a VIP, as far as the test is concerned.

### Executing Tests

Statics cause a real problem when running suites of unit tests together (for example, with your Continuous Integration server). Imagine a static map of network Socket objects that remains open from one test to another. The first test might open a Socket on port 8080, but you forgot to clear out the Map when the test gets torn down. Now when a second test launches, it is likely to crash when it tries to create a new Socket for port 8080, since the port is still occupied.

This is an over-generalized example, but in large systems, this problem happens _ALL THE TIME_. People don't think of unit tests starting and stopping their software repeatedly in the same JVM, but it is a good test of your software design, and if you have aspirations towards high availability, it is something you need to be aware of.

These problems often arise with framework objects, for example, your DB access, caching, messaging, and logging layers. If you are using J2EE or some best of breed frameworks, they probably manage a lot of this for you, but if like me you are dealing with a legacy system, you might have a lot of custom frameworks to access these layers.

If the system configuration that applies to these framework components changes between unit tests, and the unit test framework doesn't tear down and rebuild the components, these changes can't take effect, and when a test relies on those changes, they will fail.

Even non-framework components are subject to this problem. Imagine a static map called OpenOrders. You write one test that creates a few open orders, and checks to make sure they are all in the right state, then the test ends. Another developer writes a second test which puts the orders it needs into the OpenOrders map, then asserts the number of orders is accurate. Run individually, these tests would both pass, but when run together in a suite, they will fail.

Worse, failure might be based on the order in which the tests were run.

In this case, by avoiding statics, you avoid the risk of persisting data across test instances, ensuring better test reliability.

### Subtle Bugs

If you work in high availability environment, or anywhere that threads might be started and stopped, the same concern mentioned above with unit test suites can apply when your code is running on production as well.

When dealing with threads, rather than using a static object to store data, it is better to use an object initialized during the thread's startup phase. This way, each time the thread is started, a new instance of the object (with a potentially new configuration) is created, and you avoid data from one instance of the thread bleeding through to the next instance.

When a thread dies, a static object doesn't get reset or garbage collected. Imagine you have a thread called "EmailCustomers", and when it starts it populates a static String collection with a list of email addresses, then begins emailing each of the addresses. Lets say the thread is interrupted or canceled somehow, so your high availability framework restarts the thread. Then when the thread starts up, it reloads the list of customers. But because the collection is static, it might retain the list of email addresses from the previous collection. Now some customers might get duplicate emails.

### An Aside: Static Final

The use of "static final" is effectively the Java equivalent of a C #define, although there are technical implementation differences. A C/C++ #define is swapped out of the code by the pre-processor, before compilation. A Java "static final" will end up memory resident on the stack. In that way, it is more similar to a "static const" variable in C++ than it is to a #define.

### Summary

I hope this helps explain a few basic reasons why statics are problematic up. If you are using a modern Java framework like J2EE or Spring, etc, you may not encounter many of these situations, but if you are working with a large body of legacy code, they can become much more frequent.

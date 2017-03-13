Working Effectively With Legacy Code: Chapter 3
===============================================

Sensing and Separation
----------------------
In a system that wasn't developed alongside a unit test suite, we frequently will have to break dependencies in order to get classes into test harnesses.  Alternatively, we may need to break dependencies because the class we want to test has side effects that we measure through other classes.  Sometimes we can observe these effects through the interfaces of those other classes, but sometimes we can't, so we must impersonate those classes to observe the effects directly.

These two reasons to break dependencies are described as sensing and separation.

- Sensing: we break dependencies to sense when we can't access values our code computes
- Separation: to separate when we can't get a code into a test harness at all.

This leads to a discussion of one of the most useful ways of breaking dependencies in an object-oriented environment.

- Do you think that you more often have trouble with sensing, or separation?

Fake Objects
------------
The author advocates the use of fake objects in testing.  These are objects that are created specifically for the test, but fulfill some interface that the code under test makes use of.  This allows testing in isolation since the fake object will take the place of some real component of the system that would normally have side effects or be a black box for testing.  The notion of "two faces" is described as meaning that fake objects generally have a side that faces the code under test (i.e., implements the interface the code uses) and another side that faces the tests (that provides some kind of information that we can use to make assertions, like returning the last value that was used as a parameter).

Another, more advanced type of fake object is called a mock object.  Mock objects have internal assertions that can verify that methods were called on the mock.


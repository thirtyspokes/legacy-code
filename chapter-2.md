Working Effectively with Legacy Code: Chapter 2
===============================================
Change Strategies
-----------------
The chapter starts with a description of two possible ways to make software changes:
- Edit and Pray: You think carefully about the change you're going to make, try to understand the code completely, make the change and then poke around in the system to make sure that the change works and that nothing else is broken.
- Cover and Modify:  You use strong test coverage as a safety net to allow you to make changes and receive immediate feedback on any unexpected changes in behavior.

The author describes several testing philosophies, and focuses primarily on regression testing with unit tests.  He describes having a suite of regression-detecting (or, detecting unexpected changes from current behavior) unit tests as a "software vise", that holds the code in place so that you can manipulate or refactor it more easily.  He describes how many companies use large suites of "application interface" (i.e., 'functional tests') tests that are slow and must be run overnight, and how this creates a very long feedback cycle that is inefficient compared to tests that you can run on your machine quickly.

- Which of the two change styles do you think best describes how we work with Luceo?
- What kind of regression tests do we have in the system now?
- Are they helpful?  Do you feel like they provide a safety net?

Unit Testing
------------
Some characteristics of unit testing listed by the author are that they are fast, and they help localize errors.  This means that the tests are smaller, test code in isolation (i.e., without 'real' dependencies) and can be run quickly and easily.  Being able to localize errors means that the tests should make it very easy to determine what is broken when they fail.  Very large tests (like regression tests, or end to end tests) cover so much code that when those tests fail it is extremely difficult to determine where the actual defect is.

He lists four characteristics that make a test NOT a unit test:
- Talking to databases
- Communicating across networks
- Touching file systems
- Requiring special setup like editing config files

The reason such an emphasis is placed on speed is the shortened feedback cycle that it provides.

- Do you agree with this definition of unit tests?
- Do you agree with the difficulties in larger tests that the author describes?

The Legacy Code Change Algorithm
--------------------------------
The overall goal of the book is presented here:  by following this algorithm when we make changes in the legacy code, we can bring the small area we are working on under test.  As we continue to apply this process, more of the code will have tests (a software vise) and our ability to safely make changes will grow.

1.  Identify Change Points
2.  Find Test Points
3.  Break Depdencies
4.  Write Tests
5.  Make Changes and Refactor


Working Effectively with Legacy Code: Chapter 4
===============================================
The author describes a model called the 'seam model' for identifying change points in legacy code.  Broadly, a seam is a place in the code that you can change the behavior when run without editing the code in place.  In the example given, there is a single side-effecting method called that we would like to eliminate from running for the sake of our tests.

In order to do this, we create a subclass of the class containing the code we want to eliminate and then override the target method with an empty body.  Then, in the location where we create the containing class, we substitute our subclass.  The effect is that the body of the method we wanted to test is completely unchanged, but now we have replaced the side-effecting method with an empty one, and can now test in isolation.  Another important concept with seams is the enabling point, the place where we can make a decision to use one behavior or another.  In our example above, the spot where we can choose to use the original class or the subclass we created is the enabling point.

Types of Seams
--------------
The author describes various types of seams that can be utilized, based on the processes used to turn code into machine instructions.

- Preprocessing seams: using preprocessor directives to change behavior
- Link seams: altering the location of imports

The most important one is the object seam, wherein we can change behavior of a called method by changing the type of object that is being used.  In the example given, we have a `cell` object with a `Recalculate()` method.  We can adjust behavior by providing different types of classes that have the recalculate method.  However, the author also shows how not all method calls are seams - in the example, a cell is being created and called within another method, so there is no enabling point where we can substitute a new cell object, until the appropriate refactoring is made to inject the cell object as a parameter instead of creating it inline.

- Have you ever used any of the techniques in the examples to get some code under test?
- Are there other seams you know of that aren't described in this chapter?
- What's the reason that the author gives for the importance of finding seams? Do you agree?
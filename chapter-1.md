Working Effectively with Legacy Code: Chapter 1
==============================================
The four reasons we change code:
- To fix a bug.
- To add a new feature.
- To improve the design.
- To improve performance/optimize resource usage.

Adding and changing behavior
----------------------------
We usually define what's a bug fix versus a new feature in terms of changing existing code versus adding new code.  However, very rarely do we add new code without also having to change the existing code (new UI element, calling a new method that was written), so the distinction is fuzzier than we think.  What we should keep in mind is that the behavior of the software is the whole reason users pay for it, so we should always be thoughtful with how we change it.

In many cases, fixing a bug (modifying or maintaining existing code) is treated differently from an accounting perspective than writing new code.  This is true at CB (tax law as it relates to capital expediture incentivizes creating new products/features over maintaining or improving existing ones).
- How often do you feel like you modify existing code versus writing entirely new code?
- What does this imply?

Refactoring
-----------
In general we refer to the process of somehow improving the design of existing code without changing its behavior "refactoring."  One primary reason we write tests is so that we can verify that we have not in fact changed behavior during the process of modifying existing code.  Thus, our ability to refactor our codebase to improve the design depends heavily on our confidence in our test suite.
- Do we have that confidence today?
- Can you think of a refactoring that you or someone else did recently?
- What did you do to make sure you didn't change the behavior?

Putting it all together
-----------------------
The primary problem we face is this: our job involves modifying existing code without changing existing behavior, but we frequently cannot determine which existing behaviors are at risk of being accidentally changed when we modify the code.  This leads to conservatism (if it's not broken, don't bother trying to improve it because it's too risky) and fear (we are afraid to make important changes and work takes longer because of our fears of breaking existing features).  As a result, we take longer to deliver features because of the groundwork we must do to determine what features are at risk of changing, and technical debt in the product is never addressed because we can never be sure whether a refactoring might be safe or not.  Our goal, therefore, is to minimize the risk of change above all else.
- If making changes is risky because we don't know what we might break, what does that imply for bug fixes?
- Can you think of examples recently where a seemingly innocent change broke something in a big way?
- Do you agree that mangaging the risk of change is as important as the author says it is?
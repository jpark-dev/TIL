# *Clean Code* by *Robert Cecil Martin*

## DAY 18 - 07/Feb/2022
## Ch.9 Unit Tests

### Takeaways
- ***READABILITY***
- CLEAN CODE matters more in testing.
- There are things that you might never do in a production environment that are perfectly fine in a test environment. Usually they involve issues of memory or CPU efficiency. But they never involve issues of cleanliness.
- Minimize the number of asserts per concept and test just one concept per test function.
- FIRST
  - Fast: should run quickly.
  - Independent: tests should not be dependent on others.
  - Repeatable: should be repeatalbe in any enviornment (even without network).
  - Self-validating: should have a boolean output.
  - Timely: tests need to be written in a timely fashion.
  - If you let the tests rot, then your code will rot too. Keep your tests clean.

### Thoughts
- I really should work on writing better/clean tests. From the FIRST, I still need to work on S and T.
- I really like how the author emphasizes on how writing test code after writing the production code makes the production code hard to be tested. This is actually happening in many of my projects, but I'm still reluctant in writing tests before writing production code - even though I totally agree on the concept of TDD. Maybe I should take a detailed class in writing a good test codes.
- Even though I love refacotring my code for readability and reusability, I never thought of making the testing code `CLEAN`. As long as tests are done, I moved on with a sense of accomplishment that I've written tests for this module. Again, it's time to get serious about writing a better test - thank you CLEAN CODE!

### Extra

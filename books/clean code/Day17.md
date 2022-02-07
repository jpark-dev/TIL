# *Clean Code* by *Robert Cecil Martin*

## DAY 17 - 06/Feb/2022
## Ch.9 Unit Tests

### Takeaways
- Three Laws of TDD
  1. You may not write production code until you have written a failing unit test.
  2. You may not write more of a unit test than is sufficient to fail, and not compiling is failing.
  3. You may not write more production code than is sufficient to pass the currently failing test.
- Having dirty tests is equivalent to, if not worse than, having no tests.
- Tests enable all the -ilities, because tests enable change.
> Test code is just as important as production code.

### Thoughts
- Oh no, here we go. Something that many devs wanted to know, seem to be doing, but not in the most efficient way. For myself, I love writing unit tests and e2e/integeration tests using cypress - beause it gives me a good visual. However, it's also sometimes really hard to set the `golden standard` for writing a clean test code. I'm still struggling in writing tests, fighting the temptation that 'Maybe I don't need to write one for this small repo - since the test coverage is less than 60% anyway, what good does it do to the team? Maybe I can move on and take another ticket instead of writing more tests'.
- This is a big one, Jason, let's fix this now - it's always better late than never. 
- Simple rules - let's write unit tests, integration tests, that covers pretty much everything. I really need to get the codebase ALIVE. Remember the boy scout rule Jason, the `BOY SCOUT RULE`.
- Big OUCH moment...

### Extra

# *Clean Code* by *Robert Cecil Martin*

## DAY 07 - 27/Jan/2022
## Ch.3 Functions

### Takeaways
- Avoid side effects: a function should do just one thing.
- Avoid output arguments.
- Separate command from query in a function: ie) `setAndCheckIfExists` --> `exists() + set()`
- Prefer exceptions to returning error codes.
- Just like if/else statment block should have one function, do the same for `try/catch` statement.
- Keep the code DRY
- Your initial code is just a draft - revise and review to perfect it.
- The real goal is to tell the story of the system, and that the functions you write need to fit cleanly together into a clear and precise language to help you with that telling.

### Thoughts
- I like how the author mentions that each statement block should contain a function. Often I have to fight against myself in making a decision - shorter code vs. descriptive code. From now on, there will be a beautifully named function, and only one of them in each statement scope!
- Having a side effect is another thing. It's still not so clear on how to define *which level should a function handle a single task?* In other words, `closeModal()` can also be further refactored into `resetStoreValue() + setModalStateToFalse()`. I usually only refactor at this level when these are used more than once; but again, it's really nice to take some time to think about this.
- Revision after writing a working code is a MUST! Seriously, I can't stand what I wrote a year ago, all those lines can be beautifully tidied up..

### Extra

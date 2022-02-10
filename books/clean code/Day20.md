# *Clean Code* by *Robert Cecil Martin*

## DAY 20 - 09/Feb/2022
## Ch.10 Classes

### Takeaways
- A class should begin with a list of variables.
  - 1. Variables: Public --> Private --> Private instance
  - 2. Functions: Public --> Private utilities (Callee)
  - Remember the stepdown rule (JAVA)
  - Encapsulation
- Classes should be small and smaller than that.
  - A class should have one responsibility - with naming itself.
  > SRP (Single Responsibility Principle)

> Every sizable system will contain a large amount of logic and complexity. The primary goal in managing such complexity is to organize it so that a developer knows where to look to find things and need only understand the directly affected complexity at any given time.

- Increase cohesion with more variables
  - Methods and varialbes of the class become co-dependent and hang together as a logical whole.
  - If more variables/functions seem to make them loosely dependent: that's great - split them!

### Thoughts
- Another great chapter visiting classes for OOP languages. However, this is practically useful for those who want to create and publish npm packages - I have seen many devs mimick OOP structure by using `~` or `_` before private methods or variables. Maybe JS will one day have better structure with making elements private - look what TypeScript has done to JavaScript.
- Nice and clear explanation on the vertical scope of code does not matter if the code becomes clean and gets improved in readability/maintainability.
- I think I'm really into JS now - JAVA code looks so bulky and redundant all of sudden. Haha.

### Extra

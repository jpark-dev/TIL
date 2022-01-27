# *Clean Code* by *Robert Cecil Martin*

## DAY 06 - 26/Jan/2022
## Ch.3 Functions

### Takeaways
- Write small functions, and they make them *smaller*.
- The blocks within if statements, else statements, while statements, and so on should be one line long. The indent level of a function should not be greater than one or two.
dition. 
- **FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL. THEY SHOULD DO IT ONLY.**
- Extract to a level where it's not merely a restatement of its implementation.
- Use descriptive names and stay consistent.
- Minimize no. arguments in functions if possible; Using objects and arrays is not cheating!!

### Thoughts
- I'm already started to see the Java-dependent coding examples in this book. For the sub-chapter discussing about the `Switch Statements`, those who are not introduced with OOP + factory patterns will not even understand what the author is talking about. How can this be applied to the `JavaScript` world? The author answers this at the end of the very first paragraph:
> ...make sure that each switch statement is buried in a low-level class and is never repeated.
- Minimizing the number of function arguments is very interesting. I totally agree that the readability improves as there are less arguments. However, I have a different stance on the flag arguments. Of course, `render(true)` is a poorly written function but having to write two functions to seperate seems to defeat the purpose of the function if the function deals with one purpose - to distinguish a boolean condition and carries out a low level abstraction work.
```
const calculateTime(isUTC: Boolean) {
  if (isUTC) {
    return transformTime();
  }
  if (!isUTC {
    const timeInUTC = calculateToUTC();
    return transformTime(timeInUTC);
  }
}
```
- I usually like to refactor repeated functions into one, that takes a flag argment. In this way, whenever there is a change in a section(or more) that executes the function `calculateTime`, I don't have to search for the appropriate function to match the specific purpose - it's already encapsulated and `calculateTime()` will handle it accordingly depending on the argument.


### Extra

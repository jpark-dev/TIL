# *Clean Code* by *Robert Cecil Martin*

## DAY 10 - 30/Jan/2022
## Ch.5 Formatting

### Takeaways
- The team should agree to a single set of formatting rules and all members should comply.
- Code formatting is important and is about communication of professionals.
- The code doesn't have to be long in order to make a great application.
- Write your code like writing a newspaper article.
- **FLOW**
- Leave a vertical space between different concepts.
- Only the related lines of the code should appear vertically dense --> remove unncessary comments that adds up and sepparate different concepts.
- This also applies to the order and the location of these related lines of code.
- Local variables should appear at the topo of each function.
- Instance (global) variabales should appear at the top of the class (for js, the top of the js file, preferrably after the imports?)
- Dependent functions --> Caller should be above the callee (which I personally appose due to js hoisting).
- Similar named items together
- Use horizonal whitespace to accentuate strongly related concepts --> assignment statements for emphasis. Applies to the precedence of operators. 
- No more horizontal alignment - the problem is the length of the lists, not the lack of alignment.
- Indentation, indentation, indentation!~

### Thoughts
- Another interesting chapter followed. There have been many projects and teams I've come across in the past and no more than 50% had the formatting rules set up (either in formatting configuration or in a document). This should really be the golden rule, particularly for big teams as well as startups - maybe just simply sticking to AirBnB style might not be a bad idea.
- For how the author suggests the caller should be above the callee with dependent functions, I have a conflicting view. Let's take a look -
```
  const doubleTheNumber = input => {
    checkIfNumberType(input);
    ...
  }
  
  const checkIfNum = value => {
    if (typeof value === 'number') {
      return true;
    }
    return false;
  }
```

vs.

```
  const checkIfNum = value => {
    if (typeof value === 'number') {
      return true;
    }
    return false;
  }
  const doubleTheNumber = input => {
    checkIfNumberType(input);
    ...
  }
```
- I agree with how the author mentions the code should read downward, but imagine a `js` file with 10 functions where 5 of them are depdent functions.
Should all dependent functions be located below the callee?
For myself, I prefer having functions constructed above the callee - that gives me a good understanding of how functions are declared before it gets used.
Think about this - the callee function goes 'Hey, let me call this function called `checkIfNum()`. By the way, let's create it after creating this caller function`.
It may have better readability if you are reading it top-down, but just like how the author emphasized the target audience who gets to read the code is mostly the developers - I believe this way of create a function that is going to be called after before creating the caller function has a better flow.
It just feels like the function is not declared (of course, js hoisting can be quite different from other languages).

Again, there is no right/wrong answer, and as a member of a team, one should follow the team's formatting rules.

- I really never thought of horizontal/vertical spacing and openness - as I learned almost exactly how the author suggests. However, it was nice to find many things I can improve the readability of my code.

### Extra


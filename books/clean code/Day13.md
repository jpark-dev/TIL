# *Clean Code* by *Robert Cecil Martin*

## DAY 13 - 02/Feb/2022
## Ch.7 Error Handling

### Takeaways
- Error handling is important, but if it obscures logic, it’s wrong.
- Use exceptions rather than return codes - so much cleaner.
- Write try/catch/finally first.
- Provide context with exceptions with informative error messages.
- Define exception class.
- Do not return/pass null.
- Good error handling directly improves the readability and maintainability of the code.

### Thoughts
- I'm glad that I actually follow most of the rules written in this chapter. Victory!
- Defining exception class is something I knew that I should do it but I was afraid of creating one as all my seniors seemed to be just okay with the default `throw new Exception()` with an empty string, as JAVA log4J would be logging it out anyway. It'd be great practice to do so as the typescript + react also involved creating a custom error type. Will work into this in the next project :).
- It would've been awesome if the author added something about not adding `console.log`s in the error handling (I've seen one too many applications where console.log is just left there as an error handling message - which may not be the best practice. Maybe creating an error class or error message object could've been a nice addition to this chapter.

### Extra

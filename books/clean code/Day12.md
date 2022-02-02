# *Clean Code* by *Robert Cecil Martin*

## DAY 12 - 01/Feb/2022
## Ch.6 Objects and Data Structures

### Takeaways
- Objects hide their data behind abstractions and expose functions that operate on that data.
- Data structure expose their data and have no meaningful functions.
- Procedural code makes it hard to add new data structures because all the functions must change. OO code makes it hard to add new functions because all the classes must change.
- The Law of Demeter - talk to friends, not to strangers.
- Avoid hybrid structure that are half-object adn half-data structure.
- Choose the right approach depending on the situation.

### Thoughts
- This chapter is heaviliy dependent on the OOP concept of JAVA. I'm glad that I was a java developer when I entered the industry. Nothing written here is magical, but the takeaway is to choose when to use data structure vs. objects with functions. However, it's not very applicable to the world ot JavaScript: as JS does haves the pseudo-class system that can be implemented but not an OOP language.
- Then how do we implement this `private` and `public` keywords in js? If you console log pretty much any popular library/classes, then you can see the `_` underscore before the functions - which is the conventional way to make function/kv pair a private one.
- Another thing to note is that the `Law of Demeter` is useful to OOP languages, but not necessarily to JavaScript. Of course, code golfing should be avoided as it can reduce readability but will not be a bad practice unless there is too much code golfing. Again, this chapter applies to OOP languages, too bad it does not cover non-OOP languages.

### Extra

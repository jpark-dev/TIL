# *Clean Code* by *Robert Cecil Martin*

## DAY 05 - 25/Jan/2022
## Ch.2 Meaningful Names

### Takeaways
- Say what you mean. Mean what you say. Be Clear. Stay Clear.
- Pick one word per concept - and stay consistent.
- Be clear and specific - don't use `add` for both adding a kv pair to an object and adding to merge arrays into one. Find a better word for a better understanding.
- Use technical terms if required - people who will look into your code (possibly maintain and add on) will also be developers.
- Add meaningful context - don't be afraid to break things into smaller pieces that actually mean something.
- Shorter names are generally better than longer ones, so long as they are clear. Add no more context to a name than is necessary.
  - The names `accountAddress` and `customerAddress` are fine names for instances of the class `Address` but could be poor names for classes. `Address` is a fine name for a class. If I need to differentiate between MAC addresses, port addresses, and Web addresses, I might consider `PostalAddress`, `MAC`, and `URI`.
- *Don't hesitate renaming things!!!*


### Thoughts
- It's nice to see how this chapter clarifies some of the concepts which are often confusing.
- I don't think I've ever renamed someone else's work unless they were atrocious. I will try to rename things for readability - boy scout rule!!
- Language specific naming + project based rules can often be confusing and can be mixed up - but as long as I stay consistent, it'll add up in the end.

### Extra

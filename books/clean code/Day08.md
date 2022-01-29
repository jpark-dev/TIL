# *Clean Code* by *Robert Cecil Martin*

## DAY 08 - 28/Jan/2022
## Ch.4 Comments

### Takeaways
- Comments are, at best, a necessary evil. If our programming languages were expressive enough, or if we had the talent to subtly wield those languages to express our intent, we would not need comments very much—perhaps not at all.
- The proper use of comments is to compensate for our failure to express ourself in code.
> “Don’t comment bad code—rewrite it.”
- Good code should speak for itself.

#### Good comments examples:
  - Legal comments
```
// Copyright (C) 2003,2004 by Jason, Inc. All rights reserved.
// Released under the terms of the GNU General Public License version 2 or later.
```
  - Explanation of Intent
```
// This is our best attempt to get a race condition by creating large number of threads.
```
  - Clarification
```
assertTrue(a.compareTo(a) == 0);    // a == a
assertTrue(a.compareTo(b) != 0);    // a != b
assertTrue(ab.compareTo(ab) == 0);  // ab == ab
assertTrue(a.compareTo(b) == -1);   // a < b
assertTrue(aa.compareTo(ab) == -1); // aa < ab
assertTrue(ba.compareTo(bb) == -1); // ba < bb
assertTrue(b.compareTo(a) == 1);    // b > a
assertTrue(ab.compareTo(aa) == 1);  // ab > aa
assertTrue(bb.compareTo(ba) == 1);  // bb > ba
```
  - Warning of consequences
```
// SimpleDateFormat is not thread safe,
// so we need to create each instance independently.
```
  - TODOs
```
// TODO(jason@jason.com): MdM these are not needed
// We expect this to go away when we do the checkout model.
```
  - Amplification - emphasis on something that may otherwise seem inconsequential
```
String listItemContent = match.group(3).trim();
// the trim is real important.  It removes the starting
// spaces that could cause the item to be recognized
// as another list.
```
  - Docs for Public APIs

### Thoughts
- Try your best (and be honest) to re-write the code before leaving a comment.
- I like this chapter as I was on a pendulum between writing more specific comments vs. no comment at all. Unless there is a real good reason, comments should be avoided - but write one if necessary.
- It will take years of practice and experience until one can write a clean code. Again, the code tells a story, and if you think you are not the master-writer of your own story, use comments. Don't be discouraged, come back to that code with comments in a day or two, and I believe you will be able to rewrite it into a better code with less comment.
e
### Extra

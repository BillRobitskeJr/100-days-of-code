# 100 Days Of Code - Log

### Day 1: December 29, Thursday

**Today's Progress**: Completed the Basic Algorithm Scripting challenges on
freeCodeCamp.

**Thoughts**: I struggle to come up with small code projects.  I have a few that I want to work on, but in my interest to practice Agile -- defining user stories and all that -- they seem to have grown to the point where I feel I'm not ready to start working on them.  I kind of feel like I need to stop planning and just start working on them.  Start with something small - just a basic interface for the core functionality - build from there.  Then I'll at least have something to show, and that's the whole point of this exercise, right?

**Link(s) to work**

1. [freeCodeCamp Profile](https://www.freecodecamp.com/billrobitskejr) -- Shows completion of challenges, although they show up as 12/30 due to time zones.

### Day 2: December 30, Friday

**Today's Progress**: Started working on a task planning/logging app.  Have a very rough layout put together, but no behavior yet.

**Thoughts**: I decided to use Firebase for network storage and static hosting.  For now, it just means hosting.  I want to implement authentication, so it'll help with that.  I also decided to pull in Polymer for custom elements, but I'm limiting how much I go crazy with it here.  Instead, I'm going to rely on Bootstrap and save Polymer for when I want to reuse an element.

**Link(s) to work**

1. [Lasagna](https://lasagna-d5007.firebaseapp.com/)
2. [Lasagna GitHub](https://github.com/DigitalMugen/lasagna)

### Day 3: December 31, Saturday

**Today's Progress**: Continued work on task planning/logging app.  The Add Activity button now actually does something, and the "selected date" is automatically set to the current day when loaded.  Also added table column spacing.

**Thoughts**: I think I'm done with Bootstrap on this project -- I'm just not getting the look I'm picturing for the app.  I have in mind a digital replacement for a paper planner, but this just looks like I mess of Bootstrap text boxes...

**Link(s) to work**

1. [Lasagna](https://lasagna-d5007.firebaseapp.com/)
2. [Lasagna GitHub](https://github.com/DigitalMugen/lasagna)

### Day 4: January 1, Sunday

**Today's Progress**: Began implementing the interface using CSS flex box for the columns; removed Bootstrap.  Using Unicode character entities for the task progress fill-in circles.  The daily activity log needs some work - tried mocking it up with a table, but it's a bit of a mess.

**Thoughts**: Columns look good on desktop and my iPad in landscape orientation, but they're too narrow on my iPhone.  The text is also unreadable, since it scales with the viewport width.

**Link(s) to work**

1. [Lasagna](https://lasagna-d5007.firebaseapp.com/)
2. [Lasagna GitHub](https://github.com/DigitalMugen/lasagna)

### Day 5: January 2, Monday

**Today's Progress**: Created a `<circle-tally>` element for the tally control in the Daily Tasks column.  It shows filled circles for the first five tallies, and then increments an additional tally count after that point.  Circles are displayed via Unicode characters in the `::before` pseudo-class's content -- switched with the addition or removal of the `is-filled` class on `<span>` elements.

**Thoughts**: Went back to using Atom as my editor; it's easier to access from the Window's GitHub client.  Also, collected the default browser window dimensions in Safari on my iPhone 7 and Chrome on my iPad Pro.  Both always have a width of 980, but varying heights.  Hopefully, I'll be able to use that to control whether or not to display the app with columns.  I only want columns to appear on landscape tablets and on desktop.

**Link(s) to work**

1. [Lasagna](https://lasagna-d5007.firebaseapp.com/)
2. [Lasagna GitHub](https://github.com/DigitalMugen/lasagna)

### Day 6: January 3, Tuesday

**Today's Progress**: Created `<rating-scale>`, `<app-daily-tasks>`, and `<daily-task>` elements to build out the Daily Tasks view.

**Thoughts**: Bring on the Polymer!  I did think I was going crazy for a bit due to a bug in `<circle-tally>`.  In `<daily-task>`, I have the same tally count bound to both the progress `<circle-tally>` element and the actual length `<input>`.  Since input only gives back a string value (even when it's bound to a Number property), `<circle-tally>` was adding 1 to the current value as a string rather than a number.  For example, if you set the value via the actual length to 1 and then click on `<circle-tally>`, the value became 11 instead of 2.  Oops!  It was a simple fix, but Chrome decided to continue using the previously loaded, cached copy and wasn't reflecting the change.  LOL

**Link(s) to work**

1. [Lasagna](https://lasagna-d5007.firebaseapp.com/)
2. [Lasagna GitHub](https://github.com/DigitalMugen/lasagna)

### Day 7: January 4, Wednesday

**Today's Progress**: Created a simple Pomodoro timer on codepen.io using `transform: scaleX()` and `transform-origin` to handle the animation of the timer bar.  Unfortunately, I coded it badly, so it pauses when it doesn't have focus.  Oops.

**Thoughts**: Be careful when using Javascript `alert`s for testing feedback.  When you forget to stop the timer when it reaches 0 and have it display an alert each cycle that when it reaches 0... well, you're gonna have a bad time.

**Link(s) to work**

1. [Pomodoro Timer](http://codepen.io/billrobitskejr/pen/xgbRxa)
2. [Pomodoro Timer](http://s.codepen.io/billrobitskejr/debug/xgbRxa) - "Debug Mode" without the codepen.io interface

### Day 8: January 5, Thursday

**Today's Progress**: Worked on converting yesterday's Pomodoro timer over to functional programming.  It doesn't yet work (I deleted the variables, which broken yesterday's version), but it was interesting viewing the problem from a different angle.

**Thoughts**: Enough goofing around, Bill!  Get back to work on Lasagna tomorrow!  Also, codepen.io is kind of a pain to use if you have any real amount of code.  The windows are just too narrow.

**Link(s) to work**

1. [Pomodoro Timer](http://codepen.io/billrobitskejr/pen/xgbRxa)

### Day 9: January 6, Friday

**Today's Progress**: Started rebuilding (again) the past two days' Pomodoro timer in on GitHub in ES6 and functional programming.  The functional programming - or at least the arrow functions - are not going the way I hoped.  I was able to get an ES6 build stack set up and have the project self-hosting on GitHub.

**Thoughts**: I thought that arrow functions would directly translate to lambda functions, but Javascript is still Javascript.  I at least learned how to use GitHub pages and gulp/babel/ESLint/Webpack.

**Link(s) to work**

1. [Pomodoro Timer](https://billrobitskejr.github.io/pomodoro-timer/) GitHub Pages hosted version
2. [Pomodoro Timer](https://github.com/BillRobitskeJr/pomodoro-timer) GitHub repository

### Day 10: January 7, Saturday

**Today's Progress**: Returned to the planner app - began work on `<app-daily-log>` in layout out the hour/quarter-hour lined layout.

**Thoughts**: I have the layout, and it's using `rem` sizing.  May vision is to have the activities overlayed on this with some transparency, with their positions calculated against the size of today's layout work.

**Link(s) to work**

1. [Lasagna](https://lasagna-d5007.firebaseapp.com/)
2. [Lasagna GitHub](https://github.com/DigitalMugen/lasagna)

### Day 11: January 9, Monday

**Today's Progress**: Completed the first eight of the Intermediate Algorithm Scripting challenges on freeCodeCamp using functional programming.

**Thoughts**: Kind of a slow start back up after missing yesterday.  The Roman Numeral conversion algorithm felt like it took much longer than it should.

**Link(s) to work**

1. [freeCodeCamp Profile](https://www.freecodecamp.com/billrobitskejr) -- Shows completion of challenges, although they show up as 1/10 due to time zones.

### Day 12: January 10, Tuesday

**Today's Progress**: Completed the next seven of the Intermediate Algorithm Scripting challenges on freeCodeCamp using functional programming.

**Thoughts**: I think I may be abusing arrays...

**Link(s) to work**

1. [freeCodeCamp Profile](https://www.freecodecamp.com/billrobitskejr) -- Shows completion of challenges, although they show up as 1/11 due to time zones.

### Day 13: January 11, Wednesday

**Today's Progress**: Completed the next three of the Intermediate Algorithm Scripting challenges on freeCodeCamp using functional programming.

**Thoughts**: The Least Common Multiple challenge took over an hour on its own due to me effectively trying to brute force it.  After writing various means of determining the multiple, only to find they required to many recursion iterations, I discovered that it can be determined via the Greatest Common Denominator -- which can be calculated via the [Euclidean algorithm](https://en.wikipedia.org/wiki/Euclidean_algorithm).  Read-search--what comes after search?  ;)

**Link(s) to work**

1. [freeCodeCamp Profile](https://www.freecodecamp.com/billrobitskejr) -- Shows completion of challenges, although they show up as 1/12 due to time zones.

### Day 14: January 12, Thursday

**Today's Progress**: Finished up the Intermediate Algorithm Scripting challenges on freeCodeCamp - all with functional programming!

**Thoughts**: Especially after last night's work, I'm finding functional programming forces me to be a more efficient with my code.  The Least Common Multiple problem would have been easily solvable with my brute force methods if I were using for loops, but having to be mindful of my recursion depth means I had to limit how many cycles the solution took.  End result, a far faster solution than I could have left with otherwise.

**Link(s) to work**

1. [freeCodeCamp Profile](https://www.freecodecamp.com/billrobitskejr) -- Shows completion of challenges, although they show up as 1/13 due to time zones.

### Day 15: January 13, Friday

**Today's Progress**: Completed a few of the freeCodeCamp Advanced Algorithm Scripting challenges.  Starting a GitHub project for the "Build a JavaScript Calculator" project--even though it will need to move to codepen.io for submission.

**Thoughts**: Setting up an ES6 environment such as that for the Pomodoro timer app.  I'll have to wait and see how well it works when copied to codepen.io.

**Link(s) to work**

1. [freeCodeCamp Profile](https://www.freecodecamp.com/billrobitskejr) -- Shows completion of challenges, although they show up as 1/13 due to time zones.
2. [Calculator](https://github.com/BillRobitskeJr/fcc-calculator) on GitHub

### Day 16: January 14, Saturday

**Today's Progress**: Finished build stack and constructed basic layout for the Calculator project.  Got it serving from GitHub.

**Thoughts**: #FlexboxIsAwesome

**Link(s) to work**

1. [Calculator](https://billrobitskejr.github.io/fcc-calculator/)
2. [Calculator Repository](https://github.com/BillRobitskeJr/fcc-calculator)

### Day 17: January 15, Sunday

**Today's Progress**: Implemented digit buttons on the calculator project app.

**Thoughts**: Caching is really annoying sometimes - I find that something isn't working, and then spend the next 5 minutes figuring out that its not pulling the new copy of the code that's clearly there.

**Link(s) to work**

1. [Calculator](https://billrobitskejr.github.io/fcc-calculator/)
2. [Calculator Repository](https://github.com/BillRobitskeJr/fcc-calculator)

### Day 18: January 16, Monday

**Today's Progress**: Began working on calculator operations, implementing them as pure static functions.  Created a separate Calculator class to house the calculator's mutable state -- its current number buffer value and the last operations applied.

**Thoughts**: Calculator is not pure functional programming, but I suppose neither was the `textContent` implementation from yesterday.  Hopefully, with some practice on this project (or a future one), I can rectify that.  In the mean time, "a working solution is a valid solution."

**Link(s) to work**

1. [Calculator Repository](https://github.com/BillRobitskeJr/fcc-calculator)
2. [Calculator Repository - 'basic-operations' Branch](https://github.com/BillRobitskeJr/fcc-calculator/tree/basic-operations)

### Day 19: January 17, Tuesday

**Today's Progress**: Completed the Calculator app, at least with basic operations.  There's no additive inverse operation, but your typical add, subtract, multiply, and divide.  It works well enough for simple arithmetic.

**Thoughts**: Like a basic calculator, order of operations is not considered/respected.  That burden is placed on the user; you need to enter operations in the order you want them calculated.  To do more, I'll have to implement some form of operation tree that is built out, and then fully computed when equals is pressed (rather than resolving each operation when the next operation is pressed).

**Link(s) to work**

1. [Calculator](https://billrobitskejr.github.io/fcc-calculator/)
2. [Calculator Repository](https://github.com/BillRobitskeJr/fcc-calculator)

### Day 20: January 19, Thursday

**Today's Progress**: Started a little side project to implement various mechanics of the Pathfinder Roleplaying Game system via ES6 modules.  For tonight, it was the "Armor as Damage Reduction" rules from Ultimate Combat.

**Thoughts**: No more slack days, Bill!  (at least until after Day 28)

**Link(s) to work**

1. [Trail Spotter repository](https://github.com/DigitalMugen/trail-spotter)
2. [Trail Spotter repository - 'armor-as-damage-reduction' Branch](https://github.com/DigitalMugen/trail-spotter/tree/armor-as-damage-reduction)

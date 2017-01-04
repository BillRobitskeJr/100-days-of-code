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

# 100 Days Of Code - Log

### Day 1: January 1, Tuesday

**Starting Thoughts**

I want to explore machine learning, trying to combine NeuroEvolution of Augmenting Topologies (NEAT) with backpropagation training.  The idea is to imitate human learning through alternating periods of "active training" and "experimentation".  During the "active training" periods, normal backpropagation training would be used to simulate the entity attempting the action, assessing the result, refining their approach, and then moving onto the next attempt.  During "experimentation" periods, NEAT would be used to simulate "dreaming up" new ways of approaching the action, imagining their outcomes, and adopting the way(s) that work best.  The hopeful end result would be an entity that mirrors how one can hone a skill by perform the action repeatedly and then "sleeping on it" to have it "finally click".

First, however, I will need an environment to provide such an entity context and objectives to work on.  A "problem" that can be solved by deriving action upon current input, and for which one can assess both the "accuracy" of each given action and the "fitness" of the combined actions.  "Am I doing it right?" vs. "Am I getting anywhere?"

...but how does one decide if they are performing the right actions?  Imitate a teacher?  So, the environment needs to allow for an "instructor" to demonstrate what to do for the "student" to attempt to copy.

How about some form of Asteroids?  Fitness can be defined by how long the "student" survives.  A human player can serve as the "instructor" - which means that the human player interface needs to mirror that of the "student".

We'll make a game of Asteroids in which the player has a limited view of the environment - only fair that a person not have an unfair advantage over the AI.

**Today's Progress**

A bit of progress on the human player-facing game, the ship is drawn in the center of the canvas, with eight view sectors arrayed around it.

**Thoughts**

- I'm terribly rusty with the Canvas API.  It took me far to long to get this set up.  Then again, a large part of that was getting my math worked out (and it's not even complex math yet...)
- I took too much time playing around with the page title.  I was able to mimic the old Asteroids arcade logo.
- I may want to change the sectors around some.  I'd love to have twelve sectors to reflect clock positioning.  At the same time, I'm tempted to make the sectors more dense in front of the ship and less dense behind.  I think I'll leave it as is for now (at least until the obstacles are implemented).
- The idea of the game will be to keep the ship and sectors fixed on the screen and instead rotate and translate the obstacles around the ship.

**Link(s) to Work**

1. [ai-asteroids](https://github.com/BillRobitskeJr/ai-asteroids)

### Day 2: January 2, Wednesday

**Starting Thoughts**

So, I'm realizing an initial flaw with my design.  While I still want to go this route - with the player in the center and seeing only limited information of the sectors around you - it's not going to be helpful to tell "is this working".  Creating the AI to play this game isn't going to be worth anything if a player can't tell what they're doing anyway.  If a player'd just be winging it, then how can you tell if the AI is learning?

So, I need to make a second view - one more like the traditional Asteroids game.  Then I can mirror both views based on the player (or AI actor) input.  Ultimately, my next most immeidate goals are:
- Create a "bird's eye" view
- Factor "player's eye" view into a module
- Add a player input module
- Add a game state module (to keep track of the player ship and any other entities I add later)
- Connect all this stuff together!

**Today's Progress**

It does something now!  There's now a game and ship state model: GameState holds the size of the game environment (in pixels, x & y) and the refresh rate (updates per second), and ShipState holds each ship's position (relative to the game environment, x & y from 0 to 1), velocity (heading & speed), and heading.  An ObserverView has been added to show the game more like the traditional Asteroids game, while PlayerView shows the game from the perspective of a particular ship.

With these additions, index.js now just creates the game and player ship state, creates the player and observer views, and starts a loop to update the player ship's position and update the views.  Now you can see how the ship is moving around the game field, even though the player's view appears unchanged.  There's only the player ship, so there are no points of reference to tell that there's anything going on.

**Thoughts**

Asteroids is fun, but it always seemed strange that the ship would slow down on its own.  It's like moving in a fluid, not a vacuum.  For my game, the ship is completely inertial.  I want their to be a max speed (i.e. velocity.speed = 1), but it should be relativistic.  The rate of acceleration should suffer from diminishing returns as the ship approaches max speed as if it were light speed.  As speed = 1 means the ship is making a complete wrap of the screen each second, this kind of makes sense.

I haven't implemented player input yet, so there is no acceleration.  This is likely where I'll start tomorrow.

**Link(s) to Work**

1. [ai-asteroids](https://github.com/BillRobitskeJr/ai-asteroids)

### Day 3: January 3, Thursday

**Starting Thoughts**

Nothing complicated tonight, just getting player input working:
- Turn Left
- Turn Right
- Thrust
- Fire
- Hyperspace Jump

**Today's Progress**

Well, I can rotate and engage a hyperspace jump.  However, acceleration is not working right.

**Thoughts**

... I don't want to talk about it.

...other than, I need to give up on polar velocities for now and make sure I'm processing the heading correctly.

**Link(s) to Work**

1. [ai-asteroids](https://github.com/BillRobitskeJr/ai-asteroids)

### Day 4: January 4, Friday

**Starting Thoughts**

Simply put, get the ship movement system working in a sane fashion.  Yes, speed and direction made it easy to keep the speed in check, but it ends up making the math more complicated than it really needs to be.  Just use a Cartesian vector, you goof.

**Today's Progress**

Effectively only began converting things over to Cartesian vectors.  Added a matrix class so I can treat the math more cleanly.  Instead of creating a bunch of conversion functions and then looping through them, I can now just use marix addition and multiplication.

Unfortunately, the game's no longer in a "working" state.

**Thoughts**

Converted ship velocity over to a Cartesian vector, but tried to change things over to using arrays instead of objects, which in turn led to refacting the whole damned thing - views, physics, etc.

Eventually, I just decided it would be simpler to just use matrices.  I was basically trying to do this anyway with the arrays, but true matrices would allow me to perform the math more clearly than the mess of `Array.prototype.map` calls I was heading towards.

I also decided to switch the game coordinates to use the center of the game environment as the origin (0, 0), with x increasing towards the right and y increasing towards the top of the window.  The canvas's y coordinates, however, are flipped, with y increating towards the bottom.  That's basically what I'm working through now - coming up with the translation factors for converting game coordinates to canvas coordinates.

**Link(s) to Work**

1. [ai-asteroids](https://github.com/BillRobitskeJr/ai-asteroids)

### Day 5: January 5, Saturday

**Starting Thoughts**

Just more work to do to get this thing working again.

**Today's Progress**

Got things working at least as well as it was on Day 2, plus hyperspace jumping.

**Thoughts**

Tomrrow, I focus on getting turning working properly again.  Currently, your heading while turning is limited to 0 - 1, expect the new range for heading is 0 - 2&pi;.  Also, expecting the smaller range, the speed of turning needs to be increased as well.

**Link(s) to Work**

1. [ai-asteroids](https://github.com/BillRobitskeJr/ai-asteroids)

### Day 6: January 6, Sunday

**Starting Thoughts**

I was mixed this morning on if I really needed (or should) to continue writing "starting thoughts" on the day's work.  If I'm talking about what my plan is for the day, then the short answer for today would be "keep working on the thing".  However, I also realize that some of the headaches I've encountered so far were due to poor planning - which is what I first included my "starting thoughts" to address.

At the same time, is there room for more than just my plan for today in this section.  If my closing thoughts is a reflection on the day's work, then maybe my starting thoughts can be a reflection on where I'm going moving forward.

So, on that note - where am I going with this?  Clearly, first off is getting the game working in terms of a traditional Asteroids clone, with the observer view.  With that in mind, the ship controls should be working by day's end.  Shooting is the likely the only real concern as that's require adding shot entities.  Not a major issue, as they're primarily just a position and velocity (ship lite?)  After that'll be adding asteroids to avoid and destroy -- and die to.  Once all of that is working for the observer view, then I'll return to the ship-perspective view.  And then, once that's done, I should be good for developing the AI.

**Today's Progress**

- **Ship movement works fully.**  Turning works correctly again, and you can thrust.  There is no maxiumum speed, but the controls feel pretty good.  Thrust is not reflected in the player view at this time.
- **Ship shooting implemented.**  Shots project from the point of the ship with a set muzzle velocity relative to the ship's current velocity.  Currently, there is no limit on firing rate beyond the framerate.

**Thoughts**

I'm much happier with the matrix math.  It really made adding the shots simple - just calculate the shot's ship-relative velocity, then add the ship's velocity.  (That seems like a really trivial thing to be happy about, but I'm more happy that the code is also really that trivial.)

Two things that I may want to adjust in the future, but I'm okay with now:
- There are no "maximum velocity" for the ship or shots.  It gets a little insane if you hold the thruster down.  I do want to have a maximum velocity at some point, but I'd rather get this thing working first.
- The shots don't have a "lifespan".  They stay around forever and eventually turn the game into a massive bullet hell.  Currently, there's no collision with the ship, but it would become nearly impossible to dodge them if you keep missing.  I do like the idea of the shots sticking around indefinitely as a "physical" entity, but I may want to adjust the firing rate depending on how it goes once the asteroids are added and collision is in place.

**Link(s) to Work**

1. [ai-asteroids](https://github.com/BillRobitskeJr/ai-asteroids)

### Day 7: January 7, Monday

**Starting Thoughts**

I spent some time last night and this morning tinkering around with a physics system.  My thoughts are to have the game completely physics based - the asteroids, ship(s), and shots would transfer momentum when they collide.  I figured it would be awesome to see things deflecting off each other, causing them to spin out of control.  This would also produce some interesting side effects:
- You wouldn't have direct control over your heading; you'd have rotation thrusters that would change your angular velocity similar to your main thruster for adjusting your linear velocity.
- Your shots would affect your ship's velocity; the momentum granted to the shot would be balanced out by impacting the ship's momentum as well.
- Your shots would primarily impact asteroids momentum rather than immediately breaking them apart.  It doesn't seem realistic for a single tiny shot to crack a giant asteroid in half, and it would be more entertaining to just knock them spinning off first.  The dilemna, though, is at what point should an asteroid break up.

However, none of that helps me actually get this thing working!  Oops.  So, while I definitely have put in at least an hour of work today, it's not work that I'm committing to the repository.  (At least not yet.)

So, this evening, I'm going to try to at least add the asteroids to the game.  I'm not sure about collision yet, but just having some rocks floating around would at least be something I'd count as progress.

**Today's Progress**

- Added asteroids entities.  A new asteroid is spawned every five seconds with random position, linear velocity, orientation, and angular velocity.  They shape is procedurally generated based around a mean radius.
- Added a gaussian random number generator to facilitate generating points for the asteroids.

**Thoughts**

First off, I think I may slow down the spawn rate for asteroids and decrease their linear velocity.  Now that I have a guassian random number generator, I may go with a mean velocity so they don't all go shooting off like a rock-et.  (sorry.)

Nevertheless, asteroids came together pretty smoothly.  The procedural shape generation did take some tinkering.  At first, I just picked random angles and a random radius within 5% of the radius of the asteroid, but that tended to create boxy asteroids.  Then I tried various ways of ensuring the angles got spread out pretty evenly to limited results.  Finally, I decided to go the gaussian random route.  I wanted the angles to average evenly around the asteroid's circumference, and I wanted the points to be somewhere around the asteroid's mean radius.

Clearly the normal distribution route was the right tool for the job.  With only a bit of tweaking to the angles' normal distribution, I got a nice rocky-looking asteroid.

**Link(s) to Work**

1. [ai-asteroids](https://github.com/BillRobitskeJr/ai-asteroids)

### Day 8: January 8, Tuesday

**Starting Thoughts**

I'm going in a bit different direction today - mostly because it was keeping me up last night thinking about it.

The [Games Done Quick schedule](https://gamesdonequick.com/schedule) is great, but it would be better if I could easily add a run to my calendar so I can have a reminder when a particular run is going to start - say the 3:45am Nier: Automata run.  So, the solution that came to me last night was if I could have a link in my browser that would generate "Add to Calendar" links for each run on the calendar that'd allow me to quickly add it to my Google Calendar.

**Today's Progress**

Bookmarklet works great(-ish).  The game names on the GDQ schedule for any upcoming runs are replaced with links to download an .ics file for that run.

**Thoughts**

Reading the schedule came together pretty easily.  Each run basically required reading three lines - a date (which comes before that day's runs) and two run detail rows.  Nicely, the GDQ web team provided a couple nice classes to identify the date row and the second of the two run details rows.

My first challenge was generating the .ics files.  I thought I had it all ready, but the files wouldn't actually import into Apple Calendar.  Luckily, I found an [iCalendar validator](https://icalendar.org/validator.html) (Thanks, Dan Cogliano!) which made quick work of telling me that:
- My line breaks were in the wrong format.  For iCalendar files, they **must** be Carriage Return-New Line (`\r\n`).  Apparently, normal new lines (`\n`) were not sufficient.
- That I didn't have any iCalendar components in the file.  For some reason, `EVENT` and `VEVENT` are not the same thing.  Who knew?! (Everyone!  Everyone knew!)

Correcting those issues left me with a fully working script... that wasn't minified.  I was originally using webpack to optimize the output, but then the code wouldn't work outside webpack's boilerplate.  Eventually, I switched to [uglify-js](https://www.npmjs.com/package/uglify-js) (since that's all I really wanted), which in turn led me to upgrading Node.js (How was I still on version 7?!) and installing [Babel](https://babeljs.io/) (as uglify-js only works with ES2015 code).

...which led me to the point my last headache.  The bookmarklet doesn't work in Mobile Chrome!  I can add it to the bookmarks, but it does nothing when I try to run it.

As I cannot find anything on whether bookmarklets actually still work in Mobile Chrome, and not having web tools configured to allow debugging code running on mobile, I had to call it good enough.  I was able to learn some new tech (the iCalendar file format and generating download files), and I met the requirement of creating calendar items for AGDQ 2019 runs (*grins at his filled schedule for the week*).

I might revisit the idea come Summer Games Done Quick (SGDQ).  I'm thinking a separate site that reads the schedule and generates are more featured version that's mobile-friendly (not that the official one isn't mobile-friendly).

**Link(s) to Work**

1. [gdq-schedule-calendar-links](https://github.com/BillRobitskeJr/gdq-schedule-calendar-links)

### Day 9: January 9, Wednesday

**Starting Thoughts**

Back to Asteroids, today.  In particular, I want to get collision working at least with the asteroids.  When they collide they should break up and deflect off based on their momentum.

**Today's Progress**

Well, I managed a to figure out a few ways that don't work...

**Thoughts**

I did manage identify the asteroid colisions and attempted to handle them.  ...then I failed at physics.
1. I applied the transferred momentum to the impacted asteroid, but forgot to actually remove it from the impacting one. *sigh*
2. I based the transferred momentum on the asteroids "universal" velocity, not the relative velocity.

The result, two asteroids touch each other and then vanish as they seemingly hit lightspeed.  *headdesk*

**Link(s) to Work**

None...

### Day 10: January 10, Thursday

**Starting Thoughts**

Yesterday's attempt to get collision working failed, so today's objective is to get it actually working.  I may have been playing around with the physics the other day, but yesterday taught me that I need to actually work on that properly.

**Today's Progress**

Switched over to the new physics engine, but there are a bugs to work out.

**Thoughts**

Yay for "real" physics!  Boo for values turning into "Not a Number" at some point.  I have no idea why yet.  As such, I haven't really bothered to update the player commands to work with the new physics `ShipEntity` object.  Nevertheless, I'm calling it progress - just not complete.

In other news, I've found that the GDQ schedule is more of suggestions.  I'm finding the runs start far sooner than previously scheduled, so your calendar events become outdated rather quickly.  With my next attempt at this scheduling thing, making a true web app that can watch for schedule updates and alert the user automatically may be best.

**Link(s) to Work**

1. [ai-asteroids](https://github.com/BillRobitskeJr/ai-asteroids)

### Day 11: January 11, Friday

**Starting Thoughts**

Simple:  Figure out what's causing the momentums to eventually reach NaN territory (and fix it, of course).

**Today's Progress**

Corrected angles in collisions, but collisions are still "creating" momentum.  Disabled player ship and limited to only two asteroids for testing collisions.

**Thoughts**

The math is working correctly from what I can tell, but the momentum is increasing with each collision.  I guess I need to go back to the physics more, but my approach doesn't seem wrong from my understanding (change in momentum = +momentum transferred from other object + -momentum transferred to other object).  I'll have to investigate further tomorrow.

**Link(s) to Work**

1. [ai-asteroids](https://github.com/BillRobitskeJr/ai-asteroids)

### Day 12: January 12, Saturday

**Today's Progress**

None.

**Thoughts**

Between being out of town most of the day, and the finale of Awesome Games Done Quick, I slacked on my physics homework and didn't get any coding done.

### Day 12 (Take 2): January 13, Sunday

**Today's Progress**

- Reimplemented collision algorithm (correctly this time).  Asteroids now properly bounce off each other.
- Re-enabled asteroid breakage.  Adjusted fragment ratio to allow more variance between the two fragments' masses and share of momentum.  Also corrected logic around ratio limits; asteroid doesn't break if the ratio is less than or equal to 0 or greater than or equal to 1 (as one of the fragments' mass would be then zero or negative).
- Adjusted fine tuning to allow for smaller asteroid fragments and to maintain at least 3 asteroids in play.

**Thoughts**

Well, I was making the collision calculation more complicated than it needed to be.  By doing it properly - using a center-of-mass reference frame - the calculations were far simpler.  After implenting it correctly, I believe I was actually doubling the momentum change; I was treating each collision as two separate events rather than one.

With this mess done, it looks like it's time to return to the ship and shot implementations.

**Link(s) to Work**

1. [ai-asteroids](https://github.com/BillRobitskeJr/ai-asteroids)

### Day 13: January 15, Tuesday

**Starting Thoughts**

...slacker...

**Today's Progress**

- Added handling of forces on physics entities, allowing for proper linear acceleration.
- Add player's ship back into the game, and it's properly configured for the new physics engine.
- Reimplemented shooting mechanic.
- Implemented a basic "isAlive" flag for ships, so avoid the game logic continuing to allow shooting after the ship's destroyed.
- Implemented a basic fitness score - currently how long the player's ship has been alive.

**Thoughts**

It's kind of a real game now.  The fitness score isn't directly displayed to the player, but is logged to the console.

The shooting mechanic is still just setting the shots' velocities to a speed relative to the firing ship's velocity.  With the focus on proper physics, it really should be a result of force on the shot (and a reactive force back on the ship).

So, I guess the next major piece to implement is the player-perspective view.

**Link(s) to Work**

1. [ai-asteroids](https://github.com/BillRobitskeJr/ai-asteroids)

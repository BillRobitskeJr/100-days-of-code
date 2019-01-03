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

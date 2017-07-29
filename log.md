# 100 Days Of Code - Log

### Day 1: July 17, Monday

**Today's Progress**

Began work on a bookkeeping REST API - I'm going to be intentional about adhering to behavior-driven development with this project.  So far, so good.

**Thoughts**

Live streaming my work is a bit fun, especially when I have to call myself out on my typos.  "There is not 'c' in that word!"

**Link(s) to Work**

1. [Bookkeeping](https://github.com/BillRobitskeJr/bookkeeping)
2. [BillRobitskeJr/bookkeeping on Travis CI](https://travis-ci.org/BillRobitskeJr/bookkeeping)
3. [Recording of Live Coding Broadcast](https://www.twitch.tv/videos/159967763)

### Day 2: July 18, Tuesday

**Today's Progress**

Implemented POST-ing new accounts to the server.

**Thoughts**

Things when pretty smoothly tonight.  Not really a whole lot to say...

**Link(s) to Work**

1. [Bookkeeping](https://github.com/BillRobitskeJr/bookkeeping)
2. [BillRobitskeJr/bookkeeping on Travis CI](https://travis-ci.org/BillRobitskeJr/bookkeeping)
3. [Recording of Live Coding Broadcast](https://www.twitch.tv/videos/160235730)

### Day 3: July 19, Wednesday

**Today's Progress**

Implemented GET-ing a single accounts resource via GET /api/accounts/:id and added links.self URLs to returned accounts resources when GET-ing or POST-ing to /api/accounts or GET-ing /api/accounts/:id.

**Thoughts**

Something's causing my keyboard to freak out occasionally, which leads to me spamming the keyboard for a moment to get it to type anything.  Not really a programming issue, but it is definitely an annoyance *while* programming.  Also, my stream kept seeming to drop tonight.  I'm not yet sure if it was a fluke, or if there's something wrong with my connection.  Perhaps I have finally outgrew my bandwidth.  (Now, if I only trusted Comcast to give me more bandwidth than I'm *supposed* to get now, that'd be great...)

On the actual programming front, I am continuing to find behavior-driven development greatly useful.  Even if I don't really have anything to *show* for my efforts - no fancy front end, or standing server, etc - I can still incrementally verify that my code is serving its purpose.  It's not quite minimum viable product, but it's minimum "visible" product...?

Now, if I could just figure out how to automate my front-end testing...

**Links to Work**

1. [Bookkeeping](https://github.com/BillRobitskeJr/bookkeeping)
2. [BillRobitskeJr/bookkeeping on Travis CI](https://travis-ci.org/BillRobitskeJr/bookkeeping)
3. [Recording of Live Coding Broadcast](https://www.twitch.tv/videos/160490397)

### Day 4: July 20, Thursday

**Today's Progress**

Implemented updating accounts resources via PATCH /api/accounts/:id (9 new tests).  Also cleaned up the code in the AccountsRoute module some ("Don't Repeat Yourself").

**Thoughts**

I didn't stream tonight - stayed out too late, and didn't feel like running a 10pm stream.  On the plus side, however, I'm now definitely at a point where a web interface would have a useful API to utilize.  That will be my goal tomorrow - a web interface to view, add, and modify a chart of accounts.

I also discovered the [/r/dailyprogrammer](https://www.reddit.com/r/dailyprogrammer) subreddit last night.  This thing is awesome - random programming challenges!  Now, I have somewhere to go when I need a break from my projects, but want a coding problem to work on to keep up on my goal.

**Links to Work**

1. [Bookkeeping](https://github.com/BillRobitskeJr/bookkeeping)
2. [BillRobitskeJr/bookkeeping on Travis CI](https://travis-ci.org/BillRobitskeJr/bookkeeping)
3. ...no stream... :disappointed:

### Day 5: July 21, Friday

**Today's Progress**

No new progress on "Bookkeeping"; I instead worked on a couple /r/dailyprogrammer challenges - [#323 Intermediate](https://www.reddit.com/r/dailyprogrammer/comments/6mtvbk/20170712_challenge_323_intermediate_parsing/) & [#321 Easy](https://www.reddit.com/r/dailyprogrammer/comments/6jr76h/20170627_challenge_321_easy_talking_clock/).  I pulled together the solution for 321 pretty easily, but I only got as far as the third address on 323.  I swear that the format of the input address is wrong based on everything I can find on Greenland's address format.

**Thoughts**

My plan to work on front-end development for "Bookkeeping" tonight led me to insist on streaming the work.  Unfortunately, technical problems with the twitch.tv dashboard ([Tweet from @TwitchSupport](https://twitter.com/TwitchSupport/status/888531368329838595)) led me to wait until after I got home from a little league baseball game.  Double-unfortunately, I didn't get back home until after 10, and didn't feel like streaming by then.

Fortunately, I did have /r/dailyprogrammer to fall back on for something to do to get my hour of work in.  Hooray!

**Links to Work**

1. [Solution to /r/dailyprogrammer Challenge #321 - Easy - Talking Clock](https://gist.github.com/BillRobitskeJr/9a3cce6661b69c2fa32fd43f1ff54aa4)

### Day 6: July 22, Saturday

**Today's Progress**

Started work on a basic web front-end for the chart of accounts API I've been working on.  It successfully reads in the accounts and allows adding new accounts.  Nothing yet for cases where the new account number is already in use (it errors, but nothing is displayed on screen).  Also, it doesn't yet let you edit accounts.

**Thoughts**

I decided to go the Custom Elements v1 route here, so we're talking about modern browsers only.  That is great and all, but it also means that using LESS is pretty much use-LESS. :stuck_out_tongue_winking_eye:

**Links to Work**

1. [Bookkeeping](https://github.com/BillRobitskeJr/bookkeeping)
2. [BillRobitskeJr/bookkeeping on Travis CI](https://travis-ci.org/BillRobitskeJr/bookkeeping)
3. [Recording of Live Coding Broadcast](https://www.twitch.tv/videos/161174355)

### Day 7: July 23, Sunday

**Today's Progress**

Started writing specification tests - tonight working on the Account class constructor.  I also changed the `isPermanent` property to be based on the account's `number`, and added an `accountType` property that does the same.

**Thoughts**

I'm using dynamically generated tests for the specification tests.  More tests to ensure that future changes don't break anything that I don't expect - which is the whole point of the behavior-driven/test-driven design thing, right?

**Links to Work**

1. [Bookkeeping](https://github.com/BillRobitskeJr/bookkeeping)
2. [BillRobitskeJr/bookkeeping on Travis CI](https://travis-ci.org/BillRobitskeJr/bookkeeping)

### Day 8: July 24, Monday

**Today's Progress**

- Updated the REST API to include the `accountType` property in "accounts" resources
- Updated the tests for the REST API to reflect the addition of the `accountType` property
- Updated the front end to display the Account Type
- Updated the front end to automatically set the `accountType` and `isPermanent` values of new accounts based on the account number
- Updated the front end to allow for editing and saving changes to existing accounts -- _Currently, the only modification possible is changing the account name._

**Thoughts**

Dealing with DOM in TypeScript is a bit annoying.  It cannot tell what elements (if any) will be returned by `.querySelector`, so it insists that it could return null even when you just defined the content of the element being queried.  This leads to having to include a bunch of statements like the following:

```TypeScript
this.shadowRoot.innerHTML = '<div class="target">Content</div>';
const element = this.shadowRoot.querySelector('.target');
if (!element) return; // WHY...
element.innerHTML = 'New Content';
```

**Links to Work**

1. [Bookkeeping](https://github.com/BillRobitskeJr/bookkeeping)
2. [BillRobitskeJr/bookkeeping on Travis CI](https://travis-ci.org/BillRobitskeJr/bookkeeping)

### Day 9: July 28, Friday

**Today's Progress**

- Added `AccountsStore` class to save/load accounts to/from a JSON file
- Updated `AccountsRoute` to accept an `AccountsStore` instance upon creation
- Updated `AccountsRoute` to save its `AccountsStore` when accounts are added via `POST /api/accounts` or updated via `PATCH /api/accounts/:id`
- Updated `Server` to create an `AccountsStore` if provided an `accountsFile` when created
- Updated `Server` to pass this `AccountsStore` instance to its `AccountsRoute` instance
- Updated `index.ts`/`index.js` to persist accounts data to `./accounts.example.json`

**Thoughts**

Yeah, I'm missed a few days due to illness and personal issues.  Now that I'm back, I'm planning to get 4 hours in tomorrow to catch up.

**Links to Work**

1. [Bookkeeping](https://github.com/BillRobitskeJr/bookkeeping)
2. [BillRobitskeJr/bookkeeping on Travis CI](https://travis-ci.org/BillRobitskeJr/bookkeeping)

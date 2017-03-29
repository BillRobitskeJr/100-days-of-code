# 100 Days Of Code - Log

### Day 1: March 22, Thursday

**Today's Progress**

Today, I restarted my Lasagna task tracking app.  I'm still using Firebase for
hosting (and storage once I get there), but I'm going with Custom Elements v1
instead of Polymer this time.  We'll see how long that line of thought lasts.

> Why add all that overhead when I can create my own (overhead)?

As for work completed, there's not much to look at.  I have the start of the
activity log, sans any styling or real behavior.

**Thoughts**

This is more a thought from yesterday, but it is what finally gave me the
confidence with myself to recommit to this.

Custom Elements v1 shouldn't be viewed as "one thing" the way it kind of worked
in v0 and in Polymer.  It's two -- the behavior your defining (via an ES6 class)
and the direction for the browser to use that behavior when it sees a tag with a
particular name.  It seems like a meaningless detail until you realize that you
can tell multiple tags to use the **same behavior**!  That said, the call to
`window.customElements.define` should be left to the "client" code, as that's
where the tag name we want to use that behavior will actually be decided.

It was this thought that finally got me past thinking I was hacking my way
around Webpack omitting my custom element modules entirely if I didn't make some
use of the class.

**Link(s) to Work**

1. [Lasagna](https://lasagna-d5007.firebaseapp.com)
2. [GitHub Repo](https://github.com/DigitalMugen/lasagna)

### Day 2: March 24, Friday

**Today's Progress**

I added [multiview](https://www.npmjs.com/package/multiview) and
[watch-cli](https://www.npmjs.com/package/watch-cli) to save me some work
calling Webpack and copying the bundle over to the public folder.

I also started working on styling the activity log... which is clearly a work in
progress because why `<input>`?  Why?

**Thoughts**

Brains...?

Really, I can't think of anything to put under thoughts tonight...

...scratch that - plans for moving forward!  Now that I've figured out how to
get Custom Elements v1 working in ES5, I need to implement that here.

**Link(s) to Work**

1. [Lasagna](https://lasagna-d5007.firebaseapp.com)
2. [GitHub Repo](https://github.com/DigitalMugen/lasagna)

### Day 3: March 25, Saturday

**Today's Progress**

Updated build process to output ES5 code rather than ES6.  This required adding
[webcomponents.js](https://github.com/webcomponents/webcomponentsjs)'s
`custom-elements-es5-adapter.js` to make ES5 compiled "Custom Elements v1"
classes work and `webcomponents-lite.js` to polyfill Custom Elements v1 features
in older browsers.

I also revised how I was building my Shadow DOM content to use
[diffHTML](https://diffhtml.org/) instead of trying to directly reference DOM
objects that needed to change.  This allows me to define the HTML content once
and leave determine _what_ needs to be updated to diffHTML.

**Thoughts**

> I feel like I keep going around in circles on this project - because I keep
> learning "better" ways of doing things.  #100DaysOfCode
-- [@BillRobitskeJr on Twitter](https://twitter.com/BillRobitskeJr/status/845745692010262528)

I started to pull in [Babel] to transpile the ES6 code I had TypeScript
outputting, but decided to just let TypeScript output ES5 (with CommonJS-style
modules).  With the newer version of the webcomponents.js polyfills/shims, I
couldn't really see the benefit of the added complexity of deciding which
version of the code - ES5 or ES6 - to pull in at page load.

**Link(s) to Work**

1. [Lasagna](https://lasagna-d5007.firebaseapp.com)
2. [GitHub Repo](https://github.com/DigitalMugen/lasagna)

### Day 4: March 26, Sunday

**Today's Progress**

Moved the contents of the `<lasagna-activity-log-activity>` internal element
(which is also a tag name that just rolls off the tongue) into a method of the
`<lasagna-activity-log>` element class.

**Thoughts**

I must be doing something wrong with diffHTML - it works for the main class, but
its `innerHTML` function doesn't seem to work when rendering a subelement.  No
idea why at the moment, but the sub-element was a bit overkill anyway.  I'll
have to see if a different function would/will work better if I ever truly need
nested elements - which is certain to happen at some point.

**Link(s) to Work**

1. [Lasagna](https://lasagna-d5007.firebaseapp.com)
2. [GitHub Repo](https://github.com/DigitalMugen/lasagna)

### Day 5: March 27, Monday

**Today's Progress**

"Progress" is arguable, but I did continue trying to use diffHTML to handle
updating the shadow DOM based on a template string.  Unfortunately, I still
cannot get it to work nested - there's a `bufferSet` flag that is set during the
inner call to `innerHTML` which "short circuits" updating the DOM.

Revising the TypeScript declarations for the module, however, did get it working
for just `this.shadowRoot` in the `LasagnaActivityLogElement` class, which makes
it much cleaner.

**Thoughts**

My suspicions at the moment are that I need to use tagged template strings
instead of normal "vanilla" template strings.  Unfortunately, I haven't figured
out how to get TypeScript to accept the `html` function as a template tag.  The
official documentation hasn't been any help yet.
[Another site](https://basarat.gitbooks.io/typescript/docs/template-strings.html)
makes it sound possible, though.

**Link(s) to Work**

1. [Lasagna](https://lasagna-d5007.firebaseapp.com) -- Still yesterday's version
2. [GitHub Repo](https://github.com/DigitalMugen/lasagna)

### Day 6: March 28, Tuesday

**Today's Progress**

Not much... I was able to get tagged template strings working, but that didn't
resolve the issue.

**Thoughts**

I'm not seeing away around the `bufferSet` issue with diffHTML.  While I think
the idea behind the library is great, if I'm going to have to work around it,
I may as well do it the vanilla JS/DOM way.  Yes, direct DOM manipulation is
expensive, but I can mitigate it.  Wasn't that the whole reason why libraries
like diffHTML were made?

**Link(s) to Work**

1. [Lasagna](https://lasagna-d5007.firebaseapp.com) -- Still Day 4's version
2. [GitHub Repo](https://github.com/DigitalMugen/lasagna)

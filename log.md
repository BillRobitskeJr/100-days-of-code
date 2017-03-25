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

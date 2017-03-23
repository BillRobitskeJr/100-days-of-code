# 100 Days Of Code - Log

### Day 1: March 22, Thursday

**Today's Progress**:

Today, I restarted my Lasagna task tracking app.  I'm still using Firebase for
hosting (and storage once I get there), but I'm going with Custom Elements v1
instead of Polymer this time.  We'll see how long that line of thought lasts.

> Why add all that overhead when I can create my own (overhead)?

As for work completed, there's not much to look at.  I have the start of the
activity log, sans any styling or real behavior.

**Thoughts**:

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

**Link(s) to work**

1. [Lasagna](https://lasagna-d5007.firebaseapp.com)
2. [GitHub Repo](https://github.com/DigitalMugen/lasagna)

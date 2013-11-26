<section class="post-content">
One of the trickier aspects of encapsulating Shadow DOM CSS is figuring out how
much access the parent document should have. Initially it was thought that the 
Shadow DOM’s author would decide which elements could be exposed for styling
[by using `part` attributes][1], but it seems like that might be too limiting.
The thinking now is that the shadow boundary should prevent*accidental* styling
of the shadow DOM, but allow intentional styles. That’s where the new “cat” and
“hat” CSS selectors come in.

## Support [][2] 

In order to try the examples I suggest you use [Chrome Canary][3] v33 or
greater.

Also make sure you’ve enabled **Experimental Web Platform features** in Chrome
’s`chrome://flags`.

## The Hat [][2] 

The hat selector, a single caret ( ^ ), allows the parent document to pierce
the**upper shadow boundary** and style elements that are one shadow root deep.
If you have an element that only has one shadow root you can style pretty much 
anything inside of it using the hat.

See the Pen [Shadow DOM “Hat” CSS selector][4] by Rob Dodson ([@robdodson][5])
on[CodePen][6]

## The Cat [][2] 

The cat, a double caret ( ^^ ) is much more powerful. It allows you to pierce
every layer of the shadow DOM, so if you have shadow DOM within shadow DOM (a 
common occurrence when you nest custom elements) you can style all of them at 
once.

See the Pen [Shadow DOM “Cat” CSS selector][7] by Rob Dodson ([@robdodson][5])
on[CodePen][6]

## Styling Native Elements [][2] 

[@Volker_E asked][8] if the cat and hat selectors could be used to style the
shadow DOM of native elements like`<video>`. As it turns out that *does*
work, which is pretty cool.

See the Pen [Shadow DOM “Cat” and “Hat” CSS selectors][9] by Rob Dodson (
[@robdodson][5]) on [CodePen][6]</section>

 [1]: http://robdodson.me/blog/2013/08/29/shadow-dom-styles-cont-dot#parts
 [2]: http://robdodson.me/blog/2013/11/15/the-cat-and-the-hat-css-selectors/
 [3]: https://www.google.com/intl/en/chrome/browser/canary.html
 [4]: http://codepen.io/robdodson/pen/EhIax
 [5]: http://codepen.io/robdodson
 [6]: http://codepen.io
 [7]: http://codepen.io/robdodson/pen/wFqJg
 [8]: https://twitter.com/Volker_E/status/401202275009310722
 [9]: http://codepen.io/robdodson/pen/iaJHd
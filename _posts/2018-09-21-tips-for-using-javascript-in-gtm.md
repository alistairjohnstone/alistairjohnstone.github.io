---
published: true
title: JavaScript tips for Google Tag Manager
---
Knowing JavaScript can get you a long way in GTM, after all, it's essentially just a JavaScript library. There are two main places you can use JavaScript in GTM: Custom JavaScript Variables and Custom HTML tags. 

![]({{site.baseurl}}/assets/images/javascript-tips.jpg)

Here’s a few things that I have found useful to know, and hopefully you will too.

## Use querySelector() and querySelectorAll()

You may be tempted to use the age old methods `getElementByTagName()` or `getElementById()`, which are perfectly valid, but wherever possible I’d recommend using CSS selectors in combination with `querySelector()` and `querySelectorAll()`.

![]({{site.baseurl}}/assets/images/querySelector.png)

In my opinion, this combination is one of the greatest ways to leverage GTM because they just make everything easier. For triggers alone, CSS selectors are life-savers because you can use the click element to target pretty much any element on the page, regardless of if they have ID or class attributes.

![]({{site.baseurl}}/assets/images/cssselectors.png)

If you’d like to brush up on your CSS selectors, [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors) and [W3Schools](https://www.w3schools.com/cssref/css_selectors.asp) both have excellent resources.

## Remember to use \<script> tags in your Custom HTML

When adding your JavaScript to Custom HTML tags, always remember to wrap in `<script>` tags. If you forget to do this your JavaScript will be rendered as text at the bottom of the page!

If you haven’t already made this mistake and learned from it, take note.

## You can refer to other GTM variables in the JavaScript context

A really useful feature of GTM is being able to refer to JavaScript variables.

![]({{site.baseurl}}/assets/images/refer-to-variables.png)

Here we are able to remove trailing whitespace from revenue in the ecommerce object.

### Note that resolving a variable is quite an 'expensive' operation.

Statements in a loop are executed for each iteration of the loop, which can slow down your JavaScript.

![]({{site.baseurl}}/assets/images/statements-in-loops.png)

When writing JavaScript, It’s good practice to access the length of the property outside of the loop, this way the function is only evaluated once, which will make it run faster. In GTM, variables are stored as strings which are passed in to an eval() when required, this means calling functions multiple times in GTM will be even slower than usual. Even more reason to avoid putting statements in your loops!

W3schools have more information on JavaScript performance.

### You can even have a variable return a function and call that

This is really handy if you reusing snippets of code in different Custom HTML Tags or Custom JavaScript Variables in your GTM container.

![]({{site.baseurl}}/assets/images/multiply-function.png)

For example, you could have a function that creates a first party cookie, which you could use across multiple tags. When working on bigger projects, this tip can also help free up valuable space in your container, which has a limit of 200kb.

## In the Data Layer, Array indices are accessed using dot notation

Normally in JavaScript we would use bracket notation to access array indices.

![]({{site.baseurl}}/assets/images/bracket-notation.png)

However in the Data Layer Variable, in order to access array indices, you have to remember to use dot notation.

![]({{site.baseurl}}/assets/images/dot-notation.png)

This is a mildly annoying quirk that you soon get used to, however it can catch you out if you’re not aware of it!

Hope some of these tips come in handy for you when working in Google Tag Manager!

## Further reading

Websites

- [Codeacademy JavaScript Course](https://www.codecademy.com/learn/introduction-to-javascript) - a great introduction to JavaScript
- [W3schools JavaScript - Reference](https://www.w3schools.com/js/default.asp)
- [MDN JavaScript - Reference](https://developer.mozilla.org/bm/docs/Web/JavaScript)
- [W3schools CSS Selectors - Reference](https://www.w3schools.com/cssref/css_selectors.asp)
- [MDN CSS Selectors - Reference](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors)

Books

- [DOM Enlightenment](http://shop.oreilly.com/product/0636920027690.do)
- [JavaScript: The Good Parts](http://shop.oreilly.com/product/9780596517748.do)
- [Professional JavaScript for Web Developers](https://www.amazon.co.uk/Professional-JavaScript-Developers-Wrox-Guides/dp/1118026691)

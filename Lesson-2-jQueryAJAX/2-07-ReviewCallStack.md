# Review the Call Stack

The DevTools has a ton of helpful information! If you're not familiar with them, you really should spend some learning about all of its features. It really makes developing and debugging websites a lot easier! One helpful piece of info that DevTools provides is the JavaScript Call Stack. 

The Call Stack displays the order of function calls that are in progress. The function at the bottom of the stack is the first one to run. It calls the second one on the stack...the second calls the third, the third… you get the idea. A function stays on the stack until the one above it returns.

We can click on the bottom function in the stack (the `anonymous function`) to see that what kicked all this code off was the `$.ajax()` call for the Unsplash images. That `$.ajax()` call in turn calls `transport.send()`, which calls `options.xhr()`, which creates a new `XMLHttpRequest()` object!

So the order is:

1. our code in an anonymous function calls `$.ajax()`
1. `.ajax()` calls a `.send()` method
1. `.send()` calls `options.xhr()`
1. `options.xhr()` calls `jQuery.ajaxSettings.xhr` which creates a new XHR object

![Clicking through the call stack to see the order of function calls](../img/ud109-l2-jquery-xhr-call-stack.gif)
Clicking through the call stack to see the order of function calls

## QUESTION 1 OF 2

When `$.ajax()` is called, does the jQuery code create a new XHR object each time or does it create an initial one and reuses it for each subsequent call to `.ajax()`?

- [X] creates a new one each time
- [ ] reuses the existing XHR object each time

Look at jQuery's code and especially the `jQuery.ajaxSettings.xhr` function, we can see that the code is `return new window.XMLHttpRequest();`. So this code will return a new XHR object every time it's called (which happens every time $.ajax() is run!).

## QUESTION 2 OF 2

Try working through the `.send()` function (the third item from the bottom of the call stack) on your own to see how it sets up the newly created XHR object. After reviewing the code, how does it set all of the headers?

- [ ] `for` loop
- [ ] `while` loop
- [X] `for...in` loop
- [ ] `do while` loop

jQuery uses a `for…in` loop to iterate over the data in the `headers` object. This can be seen on lines `9094-9096`.
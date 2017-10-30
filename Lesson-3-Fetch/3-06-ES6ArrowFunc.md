# ES6 Arrow Function

You might be thinking that this Fetch request is starting to look like a lot of code...and it is. One quick way to shrink the amount of code is to use an ES6 Arrow function! We can convert the first `.then()` function that gets the response, calls the `.json()` method on it, and returns a Promise all to a single line with an Arrow function:

```js
// without the arrow function
}).then(function(response) {
    return response.json();
})

// using the arrow function
}).then(response => response.json())
```

So the new request would be:

```js
fetch(`https://api.unsplash.com/search/photos?page=1&query=${searchedForText}`, {
    headers: {
        Authorization: 'Client-ID abc123'
    }
}).then(response => response.json())
.then(addImage);

function addImage(data) {
    debugger;
}
```

If Arrow functions are new to you, check out our [ES6 course](https://classroom.udacity.com/courses/ud356)!

![Browser showing the app with DevTools loaded. A search for "trees" is made. The browsers pauses at the debugger line. The actual JSON response appears on the console.](../img/ud109-l3-request-json-response.gif)
*Browser showing the app with DevTools loaded. A search for "trees" is made. The browsers pauses at the debugger line. The actual JSON response appears on the console.*
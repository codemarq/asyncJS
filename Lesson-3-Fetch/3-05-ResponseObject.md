# The Response Object

See how the response that's returned is of the `Response` type? This `Response` object is new with the Fetch API and is what's returned when a Fetch request resolves.

Ok, so that's great and all, but did you notice anything weird about the response object? It didn't have any of the data that we searched for! That's because a response object has information about the response itself, it doesn't have the data...yet. To actually get the data, we need to get the "body" of the response.

Since the Unsplash API we're using will return JSON to us, we just need to call `.json()` on the response variable.

```js
fetch(`https://api.unsplash.com/search/photos?page=1&query=${searchedForText}`, {
    headers: {
        Authorization: 'Client-ID abc123'
    }
}).then(function(response) {
    return response.json();
});
```

The `.json()` method on a Response object returns a Promise, so we need to chain on another `.then()` to actually get and start using the returned data. This time, let's call `addImage` to pass it the returned data:

```js
fetch(`https://api.unsplash.com/search/photos?page=1&query=${searchedForText}`, {
    headers: {
        Authorization: 'Client-ID abc123'
    }
}).then(function(response) {
    return response.json();
}).then(addImage);

function addImage(data) {
    debugger;
}
```

There are a number of methods on a Response object. Each one will let the code handle different response types.

For example, the `.json()` method that we've looked at will take the response and convert it to from JSON. What happens if we requested an image, instead?

### QUIZ QUESTION

Which of the following methods should be used if you wanted to fetch an image? If you get stuck, check out:

- [Making fetch requests](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch#Making_fetch_requests)
- [https://davidwalsh.name/fetch](https://davidwalsh.name/fetch)

- [ ] `.arrayBuffer()`
- [X] `.blob()`
- [ ] `.formData()`
- [ ] `.json()`
- [ ] `.text()`

The correct answer is `.blob()`. `.blob()` will extract the image body from the response.
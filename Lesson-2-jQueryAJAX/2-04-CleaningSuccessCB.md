# Cleaning up the Success Callback

Content isn't getting added to the page jQuery detects the response and if it's JSON, it will automatically convert it to JavaScript for us. How awesome is that! So we only need to make a few tweaks to the existing code. Here's what it currently is:

```js
function addImage() {
    const data = JSON.parse(this.responseText);
    const firstImage = data.results[0];

    responseContainer.insertAdjacentHTML('afterbegin', `<figure>
            <img src="${firstImage.urls.small}" alt="${searchedForText}">
            <figcaption>${searchedForText} by ${firstImage.user.name}</figcaption>
        </figure>`
    );
}
```

We just need to change the first three lines:

```js
function addImage(images) {
    const firstImage = images.results[0];

    responseContainer.insertAdjacentHTML('afterbegin', `<figure>
            <img src="${firstImage.urls.small}" alt="${searchedForText}">
            <figcaption>${searchedForText} by ${firstImage.user.name}</figcaption>
        </figure>`
    );
}
```

## What changed

- the function now has one parameter `images`
- this parameter has already been converted from JSON to a JavaScript object, so:
  - the line that had `JSON.parse()` is no longer needed.
- the `firstImage` variable is set to the `images.results` first item

The code that adds the HTML to the response container hasn't changed at all!

### Replace Nytimes Xhr With `$.Ajax()`

Now that we've walked through converting one request from using XHR to jQuery's `.ajax()` method, why don't you give it a shot on your own and convert the second request! Make sure to use the existing code as an example. If you get stuck, check out the documentation page. When you're successfully converted the code to use jQuery's `.ajax()` method and fixed the callback function so it adds the data to the page, check the checkbox to continue.

- [ ] I've successfully coverted the code from XHR requests to `$.ajax()`
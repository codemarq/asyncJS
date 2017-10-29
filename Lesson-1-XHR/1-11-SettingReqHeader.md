# Setting a Request Header

The XHR method to include a header with the request is [setRequestHeader](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/setRequestHeader). So the full code needs to be:

```js
const searchedForText = 'hippos';
const unsplashRequest = new XMLHttpRequest();

unsplashRequest.open('GET', `https://api.unsplash.com/search/photos?page=1&query=${searchedForText}`);
unsplashRequest.onload = addImage;
unsplashRequest.setRequestHeader('Authorization', 'Client-ID <your-client-id>');
unsplashRequest.send();

function addImage(){
}
```

[video](https://youtu.be/rgupp3Tk5tw)

Since the New York Times doesn't require a specific header, we don't need to do anything special. We'll set its `onload` property to the function `addArticles` that we'll flesh out in a minute:

```js
function addArticles () {}
const articleRequest = new XMLHttpRequest();
articleRequest.onload = addArticles;
articleRequest.open('GET', `http://api.nytimes.com/svc/search/v2/articlesearch.json?q=${searchedForText}&api-key=<your-API-key-goes-here>`);
articleRequest.send();
```

Make sure to fill in the URL above with the API key you received in an email from the New York Times after signing up as a developer.

### Adding The Articles

Similar to how we added the Unsplash image to the page. See if you can add all of the New York Times articles to the page. When you''re done, check the box to continue.

- [ ] My code now adds the articles to the page!

[video](https://youtu.be/V3zRuIqdUuU)
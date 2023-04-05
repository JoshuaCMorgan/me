# issue AJAX request to server to get data (url/json)

AJAX (Asynchronous Javascript and XML) lets us send and request data without having to perform a full page load. It isn't a library like jQuery, but a Web API like `XMLHttpRequest`. It lets you make network requests like `XMLHttpRequest`, but it leverages the Promise syntax to provide a much simpler interface

Important to note:

- The Promise that `fetch()` returns won't reject if the response `status` is an HTTP error status code (i.e. response codes in the 4xx and 5xx ranges)
- By default, `fetch()` won't send cookies. In order to send cookies with the request, the `credentials`[parameter](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/fetch#Parameters) must be set to either `include`, or `same-origin`. The latter option sends credentials only if the request URL is on the same origin as the calling script.
- Fetch uses the [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) syntax, which provides `then()` and `catch()` methods.


## Example

A Fetch request takes two parameters: URL and options object.

```javascript
				//path to the resource
fetch('/my-blog-post',
    { method: 'GET' }
  ) // returns a promise that resolves with a Response object
  .then((response) => {
    // do something with the response
  });
```

```javascript
fetch("/comments?photo_id=" + idx)
      .then(response => response.json())
      .then(comment_json => {
        let comment_list = document.querySelector("#comments ul");
        comment_list.insertAdjacentHTML('beforeend', templates.photo_comments({ comments: comment_json }));
    });
```



## Fetch with url encoding

- URL encoding also works with POST requests, 
  - but you must include a `Content-Type` header with a value of `application/x-www-form-urlencoded` .
- Place the encoded name-value string in the request body.

```JavaScript
fetch(/pictures, {
    method:"POST",
    headers: { 'Content-Type': 'application/x-www-form-urlencoded; charset=utf-8' },
    body: "photo_id=1"
})
// if using a local server on port 3000
// this sends request to:
http://localhost:3000/photo_id=1
```

key points:

- `Response` object returned by server allows us to check the HTTP status but we don't ahve the body yet.
- From the response object, we can check status and headers, etch
  - `status`
  - `ok`
- To get response body, we need to make additional method call. [reference](https://javascript.info/fetch)
  - **`response.text()`** – read the response and return as text,
  - **`response.json()`** – parse the response as JSON,
  - **`response.formData()`** – return the response as `FormData` object
  - **`response.blob()`** – return the response as [Blob](https://javascript.info/blob) (binary data with type),
  - **`response.arrayBuffer()`** – return the response as [ArrayBuffer](https://javascript.info/arraybuffer-binary-arrays) (low-level representation of binary data),
  - additionally, `response.body` is a [ReadableStream](https://streams.spec.whatwg.org/#rs-class) object, it allows you to read the body chunk-by-chunk, we’ll see an example later.

## Example JSON
- the `Content-Type` header has a value of `application/json; charset=utf-8`.

```javascript
// Get Request
fetch('https://api.github.com/users/manishmshiva', {
  method: "GET",
  headers: {"Content-type": "application/json;charset=UTF-8"}
})
.then(response => response.json()) 
.then(json => console.log(json)); 
.catch(err => console.log(err));
```

```javascript
// POST request
// data to be sent to the POST request
let _data = {
  title: "foo",
  body: "bar", 
  userId:1
}

fetch('https://jsonplaceholder.typicode.com/posts', {
  method: "POST",
  body: JSON.stringify(_data),
  headers: {"Content-type": "application/json; charset=UTF-8"}
})
.then(response => response.json()) 
.then(json => console.log(json));
.catch(err => console.log(err));
```
#fetch #HTTPheaders #AJAX #urlencoding #encoding


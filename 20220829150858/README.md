# Using a CDN for including JS library in your project

The set-up when using a CDN is exactly the same except that the value of the `src` attribute of the `<script>` tag will be the URL to the file on the CDN:

```html
<!doctype html>
<html lang="en">
   <head>
      <title>My Awesome Project</title>
      <script
        src="https://code.jquery.com/jquery-3.6.0.min.js"
        integrity="sha256-/xUj+3OJU5yExlq6GSYGSHk7tPXikynS7ogEvDej/m4="
        crossorigin="anonymous"
      ></script>
      <script src="/js/app.js"></script> <!-- we can use jQuery in our app.js file -->
      <script>
        // we can use jQuery here
      </script>
   </head>
   <body>
```

## Important notes
- When loading assets from a CDN, it's essential that you include the `integrity` and `crossorigin` attributes within your `script` tag.

These attributes are part of a browser security feature known as **Subresource Integrity**.

- The `integrity` attribute allows browsers to verify that the resource being requested hasn't been manipulated in transit.
- The `crossorigin` attribute enables the browser to accurately process the CORS request.

- You should place the `<script>` tag for the library *before* any script tags where that library is used.

#CDN #external_library
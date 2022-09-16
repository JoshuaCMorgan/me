# creating Ajax requests in jQuery
The `.ajax()` method of jQuery is the most used for doing AJAX tasks.
jQuery’s core `$.ajax()` method is a powerful and straightforward way of creating Ajax requests. It takes a configuration object that contains all the instructions jQuery requires to complete the request. The $.ajax() method is particularly valuable because it offers the ability to specify both success and failure callbacks. Also, its ability to take a configuration object that can be defined separately makes it easier to write reusable code. [AJAX](https://learn.jquery.com/ajax/jquery-ajax-methods/)

basic syntax: The `name:value` in the syntax are the sets of key-value pairs that are used to configure the AJAX request.
```js
$.ajax({
  name: value, 
  name: value, 
 })
```

```js
// Using the core $.ajax() method
$.ajax({
 
    // The URL for the request
    url: "post.php",
 
    // The data to send (will be converted to a query string)
    data: {
        id: 123
    },
 
    // Whether this is a POST or GET request
    type: "GET",
 
    // The type of data we expect back
    dataType : "json",
})
  // Code to run if the request succeeds (is done);
  // The response is passed to the function
  .done(function( json ) {
     $( "<h1>" ).text( json.title ).appendTo( "body" );
     $( "<div class=\"content\">").html( json.html ).appendTo( "body" );
  })
  // Code to run if the request fails; the raw request and
  // status codes are passed to the function
  .fail(function( xhr, status, errorThrown ) {
    alert( "Sorry, there was a problem!" );
    console.log( "Error: " + errorThrown );
    console.log( "Status: " + status );
    console.dir( xhr );
  })
  // Code to run regardless of success or failure;
  .always(function( xhr, status ) {
    alert( "The request is complete!" );
  });
```
#ajax #ajax_request
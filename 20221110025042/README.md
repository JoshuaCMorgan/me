# Trigger event handler bound to an element without any user interaction
"jQuery's event handling system is a layer on top of native 
browser events. When an event handler is added using `.on( 
"click", function() {...} )`, it can be triggered using 
jQuery's `.trigger( "click" )` because jQuery stores a 
reference to that handler when it is originally added." The `.
trigger()` function cannot be used to mimic native browser 
events, such as clicking on a file input box or an anchor tag.

Instead of duplicating our `click` event, we can use `.trigger()` to invoke the event handler function for us.  
In our callback, we could duplicate the `slideToggle` that happens in our `keypress` event,
 but instead we should consider having the toggle only in one place. Then if something changes 
 later on, like the ID we are using, we only have one place we need to make an update to. What 
 we can do instead is to move the `slideToggle` from the `keypress` event to this one, then 
 our `keypress` event can trigger the click event on this anchor. 
```html
<!doctype html>
<html lang="en-US">
  <head>
    <title>jQuery Selectors</title>
    <meta charset="utf-8" />
    <link rel="stylesheet" href="style.css" />
    <script src="https://code.jquery.com/jquery-3.6.1.min.js" integrity="sha256-o88AwQnZB+VDvE9tvIXrMQaPlFFSUTR+nldQm1LuPXQ=" crossorigin="anonymous"></script>
  </head>
  <body>
    <main>
      <form action="" method="get">
        <fieldset>
          <h1>Type a key to toggle the accordion with</h1>
          <input type="text" id="key" name="key" maxlength="1" />
          <input type="submit" value="Set" />
        </fieldset>
      </form>
      <p><a href="#">Toggle accordion</a></p>
      <div id="accordion">
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
      </div>
    </main>
  </body>
  <script>
   $(function() {
    $("form").on("submit", function(e) {
      e.preventDefault();
      var character = $("#key").val();

      $(document).off("keypress").on("keypress", function(e) {
        if (e.key !== character) { return; }
        $("a").trigger("click");
      });
    });

    $("a").on("click", function(e) {
      e.preventDefault();
      $("#accordion").slideToggle();
    });
  });
  </script>
</html>
```
#trigger #trigger-different-event #jquery #form #keypress #accordion #slide
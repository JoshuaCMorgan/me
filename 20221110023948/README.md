# unbinding previous events

Sometimes, created events are based upon user input.  If that 
user input changes, then we must unbind any previous events before
added new ones.

Let's say we have a web page that allows the user to set the key
that will toggle something.  Each time a user sets the new key that
will toggle the event, we first must unbind previous ones. 
Otherwise,  there will eventually be multiple keys that can 
toggle the accordion. By unbinding any previous keypress event, 
we are making it so that only the key that is currently set can 
toggle

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
#unbind #toggle #toggle #trigger #keypress #value #form #off
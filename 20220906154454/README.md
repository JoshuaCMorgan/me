# Handling HTML data attributes with jQuery while hiding/showing content chosen

In short, if you want to get or set the value of an HTML data attribute, use the .attr method. As a setter method, attr will change the HTML markup.

## Example using .attr() method

We add a click event to the anchors that will locate the appropriate article, hide all others and make the located one visible. 
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Handlebars Praxis</title>
    <meta charset="utf-8" />
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/2.2.4/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/handlebars.js/4.0.5/handlebars.js"></script> 
   
  </head>
  <body>
    <ul>
      <li><a href="#" data-block="gold">Gold Sponsors</a></li>
      <li><a href="#" data-block="silver">Silver Sponsors</a></li>
      <li><a href="#" data-block="bronze">Bronze Sponsors</a></li>
    </ul>
    
    <article data-block="gold">
      <h1>Gold Sponsors</h1>
    </article>
    
    <article data-block="silver">
      <h1>Silver Sponsors</h1>
    </article>
    
    <article data-block="bronze">
      <h1>Bronze Sponsors</h1>
    </article>
    
    <script>
      $('a').on('click', function(e) {
        /*
        Hide all articles
        show the article with value of data-block that matches event target
        If first one is chosen, then this is what we want to filter for:
        $('[data-block=gold]')
        - To get 'gold'
        $('this').attr('data-block')
        - To make it all fit
        $('[data-block=$('this').attr('data-block')]')
        
*/
        e.preventDefault()
        $('article').hide().filter('[data-block=' + $(this).attr('data-block') + ']').show();
      })
    </script>
  </body>
</html>
```
#hide #show #show_chosen_content #filter #click #navigation #data-block #attributes
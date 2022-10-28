# create custom event and add functionality to it

Below we have a method that dispatches a `bolded` event when the user clicks on the section.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title></title>
    <meta name="description" content="">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <style>
      .highlight {
        display: inline;
        background-color:#FFFF00;
      }
    </style>
  </head>
  <body>
        <section>Hello World</section>
        <p>Click on 'Hello World'</p>
    <script src="play2.js" async defer></script>
  </body>
</html>
```
You'll notice that we've added the highlight functionality directly to the 
custom event rather than to the event listener
```javascript
function makeBold(element) {
    element.style.fontWeight = 'bold';
    const myEvent = new CustomEvent('bolded', {
        detail: {
            highlight: function (elem) {
                elem.classList.add('highlight');
            }
        },
    });
    sectionElement.dispatchEvent(myEvent);
};

sectionElement.addEventListener('bolded', function (e) {
    e.detail.highlight(this);
});


sectionElement.addEventListener('click', () => {
  makeBold(sectionElement);
})
```
If we didn't want to add it to the event, we would code it this way
```javascript
function makeBold(element) {
  element.style.fontWeight = 'bold';
  const event = new CustomEvent('bolded');

  element.dispatchEvent(event);
}

sectionElement.addEventListener('bolded', (event) => {
  event.target.classList.add('highlight');
});
```
#custom-event #new-event #highlight #dispatch-event #bold

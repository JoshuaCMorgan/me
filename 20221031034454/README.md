# Event Tracker: track events that occur on web page

We can track events on a web page by wrapping a callback function in a function that adds each event to a tracker object before invoking the callback. 

Our function takes a callback function as an argument and return a new function that:

- Records the event, if the specific event hasn't been recorded before.
Executes the original callback function.
 
here is some markup
```html
<html>
  <head>
    <title>Tests</title>
    <meta charset="utf-8">
    <style>
      #red, #blue, #green, #orange {
        cursor: pointer;
        color: white;
        padding: 10px;
        margin: 10px;
      }
    
      #red {
        width: 400px;
        height: 400px;
        background: red;
      }

      #blue {
        width: 200px;
        height: 200px;
        background: blue;
      }

      #orange {
        width: 100px;
        height: 100px;
        background: orange;
      }

      #green {
        width: 50px;
        height: 50px;
        background: green;
      }
    </style>
  </head>
  <body>
    <div id="red">Red
      <div id="blue">Blue</div>
      <div id="orange">Orange
        <div id="green">Green</div>
      </div>
    </div>
    <script src="test.js"></script>
  </body>
</html>
```

here is our js code
- First, we define `tracker` object that has a private events array and several methods. 
  - The `list` method makes the latter part of the scenario possible. It prevents you from directly manipulating the array of events.

- Another aspect worth looking at is the `track` function. 
  - It takes a callback function as an argument and returns a function that, when executed, invokes the callback. 
  - What's noteworthy here is the private function, `isEventTracked`. 
  - The function determines whether an event is tracked already. If it isn't tracked, it tracks it.
```
const divRed = document.querySelector('#red');
const divBlue = document.querySelector('#blue');
const divOrange = document.querySelector('#orange');
const divGreen = document.querySelector('#green');

const tracker = (() => {
  const events = [];
  return {
    list() {
      return events.slice();
    },
    elements() {
      return this.list().map(({target}) => target);
    },
    add(event) {
      events.push(event);
    },
    clear() {
      events.length = 0;
      return events.length;
    },
  };
})();

function track(callback) {
  function isEventTracked(events, event) {
    return events.includes(event);
  }

  return event => {
    if (!isEventTracked(tracker.list(), event)) {
      tracker.add(event);
    }

    callback(event);
  };
}

divRed.addEventListener('click', track(event => {
  document.body.style.background = 'red';
}));

divBlue.addEventListener('click', track(event => {
  event.stopPropagation();
  document.body.style.background = 'blue';
}));

divOrange.addEventListener('click', track(event => {
  document.body.style.background = 'orange';
}));

divGreen.addEventListener('click', track(event => {
  document.body.style.background = 'green';
}));
```
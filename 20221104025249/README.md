# Cancel HTTP request if request takes too much time.

Here, we can use `timeout` property on the `XMLHttpRequest` object.
We need to set the time to wait in milliseconds. 
Then, add an event listener on the xhr object.

```javascript
function retrieveSchedules() {
  const request = new XMLHttpRequest();

  // Be sure to change your host and port number accordingly
  request.open('GET','http://localhost:3000/api/schedules')
  request.timeout = 5000;
  request.responseType = 'json';

  request.addEventListener('load', event => {
    // do something
  });

  request.addEventListener('timeout', event => {
    alert('It is taking longer than usual, please try again later.')
  });

  request.addEventListener('loadend', event => {
    alert('The request has completed.');
  });

  request.send();
}
```
#timeout #cancel-request #kill-request #stop-request
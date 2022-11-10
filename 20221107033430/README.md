# Resend/update data (form data) if error occurs

You may find that a form submission doesn't meet the prescribe qualifications. 
Maybe a user needs to be in the database but isn't. 

Look at the code below,
we retrieve the form data and make post request.  Let's say it comes back `404`.
KEY IDEA: During the load, we are still within the submit event.  So, we could just fix the form and dispatch it again.
Whatever needs to be done for a proper form submission can get resolved.  
After proper completion, we can update the form data for the form and then dispatch a new submit event to it. 

```javascript
form.addEventListener('submit', (event)  => {
  event.preventDefault();
  const formData = new FormData(form);
  const json = JSON.stringify(formDataToJson(formData));
  
  const xhr = new XMLHttpRequest();

  xhr.open('POST', form.action);
  xhr.setRequestHeader('Content-Type', 'application/json');
  xhr.send(json);

  xhr.addEventListener('load', (event) => {
    let status = xhr.status;
    switch(status) {
        case 204:
            alert('Your schedule has been booked.');
            window.location.href = "/exercise5.html";
            break;
        case 404:
            alert(xhr.responseText); 
      //...omitted
    }
  });
```
Here are the steps
1.  Do any necessary preliminary work 
    1.  let's say its adding a new student
2.  set fixed data on form data
3.  create new Event
4.  dispatch the new event on the form

```javascript
// ...code omitted
case 404:
  // 1. Preliminary work: add new student
  const newStudentForm = document.querySelector('#newStudentForm');
  newStudentForm.addEventListener('submit', (event) => {
    event.preventDefault();

    const formData2 = new FormData(newStudentForm);
    const json2 = JSON.stringify(formDataToJson(formData2));
    
    const xhr2 = new XMLHttpRequest();
    xhr2.open('POST', newStudentForm.action);
    xhr2.setRequestHeader('Content-Type', 'application/json');
    xhr2.send(json2);

  
  xhr2.addEventListener('load', (event) => {
    alert(xhr2.responseText);
    if (xhr2.status === 201) {
      newStudentForm.reset();
      // 2. fix the form data
      formData.set('student_email', formData.get('email'));
      // 3. create new event
      let newSubmission = new Event('submit', { cancelable: true })
      // 4. dispatch new event once again on the form
      form.dispatchEvent(newSubmission);
    }
  })
})
```
We could use Promises for this

#new-event #form #dispatch #update-form-data #form-data #update 
#resend
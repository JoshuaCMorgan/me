# Use IIFE's to return a function/object with access to private data


We can use an IIFE so that the function (rather than the user) is responsible by itself 
for keeping track of data  generated without exposing the data to being unintentionally reassigned.  
We are creating a more isolated namespace, a scope to the 'identifiers' in order
to prevent collisions between them and unintentional  manipulation from an outsider.

## Functions
Below, `studentId` could be reassigned, jeapardizing its ability to return a unique number. 

```javascript
let studentId = 0;

function generateStudentId() {
  studentId += 1;
  return studentId;
}
```
Now, the data (`studentId`) is private.  Only the returned function has access to it.
```javascript
let generateStudentId = (function() {
  let studentId = 0;

  return function() {
    studentId += 1;
    return studentId;
  };
})();
```

## Objects
Here's an example using objects.  With this the students list is private.  `studentBody` is an object, which has access to private data.  The only way to add, access, (or modify) the students' names is through the object.
```javascript
let studentBody = (function() {
  let students = [];
  function isValid(newStudent) {
    return students.every(function(stock) {
      return newStudent.name !== students.name;
    });
  }

  return {
    logStudents() {
      students.forEach((student) => ;console.log(student.name));
    }
    addStudent(newStudent) {
      if (isValid(newStudent)) { 
        students.push(newStudent) 
      }
    },
  };
})();

studentBody.addStudent({name: 'Joe'})
```

## Example in the wild
To isolate our namespace, we wrap all of our code in an IIFE.
```javascript
(function groceryListManager() {
  class GroceryList {
    constructor(listContainerElement) {
      this.list = document.querySelector(listContainerElement);
    }

    addItem(name, quantity) {
      var listItem = document.createElement("li");
      listItem.append(`${quantity} ${name}`);

      this.list.append(listItem);
    }
  }

  document.addEventListener("DOMContentLoaded", function () {
    let form = document.querySelector("form");
    let myGroceryList = new GroceryList("#grocery-list");
    const getValueOf = (selector) => form.querySelector(selector).value;

    form.addEventListener("submit", function (event) {
      event.preventDefault();

      let name = getValueOf("#name");
      let quantity = getValueOf("#quantity") || "1";

      myGroceryList.addItem(name, quantity);
      form.reset();
    });
  });
})();
```
#private-data #iife #immediately-invoked-function-expression #best-practice
#namespace
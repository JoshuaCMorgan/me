# Coding practice: dispatch table

If I have a set of inputs from which to choose from, I could use a `switch` statement like so:
```javascript
function processUserInput(choice, firstNumber, secondNumber) {
  switch(choice) {
    case '+':
      return firstNumber + secondNumber;
      break; 
    case '-':
      return firstNumber - secondNumber;
      break;
    case '*':
      return firstNumber * secondNumber;
      break;
    case '/':
      return firstNumber / secondNumber;
      break;
  }
}

processUserInput('+', 2, 4) // 6
```

But I could also use a dispatch table. We are using a dispatch table to hold all the possible commands a user can give, and the functions the program should call.

## Why dispatch tables are helpful
The fundamental change we made is transforming the conditionals into a data structure. And data is much easier to manipulate than conditionals. In the future, if we want to add a new command, all we have to do is add it to commandTable. No messing around with case or break statements required.

```javascript
// table of pointers/properties to functions
const Calculate = {
    "+": (firstNumber, secondNumber) => firstNumber + secondNumber,
    "-": (firstNumber, secondNumber) => firstNumber - secondNumber,
    "*": (firstNumber, secondNumber) => firstNumber * secondNumber,
    "/": (firstNumber, secondNumber) => firstNumber / secondNumber,
  };

let form = document.querySelector("form");
const getValueOf = (selector) => form.querySelector(selector).value;

form.addEventListener("submit", (event) => {
  event.preventDefault();

  // get-set input from user
  let firstNumber = +getValueOf("#first-number");
  let secondNumber = +getValueOf("#second-number");
  let operator = getValueOf("#operator");

  // retrieve the function we want to use
  let calculate = Calculate[operator];
  let answer = calculate(firstNumber, secondNumber);
  document.querySelector("#result").textContent = String(answer);
});
```

#dispatch-table #best-practice #javascript #switch #case #data-structure
[dispatch table wiki](https://en.wikipedia.org/wiki/Dispatch_table)
[adripof](http://adripofjavascript.com/blog/drips/using-dispatch-tables-to-avoid-conditionals-in-javascript.html)
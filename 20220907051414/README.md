# Coerce JavaScript Numbers using unary + operator
The unary + operator converts its operand to a number.

```javascript
x + ""  // => String(x)
+x      // => Number(x)
x-0     // => Number(x)
!!x    // => Boolean(x): Note double !


let form = document.querySelector("form");
const getValueOf = (selector) => form.querySelector(selector).value;

// we retrieve the value that the element holds, which is a string.
// then use unary + operator in the return string to convert it to a number.
let firstNumber = +getValueOf("#first-number");
```
#unary-operator #coercion #numbers
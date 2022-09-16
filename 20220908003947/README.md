# Use IIFE for creating private scope

IIFE's help us with naming conflicts. Here, `myPet` is in the global scope.
But there could be a variable with the same name.
```javascript
// thousands of lines of messy JavaScript code!
let myPet = {
  type: 'Dog',
  name: 'Spot',
};

console.log(`I have pet ${myPet.type} named ${myPet.name}`);
// more messy JavaScript code
```

We could isolate the object inside a function since they create their own scope.  But we still have the problem of naming conflict.

We can turn the function declaration and invocation into an IIFE. It has a private scope for `myPet`, and it won't clash with any other functions.
```javascript
(function(type, name) {
  let myPet = {
    type,
    name,
  };

  console.log(`I have pet ${myPet.type} named ${myPet.name}`);
})('Dog', 'Spot');
```


#best-practice #immediately-invoked-function-expression #private-scope
#javascript 
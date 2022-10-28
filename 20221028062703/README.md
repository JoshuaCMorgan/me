# create and insert new options for select element drop-down list

You may have a blank `select` element drop-down list and  want to populate it
with some new options. Or you have options that you want to swap out.

Below, we have some classification groups and animals.  We want to 
update the options on one dropdown when the selection in the other dropdown changes. For instance, when the user chooses an option under Classifications, the items in the Animals dropdown should change accordingly. 

```html
<body>
    <form id="selection-filters" method="post" action="#">
      <select id="animal-classifications">
        <option value="Classifications" selected>Classifications</option>
        <option value="Vertebrate">Vertebrate</option>
        <option value="Warm-blooded">Warm-blooded</option>
        <option value="Cold-blooded">Cold-blooded</option>
        <option value="Mammal">Mammal</option>
        <option value="Bird">Bird</option>
      </select>
      <select id="animals">
        <option value="Animals" selected>Animals</option>
        <option value="Bear">Bear</option>
        <option value="Turtle">Turtle</option>
        <option value="Whale">Whale</option>
        <option value="Salmon">Salmon</option>
        <option value="Ostrich">Ostrich</option>    
      </select>
      <button id="clear">Clear</button> 
    </form>
    <script src="play2.js"></script>
  </body>
```
What we can do is clear the options each time, and then fill the drop-down
list with new options.

Here are the linked options.  If someone chooses 'Vertebrate', then 
the animal drop-down list will show the corresponding animals.
```javascript
const linkedOptions = {
  classifications: {
    Vertebrate: ["Bear", "Turtle", "Whale", "Salmon", "Ostrich"],
    "Warm-blooded": ["Bear", "Whale", "Ostrich"],
    "Cold-blooded": ["Salmon", "Turtle"],
    Mammal: ["Bear", "Whale"],
    Bird: ["Ostrich"],
    Classifications: [
      "Animals",
      "Bear",
      "Turtle",
      "Whale",
      "Salmon",
      "Ostrich",
    ],
  },
  animals: {
    Bear: ["Vertebrate", "Warm-blooded", "Mammal"],
    Turtle: ["Vertebrate", "Cold-blooded"],
    Whale: ["Vertebrate", "Warm-blooded", "Mammal"],
    Salmon: ["Vertebrate", "Cold-blooded"],
    Ostrich: ["Vertebrate", "Warm-blooded", "Bird"],
    Animals: [
      "Classifications",
      "Vertebrate",
      "Warm-blooded",
      "Cold-blooded",
      "Mammal",
      "Bird",
    ],
  },
};
```

We first access the elements and get setup.
When a user clicks on an option, the `option` element has a `value` property
which gives us the appropriate value, such as 'Bear' or 'Warm-blooded'.
```javascript
const animalClassifications = document.querySelector("#animal-classifications");
const animals = document.querySelector("#animals");
const clearFiltersBtn = document.querySelector("#clear");
let animalClassificationsValue;
let animalsValue
```
We are going to use that value as key property access to get the array value.
Each `select` DOM element object has a `options` property, which is an array
of each `option` element in its drop-down list.
Here, we are capturing the value, such as `Bear`.
Then, we are grabbing the appropriate array of values (`["Vertebrate", "Warm-blooded", "Mammal"]`) .
Then, we are sending the element and the array to a function for processing.
```javascript
animalClassifications.addEventListener("change", (event) => {
  animalClassificationsValue =
    animalClassifications.options[animalClassifications.selectedIndex].value;
  setOptions(
    animals,
    linkedOptions["classifications"][animalClassificationsValue]
  );
});
```

What we want to do is clear that array list, and repopulate it with new options. 

In the code below, we first access to `options` property of the element
and clear the list of options by setting its length to 0.
Then, we will take our array of values and  iterate through them and their index.
Upon each iteration, we will create a new option 
and using the current index, we will set current index position of 
the `options` element to the current new option we created.

 ```javascript
function setOptions({ options }, filters) {
  options.length = 0;
  filters.forEach((value, index) => {
    options[index] = new Option(value);
  });
}
 ```

 Here, it is all-together, with the addition of the clear option
 and minus the linkedOptions
 ```javascript
const animalClassifications = document.querySelector("#animal-classifications");
const animals = document.querySelector("#animals");
const clearFiltersBtn = document.querySelector("#clear");
let animalClassificationsValue;
let animalsValue;

function setOptions({ options }, filters) {
  options.length = 0;
  filters.forEach((value, index) => {
    options[index] = new Option(value);
  });
}

function setDefault(event) {
  event.preventDefault();
  setOptions(animalClassifications, [
    "Classifications",
    "Vertebrate",
    "Warm-blooded",
    "Cold-blooded",
    "Mammal",
    "Bird",
  ]);
  setOptions(animals, [
    "Animals",
    "Bear",
    "Turtle",
    "Whale",
    "Salmon",
    "Ostrich",
  ]);
}

animalClassifications.addEventListener("change", (event) => {
  animalClassificationsValue =
    animalClassifications.options[animalClassifications.selectedIndex].value;
  setOptions(
    animals,
    linkedOptions["classifications"][animalClassificationsValue]
  );
});

animals.addEventListener("change", (event) => {
  animalsValue = animals.options[animals.selectedIndex].value;
  setOptions(animalClassifications, linkedOptions["animals"][animalsValue]);
});

clearFiltersBtn.addEventListener("click", setDefault);
 ```
 #new-option #select #remove-option #clear-option #clear

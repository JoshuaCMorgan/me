# remove select element drop-down list of option elements

You may have a drop-down list of options for a `<select>` element. 
If you want to clear / remove all or short a list of options, you can use
the `options` property on the `select` element
```html
<select id="animal-classifications">
  <option value="Classifications" selected>Classifications</option>
  <option value="Vertebrate">Vertebrate</option>
  <option value="Warm-blooded">Warm-blooded</option>
  <option value="Cold-blooded">Cold-blooded</option>
  <option value="Mammal">Mammal</option>
  <option value="Bird">Bird</option>
</select>
```
Here, we retrieve the `select` element.
If we access the value of the `options` property, we see this it is an array.
We just set the array to length 0 and we've removed all options
And if we check, we will see the `select` element is empty
```javascript
const animalClassifications = document.querySelector("#animal-classifications");
console.log(animalClassifications.options);
// HTMLOptionsCollection(6) [option, option, option, option, option, option, selectedIndex: 0]

animalClassifications.options.length = 0;
console.log(animalClassifications)
//  <select id="animal-classifications"> </select>
```
#select #remove-options #clear-options #remove #clear

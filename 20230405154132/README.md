# create new array that is a range of numbers

`Array.from()` can take an iterable or array-like object.  if given number, it will return empty array of given size. It takes second argument `mapFn` is the map function to call on every element of the array. 
Here, we map each index to the index value, giving us an array of its index values.
```javascript
function getRange(num) {
  return Array.from(new Array(num), (_, i) => i)
}

getRange(4) // [0, 1, 2, 3]
```

#array #range
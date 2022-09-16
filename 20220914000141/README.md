# Examples and Description of Algorithm Big-O Notation

```javascript
const smArr = [5, 3, 2, 35, 2];

const bigArr = [5, 3, 2, 35, 2, 5, 3, 2, 35, 2, 5, 3, 2, 35, 2, 5, 3, 2, 35, 2, 5, 3, 2, 35, 2, 5, 3, 2, 35, 2, 5, 3, 2, 35, 2, 5, 3, 2, 35, 2, 5, 3, 2, 35, 2, 5, 3, 2, 35, 2];
```

## O(1)

- This is the ideal, no matter how many items there are, whether one or one million, the amount of time to complete will remain the same. 
- Most operations that perform a single operation are O(1). They will all take the same amount of time regardless of the array length.
  - Pushing to an array, 
  - getting an item at a particular index, 
  - adding a child element, 
  - a function that multiplies a set number by some value passed inetc, 

```javascript
const a1 = performance.now();
smArr.push(27);
const a2 = performance.now();
console.log(`Time: ${a2 - a1}`); // Less than 1 Millisecond


const b1 = performance.now();
bigArr.push(27);
const b2 = performance.now();
console.log(`Time: ${b2 - b1}`); // Less than 1 Millisecond
```

## O(n)

By default, all loops are an example of linear growth because there is a 
one-to-one relationship between the data size and time to completion. So an 
array with 1,000 times more items will take exactly 1,000 times longer.

```javascript
const a1 = performance.now();
smArr.forEach(item => console.log(item));
const a2 = performance.now();
console.log(`Time: ${a2 - a1}`); // 3 Milliseconds

const b1 = performance.now();
bigArr.forEach(item => console.log(item));
const b2 = performance.now();
console.log(`Time: ${b2 - b1}`); // 13 Milliseconds
```

## O(n^2)
Exponential growth is a trap we’ve all fall into at least once. Need to find a 
matching pair for each item in an array? Putting a loop inside a loop is great 
way of turning an array of 1,000 items into a million operation search that’ll 
freeze your browser. It’s always better to have to do 2,000 operations over two 
separate loops than a million with two nested loops.

```javascript
const a1 = performance.now();
smArr.forEach(() => {
    arr2.forEach(item => console.log(item));
});
const a2 = performance.now();
console.log(`Time: ${a2 - a1}`); // 8 Milliseconds


const b1 = performance.now();
bigArr.forEach(() => {
    arr2.forEach(item => console.log(item));
});
const b2 = performance.now();
console.log(`Time: ${b2 - b1}`); // 307 Milliseconds
```

## O(log n)
- it searches in progressively more specific sections without looking at most of the data.
- imagine looking up a word like ‘notation’ in a dictionary. You can’t search one entry after the other, instead you find the ‘N’ section, then maybe the ‘OPQ’ page, then search down the list alphabetically until you find a match.
  
Here, we do a quicksort
```javascript
const sort = arr => {
  if (arr.length < 2) return arr;

  let pivot = arr[0];
  let left = [];
  let right = [];

  for (let i = 1, total = arr.length; i < total; i++) {
    if (arr[i] < pivot) left.push(arr[i]);
    else right.push(arr[i]);
  };
  return [
    ...sort(left),
    pivot,
    ...sort(right)
  ];
};

sort(smArr); // 0 Milliseconds
sort(bigArr); // 1 Millisecond
```

Here's a function that expresses it fundamentally.
- every time we double the length of the input array, the number of operations increases linearly (by 1 each time).
```javascript
function logTime(arr) {
  let numberOfLoops = 0
  for (let i = 1; i < arr.length; i *= 2) {
    numberOfLoops++
  }
  return numberOfLoops
}
let loopsA = logTime([1]) // 0 loops
let loopsB = logTime([1, 2]) // 1 loop
let loopsC = logTime([1, 2, 3, 4]) // 2 loops
let loopsD = logTime([1, 2, 3, 4, 5, 6, 7, 8]) // 3 loops
let loopsE = logTime(Array(16)) // 4 loops
```
A binary tree gives a good example:
i split my search area in 1/2 and look only in appropriate areas
           1             
        /     \          
     2            9      
    / \          / \     
  3     4     10     11  
 / \   / \   /  \   /  \ 
5   6 7   8 12  13 14  15

#algorithms #big-o-notation #time-complexity
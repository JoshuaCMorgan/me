# jQuery objects are not 'live'

jQuery objects of selected elements do not update in the progression of code execution.  
So, if you select all paragraph elements on the page, the number of elements in that 
object will not change if another paragraph element is created and added to the page. The set of elements contained within a jQuery object will not change unless explicitly modified.

```js
// Selecting all <p> elements on the page.
let allParagraphs = $( "p" );

// Updating the selection. 
allParagraphs = $( "p" );
```
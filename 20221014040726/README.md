# a function that converts the DOM, starting from the body, to nested arrays. 

 Each element in the DOM is represented as ["PARENT_TAG_NAME", [children]] where children are elements as well and as such follow the same format.

 ```html
<!doctype html>
<html>
  <head>
    <title>Nodes to Array</title>
  </head>
  <body>
    <div id="1">
      <div id="4"></div>
      <div id="5">
        <div id="6"></div>
      </div>
    </div>
    <div id="2"></div>
    <div id="3">
      <div id="7"></div>
      <div id="8"></div>
      <div id="9"></div>
    </div>
  </body>
</html>
 ```

 ```javascript
 function nodeToArr(node) {
    let array = [node.tagName, []];

    for (let idx = 0; idx < node.children.length; idx += 1) {
      let result = nodeToArr(node.children[idx]);
      array[1].push(result);
    }

    return array;
  }

  console.log(JSON.stringify(nodeToArr(document.body)));
 ```

 ```javascript
 function nodesToArr(node = document.body) {
  const childElements = [...node.children].map(nodesToArr);

  return [
    node.tagName,
    childElements,
  ];
}

console.log(JSON.stringify(nodeToArr(document.body)));
 ```
 #convert-nodes-to-array #convert-nodes #recursion #JSONstringify

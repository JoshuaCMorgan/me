# Swap the positions of the elements/nodes
 You may need to swap nodes at some point. 

```html
<!doctype html>
<html>
  <head>
    <title>Node Swap</title>
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
// Solution 1: Using clones, replaceChild and replaceWith
function nodeSwap(id1, id2) {
  function isInvalidSwap(node1, node2) {
    return ((!node1 || !node2) ||
        node1.contains(node2) || node2.contains(node1));
  }

  // extract the relevant nodes
  const node1 = document.getElementById(id1);
  const node2 = document.getElementById(id2);

  // return if either node is not found in the DOM, or both nodes don't share the same parent
  if (!isInvalidSwap(node1, node2)) {
    / both nodes(node1, node2) will have the same parent, pick either node to extract the parent node and store it 
  const parent = node1.parentNode;

  // deep cloning of both nodes to keep track of all of their child and grandchild nodes
  const clone1 = node1.cloneNode(true);
  const clone2 = node2.cloneNode(true);

  // replaced existing nodes with new clone nodes => any event handlers will be lost
  parent.replaceChild(clone1, node2);
  parent.replaceChild(clone2, node1);

  // replace clones in the DOM with the original nodes to keep reference to the event handlers
  clone1.replaceWith(node1);
  clone2.replaceWith(node2);

  return true;
  }
}


// Solution 2: using replaceWith
function nodeSwap(id1, id2) {
  function isInvalidSwap(node1, node2) {
    return ((!node1 || !node2) ||
        node1.contains(node2) || node2.contains(node1));
  }
  // extract the relevant nodes
  const node1 = document.getElementById(id1);
  const node2 = document.getElementById(id2);

  // return If either node is not found in the DOM, or both nodes don't share the same parent
  if (!isInvalidSwap(node1, node2)) {
    // Temp node to keep track of positions
    const tempNode = document.createElement('div');

    // `node1` still points to the original node extracted on line 2 of this function. However, on the DOM it got replaced with `tempNode`
    node1.replaceWith(tempNode);
    node2.replaceWith(node1);
    tempNode.replaceWith(node2);
    return true;
  }
}
 // at least one of the id attributes doesn't exist
  nodeSwap(1, 20);// undefined

  // at least one of the nodes is a "child" of the other
  nodeSwap(1, 4); //undefined
  nodeSwap(9, 3); //undefined

  // // one swap
  nodeSwap(1, 2);

  // // multiple swaps
  nodeSwap(3, 1);
  nodeSwap(7, 9);
```
#node-swap #replacewith #replacechild #swap #replace #clone

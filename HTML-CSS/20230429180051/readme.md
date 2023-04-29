# Flexbox Navigation bar

This works ok. The problem is that 'contact us' gets cut off. And it doesn't even show on mobile devices.
The navbar is the flex container. The direct child elements of a flex container automatically becomes flexible (flex) items.

Since we have two flex items, and our goal is to have each be set to opposite ends, then we need to justify the content of the flex box with `space-between`.

```css
nav {
  display: flex;
  justify-content: space-between;
  background-color: #6e072d;
  color: white;
}
```

Unordered lists are block elements with some padding and margin. So we need to reset these.

```css
ul {
  display: flex;
  padding: 0;
  margin: 0;
}
```

To give each `li` element some space we can set the padding. We can also take away the dot.
The unique feature here is the white border on internal tags. For that, we can use pseudo selectors.

```css
li {
  list-style-type: none;
  padding: 1em 1.5em;
  cursor: pointer;
}
li:not(:last-of-type) {
  border-right: 2px solid white;
}

li:hover {
  background-color: #b90e4d;
}
```

#flexbox #navbar #pseudo-selectors #unordered-lists #lists #dot #cursor #list-style #pointer

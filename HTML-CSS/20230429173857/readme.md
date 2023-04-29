# Nav bar handling UL defaults

By default, it seems `ul`s get a font-size of 16. And this affects spacing between elements when display is changed to `inline-block`. The result is that if `li` elements have a border, then there will be a gap between them. Therefore you'll need to do a reset.
Say, we want 4 elements that are equally apportioned across the screen. We will need to change a couple properties. The font-size and `padding-left`. We need these set to 0, since we have each `li` have a width of `25%`.

Setting `ul` font-size to `0` causes trouble for `li` elements, since they are now collapsed. So, setting their size is important. Here we've set each `li` element font-size to `1.25rem`

Because we have each element set to width of `25%`, which measures content area by default, we have a problem with the 1px borders. So, we need to change the `box-sizing` property to `border-box` to allow width to include the border. And the padding that we add to the `a` tag.

We have to give the `a` tags some line height since they will only consume enough space for the font. We set it to `2.5` times the root.

```css
nav ul {
  background-color: powderblue;
  list-style-type: none;
  padding-left: 0;
  font-size: 0;
  width: 100%;
}

nav li {
  display: inline-block;
  color: blue;
  font-size: 1.25rem;
  text-align: center;
  width: 25%;
  box-sizing: border-box;
  border: 1px solid red;
}

nav a {
  box-sizing: border-box;
  color: blue;
  display: inline-block;
  line-height: 2.5;
  padding: 0 20px;
  text-decoration: none;
  width: 100%;
}
```

#navbar #box-sizing #ul #li #font-size

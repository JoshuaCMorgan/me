# Hosting external library files locally

n projects that use external libraries, it's common to organise the directory structure so that the files for those libraries are kept in a separate directory within your javascripts directory, perhaps something like this (jQuery here as an example):

Copy Code

```html
├── index.html
├── img
├── css
├── js
│   ├── app.js
│   └── vendor
│       └── jquery.js
```

#external library 
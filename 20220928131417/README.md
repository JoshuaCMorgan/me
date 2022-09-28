#Using jQuery, Retrieve select option from dropdown when there is a change

You might have a collection of dropdown select options that you created with  the elements `select` and `option`, like below.
Here we have a form with a set of selections for [make, model, price, year];
These selections are interdependent.  How can we reflect the appropriate changes based upon a single change?
```html
<header>
      <h1>Buy Used Cars</h1>
      <form action="#" method="get" class="filters" id="filters">
      </form>
    </header>

    <main id="used-cars">
    </main>

    <script type="text/x-handlebars-template" id="filter-controls">
      <fieldset>
        <label>
          Make
          <select name="make-filter" id="filter-make-by">
            {{> makeOptions}}
          </select>
        </label>

        <label>
          Model
          <select name="model-filter" id="filter-model-by">
            {{> modelOptions}}
          </select>
        </label>

        <label>
          Price
          <select name="price-filter" id="filter-price-by">
            {{> priceOptions}}
          </select>
        </label>

        <label>
          Year
          <select name="year-filter" id="filter-year-by">
            {{> yearOptions}}
          </select>
        </label>

        <input type="reset" name="reset" id="reset" value="Reset" />
      </fieldset>
    </script>
```

We can use jQuery in this way.
We can attach an event handler function for a 'change' event to each 
`select` element that is a descendent of the `#filter` element.
```javascript
// $objects.on(event, select, handler)
$("#filters").on('change', 'select', updateFilters())
```

# dropdown-menu # select # change
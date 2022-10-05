# Forms and validation
[link](https://html.spec.whatwg.org/multipage/form-control-infrastructure.html#form-submission-attributes)
Attributes for form submission can be specified both on form elements and on submit buttons 

The attributes for form submission that may be specified on form elements are action, enctype, method, novalidate, and target.

The corresponding attributes for form submission that may be specified on submit buttons are formaction, formenctype, formmethod, formnovalidate, and formtarget. 

The novalidate and formnovalidate content attributes are boolean attributes. If present, they indicate that the form is not to be validated during submission.
Example

The no-validate state of an element is true if the element is a submit button and the element's formnovalidate attribute is present, or if the element's form owner's novalidate attribute is present, and false otherwise.

```html
<form action="#" method="post" novalidate>
```

`valid = element.checkValidity()`
Returns true if the element's value has no validity problems; false otherwise. Fires an invalid event at the element in the latter case.
The `checkValidity()` method, when invoked, must run the check validity steps on this element.
The check validity steps for an element element are:
  - If element is a candidate for constraint validation and does not satisfy its constraints, then:
    - Fire an event named invalid at element, with the cancelable attribute initialized to true (though canceling has no effect).
    -Return false.
  - Return true.

Example of its use:
  - We get the form element, check if constraint exists
```javascript
handleFormSubmit: function () {
  // retrieve the form element, the access form element inside jQuery object
  // checkValidy is found in [[Prototype]]: HTMLFormElement
    if ($('form')[0].checkValidity()) {
      $('.form_errors').text('');
    } else {
      $('.form_errors').text('Form cannot be submitted until errors are corrected.');
      this.validateFormInputs();
      return false;
    }
  },
```

## satisfaction of constraints
[validity states](https://html.spec.whatwg.org/multipage/form-control-infrastructure.html#validity-states)
An element can be constrained in various ways. The following is the list of validity states that a form control can be in, making the control invalid for the purposes of constraint validation.
- if an element doesn't satisfy of any validity state suffers
- validity states (see link for me examples)
  - value missing
    - When a control has no value but has a `required` attribute
  - pattern mismatch
    - When a control has a value that doesn't satisfy the `pattern` attribute
#check-validity #forms #form-error #pattern-attribute #required-attribute


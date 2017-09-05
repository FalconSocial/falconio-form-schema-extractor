[![Published on webcomponents.org](https://img.shields.io/badge/webcomponents.org-published-blue.svg)](https://www.webcomponents.org/element/FalconSocial/falconio-form-schema-extractor)

Polymer 1 element for extracting data out of forms. Part of Falcon.io - Build Elements bundle.

<!-- START-HIDDEN-SECTION: Add imports and styling here. -->
<script src="../webcomponentsjs/webcomponents-lite.js"></script>
<link rel="import" href="falconio-form-schema-extractor.html">
<!-- END-HIDDEN-SECTION: Add the visible part of the demo below. -->
```html
    <form id="myForm">
        <input type="text" required name="fullname" placeholder="Full Name">
        <input type="email" name="email" placeholder="Email">
        <input type="number" name="age" placeholder="Age">
        <input type="checkbox" name="choice">Choice
    </form>
    <build-form-schema-extractor
        form="myForm"
        schema="{{ schema }}"
    ></build-form-schema-extractor>
```

`<build-form-schema-extractor>` attempts to extract a [json schema](http://json-schema.org/) from a [html form](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form) using built-in or provided rules to transform the form fields into json schema properties. It will continously update the scheme according to the fields that is currently in the provided form.
Example:
```html
    <form id="myForm">
        <input type="text" required name="fullname" placeholder="Full Name">
        <input type="email" name="email" placeholder="Email">
        <input type="number" name="age" placeholder="Age">
        <input type="checkbox" name="choice">Choice
    </form>
    <build-form-schema-extractor
        form="myForm"
        schema="{{ schema }}"
    ></build-form-schema-extractor>
```

Which would extract in this json scheme
```json
    {
        "type": "object",
        "properties": {
            "fullname": {
                "title": "Full Name",
                "type": "string"
            },
            "email": {
                "title": "Email",
                "type": "string",
                "format": "email"
            },
            "age": {
                "title": "Age",
                "type": "number"
            },
            "choice": {
                "title": "Choice",
                "type": "boolean"
            }
        },
        "required": ["fullname"]
    }
```
### The following form field attributes gets transformed by default

field name | function | schema name
-----------|----------|-------------
`id` | Can be used for internal reference | `id`
`minlength` | Specifies the minimum number of characters | `minLength`
`maxlength` | Specifies the maximum number of characters | `maxLength`
`min` | Specifies the minimum value | `minimum`
`max` | Specifies the maximum value | `maximum`
`required` | Specifies that an input field is required (must be filled out) | becomes part of `required` array
`placeholder` | title for field | `title`
`label` | title for field if placeholder is not specified | `title`

## Running demos and tests in browser




## Running tests from the command line

When in the `falconio-form-schema-extractor` directory, run `polymer test`



## License

MIT License
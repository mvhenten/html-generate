# html-element
Generate HTML from a plain object definition

Simple helper functions to generate html from javascript objects as configuration hashes.

I was rendering a complex html widget involving some logic that was too much to handle in a
template. Looking trough npmjs.org came up nada, so I wrote this.

These functions are intended as low-level workhorses, so I've tried to keep the code as fast
as possible by using simple for loops and little functions.

### install

    npm install html-helper

### Example:

```javascript
    var HTML = require('html-helper');

    var html = HTML.element({
        tagName: 'p',
        text: 'Lorem ipsum sit amet...',
        attributes: {
            foo: '"bar"'
        },
        children: [{
            text: 'consectetur adipisicing elit'
        }]
    });

    // <p foo="&quot;bar&quot;">Lorem ipsum sit amet...
    //   <div>consectetur adipisicing elit</div>
    // </p>
```

## Methods

#### element

Low level interface, takes an object of the following form:

* tagName - The name of the tag for this html element
* text - Text content. Will be entity encoded.
* html - HTML content. Will not be entitiy encoded.
* attributes - An object of key-value attribute pairs. values will be entity encoded.
* children - An array of objects defining children for this html element

E.g. the following:

```javascript
    element({
        tagName: 'ul',
        atributes: {
            class: 'nav'
        },
        children: [
            {
                tagName: 'li',
                text: 'Do you want to go '
                attributes: {
                    class: 'active'
                },
                html: '<a href="/">home?</a>'
            }
        ]
    });
```

produces:

```html
    <ul>
        <li class="active">Do you want to go <a href="/">home?</a></li>
    </ul>
```

#### tag

Alternative interface, provides a little coating around `element`:

```javascript
    tag('p', 'You can read all about it ', {
        html: tag('a', 'here', { href: '/about' })
    });

    // <p>You can read all about it <a href="/about">here</a></p>
```



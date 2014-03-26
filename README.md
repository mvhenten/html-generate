# html-element
Generate HTML from a plain object definition

Simple helper functions to generate html from javascript objects as configuration hashes.

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

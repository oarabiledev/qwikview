![roseview Banner](docs/roseview.png)

# roseview

roseview allows developers to control all ui, using javascript and that makes achieving reactivity easier.

Before libraries were a thing, the way forwad on ui was narrow minded, it was all about separation of concerns and that worked for a while, before we realized we could go crazy with the web.

There are many frameworks and we are just one of them, all built for different niche cases, here is a tip :

> **_NOTE:_** For pages that ussually are demo pages, I dont recommend use of any framework.

Now that we have de-mistified the purpose of all frameworks, here is what makes roseview different :

- Can be used without a build step
- We build everything and use only a few external libraries
- It is easier to understand and build complex things with
- Codebase scales atleast in a visiually appealing way.

## Getting Started > 3

Firstly link to the file in your html :

```html
<script src="roseview.core.js"></script>
/** Or */
<script src="roseview.es.js" type="module"></script>
/** Or */
<script src="https://www.unpkg.com/roseview" type="module"></script>
```

Now the next focus is your main file, you can call it : `app.js` or `main.js` :

```javascript
/**
 * We use the concept of layouts, these are special divs - you
 * pass in parameters and  those specify the direction and
 * flow of  elements in them.
 */

import { html, htmlPage } from "roseview";

// let main = html.CreateLayout(type, options);

/**
 * The type is which type of special div you want, ther
 * is the linear div ( content flows in columnar form )
 * and we have absolute ( the polar opposite of linear)
 * lastly we have the frame, which will allow us to
 * place stuff over each other.
 */

let main = html.CreateLayout("linear", "top, vertical, scrolly");

/**
 * For options these specify de=irection and how the main view
 * behaves, we have the following options :
 * center, left, right
 * top, bottom,
 * scrolly, scrollx
 * noscrollbar,
 * fillx, filly, fillxy
 */

// htmlPage.Build(mainContainer, appRoutes)
// Now add the layout to the body.
htmlPage.Build(main);
```

You have a simple roseview app now, to add elements like buttons and Images, they are all methods in the html Object.

> Refer To The Elements.md Page For more Info

### Basic Elements >3

Here is a display of basic htmlelements in use :

```javascript
let main = html.CreateLayout("linear", "center");

let button = html.Button(main, "Hello World");

/**
 * All method function to the html Object has their parameter as
 * the parent :
 * This adds them to that layout, you can use
 * addChild as an alternative
 * (for adding layouts on other layouts)
 *
 * Then have the main param of that element, for an image
 * it will be an array of urls to that image
 *
 * Then finally the props, use gerenal DOM setters in here
 * as an object.
 */

htmlPage.Build(main);
```

Check This Page :

- [Elements Documentation](docs/Elements.md)

## The Approach To Reactivity

roseview uses signals, showIF for the reactivity patern.

```javascript
import { createSignal } from "roseview";

const onThemeChange = function (val) {
 if (getTheme() == "light") {
  // change all elements to light mode
 } else {
  // change all elements to dark mode
 }
};

let [getTheme, setTheme, onThemeChange] = createSignal("light");

// Access the values via getThene and setTheme
```

## showIF

You can import showIF function which allows you to hide or show certain elements in a page.

```javascript

import { showIF } from 'roseview'

showIF(truthy_or_falsy_val, elementA, elementB);
```

Check This Page:

- [Reactivity Docs](docs/Reactivity.md)

That is the barebones needed to get started with the framework.
Thank You For Your Interest ❣️

For the next step I suggest you check :

- [Methods Documentation](docs/Methods.md)

- [Elements Documentation](docs/Elements.md)

- [Reactivity Docs](docs/Reactivity.md)

- [Animation Docs](docs/Animation.md)

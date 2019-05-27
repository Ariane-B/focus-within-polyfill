# `:focus-within` Pseudo-Class Polyfill

[![npm version](https://badge.fury.io/js/focus-within-polyfill.svg)](https://badge.fury.io/js/focus-within-polyfill) [![Build Status](https://travis-ci.org/matteobad/focus-within-polyfill.svg?branch=master)](https://travis-ci.org/matteobad/focus-within-polyfill/) ![David](https://img.shields.io/david/dev/matteobad/focus-within-polyfill.svg) ![David](https://img.shields.io/david/matteobad/focus-within-polyfill.svg) [![Greenkeeper badge](https://badges.greenkeeper.io/matteobad/focus-within-polyfill.svg)](https://greenkeeper.io/)
[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release) ![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-blue.svg) [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

* [How to use](#hot-to-use)
* [How it works](#how-it-works)
* [Features](#features)
* [Browser support](#browser-support)
* [Demo](https://matteobad.github.io/focus-within-polyfill)

The `:focus-within` CSS pseudo-class represents an element that has received focus or contains an element that has received focus. In other words, it represents an element that is itself matched by the :focus pseudo-class or has a descendant that is matched by `:focus`. (This includes descendants in shadow trees.)

This selector is useful, to take a common example, for highlighting an entire `<form>` container when the user focuses on one of its `<input>` fields.

More information on [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus-within).

## How to use

This package is available both as production ready script and as a package. The script can be downloaded [here](https://unpkg.com/focus-within-polyfill/dist/focus-within-polyfill.js), or installed with a package manager.

```sh
# npm
npm install focus-within-polyfill --save

# yarn
yarn add focus-within-polyfill
```

When including the polyfill in a script tag, call `window.focusWithin.polyfill(string)` method to initialize the polyfill:

```javascript
/* ES5 */
<script src='https://unpkg.com/focus-within-polyfill/dist/focus-within-polyfill.js'></script>

focusWithin.polyfill()
```

In addition this library is available as a es6 module that can be imported and bundled up with any build tool. If you are importing it as a dependency, make sure to call the polyfill method:

```javascript
/* ES6 */
import focusWithin from 'focus-within-polyfill'

focusWithin.polyfill()
```

After import and initialization the polyfill will kick in **only** if `:focus-within` is not supported in the current browser. By default the `[focus-within]` attribute will be added automatically to every element that should have the pseudo-class. Additionally in the initialization fase a **custom class** or **custom attribute** can be specified like in the example below:

```javascript
focusWithin.polyfill('[focus-within]'); // default
focusWithin.polyfill('[focus-inside]'); // custom attribute
focusWithin.polyfill('.focus-within'); // custom class
```

## How it works

This package will add two event listeners, one on the *focus* event and one on the *blur* event to trigger the automatic apply and remove of a custom attribute to indicate wheter the Element should have a `:focus-within` pseudo-class. In order to do so and be compatible with older version of IE and EDGE the `getAttribute`, `setAttribute` and `removeAttribute` methods are used to set both attributes and classes. Then `requestAnimationFrame` is used to apply the modification to the DOM.

This polyfill is compatible with native [Shadow DOM](https://developers.google.com/web/fundamentals/web-components/shadowdom#what) and with the [webcomponents polyfill](https://www.webcomponents.org/polyfills/). This means that even on IE11 and EDGE you will be able to use the `:focus-within` pseudo-class to style elements even outside a shadowRoot.

## Features

* _Custom attribute/class_ value to apply the polyfill
* _Shady CSS/DOM_ support even with the [webcomponents polyfill](https://www.webcomponents.org/polyfills/)
* _Non standard Element_ support, like SVG Element with link inside

## Browser Support

| Polyfill        | Edge | IE9+ | Chrome | Firefox | Safari |
| --------------- |:----:|:----:|:------:|:-------:|:------:|
| `:focus-within` | ✓    | ✓    | ✓      | ✓       | ✓      |

\* This polyfill maybe work on older versions of the browsers.

## 📺 Demos

The [demos](https://github.com/matteobad/focus-within-polyfill/tree/master/demos) folder contains 10+ demos that uses this polyfill.

| Type      | Title                                               | Code                                | Live demo                                                                           |
| --------- | --------------------------------------------------- | ------------------------------------|------------------------------------------------------------------------------------ |
| Content   | :focus-within for `<button>, <input>` elements      | [Code](demos/buttons.html)          | [Live](https://matteobad.github.io/focus-within-polyfill/demos/buttons.html)        |
| Content   | :focus-within for `<div contenteditable>` elements  | [Code](demos/editable-text.html)    | [Live](https://matteobad.github.io/focus-within-polyfill/demos/editable-text.html)  |
| Content   | :focus-within for `<div tabindex>` elements         | [Code](demos/focusable-divs.html)   | [Live](https://matteobad.github.io/focus-within-polyfill/demos/focusable-divs.html) |
| Content   | :focus-within for `<select>` elements               | [Code](demos/select.html)           | [Live](https://matteobad.github.io/focus-within-polyfill/demos/select.html)         |
| Content   | :focus-within for `<others>` elements               | [Code](demos/others.html)           | [Live](https://matteobad.github.io/focus-within-polyfill/demos/others.html)         |

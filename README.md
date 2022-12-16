## Vue 3 Line Clamp

[![npm version](https://img.shields.io/npm/v/vue3-line-clamp.svg)](https://www.npmjs.org/package/vue3-line-clamp)
[![npm downloads](https://img.shields.io/npm/dm/vue3-line-clamp.svg)](http://npm-stat.com/charts.html?package=vue3-line-clamp)

This a vue 3 port of the original [vue 2 line clamp](https://github.com/Frondor/vue-line-clamp)

A simple, fast and lightweight directive for truncating multi line texts using "cross-browser" CSS strategies.

### Install

```bash
npm install --save vue3-line-clamp
```

```javascript
import { createApp } from 'vue';
import lineClamp from 'vue3-line-clamp'

const app = createApp({});
app.use(lineClamp, {
  // plugin options
})
```

### Usage

```html
<p v-line-clamp:20="2">Some long text that needs to be truncated to a fixed number, which is 2 in this case. And if the browser doesn't support `-webkit-line-clamp`, then a line-height of 20px is going to be used in order to truncate this text, thus calculating its max-height.</p>
```
**NOTE:** the argument passed to the directive must be a number, and its used as the `line-height` value for non-webkit browsers, as part of the fallback method.
In some upcoming version it may be able to detect this value automatically.

### Plugin options

| property  | type  | default  | description |
| --- | --- | --- | --- |
| importCss  | Boolean | false  | Set to `true` in order to import styles into `<head>` automatically, element.style is used by default
| textOverflow  | String | `ellipsis`  | Set the value for [`text-overflow`](https://developer.mozilla.org/en-US/docs/Web/CSS/text-overflow) property in modern browsers
| fallbackFunc  | Function | defaultFallbackFunc  | Provide your own default method to handle the truncation strategy on unsupported browsers. Accepts all directive params: `element (Node)`, `bindings (Object)`, `lines (Number)`


### Caveats

1. Probably there may be problems when loading custom fonts. I've done some tests and couldn't detect any inconsistence so far, so feel free to open an issue and provide code to reproduce any bug or glitch you find.
2. The fallback method for older browsers won't show up the ellipsis (`...`) since we can't control the part of the text node that may get "clamped".

### Changelog

**v1.0.0** - Latest version of `vue-line-clamp` (1.2.4) ported to vue 3

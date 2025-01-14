# postcss-color-gray

[![CSS Standard Status](https://jonathantneal.github.io/css-db/badge/css-color-grays.svg)](https://jonathantneal.github.io/css-db/#css-color-grays)
[![Build Status](https://travis-ci.org/postcss/postcss-color-gray.svg?branch=master)](https://travis-ci.org/postcss/postcss-color-gray)
[![Coverage Status](https://img.shields.io/coveralls/postcss/postcss-color-gray.svg)](https://coveralls.io/r/postcss/postcss-color-gray)

[PostCSS](https://github.com/postcss/postcss) plugin to transform [gray()](http://dev.w3.org/csswg/css-color/#grays) function to today's CSS

```css
.foo {
  color: gray(0);
}

.bar {
  color: gray(255, 50%);
}

.baz {
  color: gray;
}
```

↓

```css
.foo {
  color: rgb(0, 0, 0);
}

.bar {
  color: rgba(255, 255, 255, 0.5);
}

.baz {
  color: gray;
}
```

## Installation

[![NPM version](https://badge.fury.io/js/postcss-color-gray.svg)](https://www.npmjs.org/package/postcss-color-gray)

[Use npm](https://www.npmjs.org/doc/cli/npm-install.html).

```
npm install postcss-color-gray
```

## API

```javascript
var postcssColorGray = require('postcss-color-gray');
```

### postcssColorGray()

Return: `Function`

It converts `gray(A)` to `rgb(A,A,A)`, and converts `gray(A,B)` to `rgba(A,A,A,B)`.

```javascript
var postcss = require('postcss');
var colorGray = require('postcss-color-gray');

postcss()
  .use(colorGray())
  .process('a {color: gray(85); background-color: gray(10%, .25)}')
  .css;
//=> 'a {color: rgb(85, 85, 85); background-color: rgba(26, 26, 26, 0.25)}'
```

*Note that [gray() may have a keyword argument to specify a color via "luminance"](http://dev.w3.org/csswg/css-color/#issue-658bb235). Current version of postcss-color-gray doesn't support this feature.*

## License

[ISC License](./LICENSE) © 2017 Shinnosuke Watanabe

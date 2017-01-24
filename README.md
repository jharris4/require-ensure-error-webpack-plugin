# require-ensure-error-webpack-plugin

This plugin adds support for an error handling callback to require.ensure in Webpack 2.2+

**This plugin requires Webpack Version 2.2+**

For Webpack 1.x support, see the [require-error-handler-webpack-plugin](https://github.com/richardscarrott/require-error-handler-webpack-plugin/blob/master/src/BundleLoader.js)

## Installation

``` shell
npm install require-ensure-error-webpack-plugin --save-dev
```

## Usage

```javascript
var RequireEnsureErrorHandlerPlugin = require('require-ensure-error-webpack-plugin');

{
	plugins: [
		new RequireEnsureErrorHandlerPlugin()
	]
}
```

```javascript
require.ensure(['./a'], function() {
	var a = require('./a');
    console.log('success require ensure 1', a);
}, function() {
    console.log('error require ensure 1');
}, 'chunkName1');

require.ensure(['./b'], function() {
	var b = require('./b');
    console.log('success require ensure 2', b);
}, function() {
    console.log('error require ensure 2');
});

require.ensure(['./c'], function() {
	var c = require('./c');
    console.log('success require ensure 3', c);
}, 'chunkName3');

require.ensure(['./d'], function() {
	var d = require('./d');
    console.log('success require ensure 4', d);
});
```

## Usage with loaders

The [bundle-loader](https://github.com/webpack/bundle-loader) is **not** compatible with error callbacks,
so you can use the [split-chunk-loader](https://github.com/jharris4/split-chunk-loader) instead.
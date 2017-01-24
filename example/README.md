# Example

The example generates 4 code split bundles with the varying permutations of require.ensure parameters.

- 1 require.ensure([], onSuccess, onError, chunkName)
- 2 require.ensure([], onSuccess, onError)
- 3 require.ensure([], onSuccess, chunkName)
- 4 require.ensure([], onSuccess)

## Getting started

``` shell
git clone https://github.com/jharris4/require-ensure-error-webpack-plugin.git
npm install
npm run example
```

Open index.html in your browser and you should see output like this in the browser console:

```
success require ensure 1 a
success require ensure 2 b
success require ensure 3 c
success require ensure 4 d
```

(The order may be different since these operations are asynchronous)

Now delete all split chunk files (all -output.js files **except** main-output.js)

Refresh index.html in your browser, and you should see the following in the browser console:

```
error require ensure 1
error require ensure 2
// ... a bunch of uncaught errors related to the 3rd and 4th require.ensure calls without error handlers
```
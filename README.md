# purescript-webstorage
[![Build Status](https://travis-ci.org/joneshf/purescript-webstorage.svg?branch=master)](https://travis-ci.org/joneshf/purescript-webstorage)

## Documentation

Module documentation is [published on Pursuit](http://pursuit.purescript.org/packages/purescript-webstorage).

## Running tests

This package only supports browsers.
This means that `pulp test` will complain.
To allow tests to run with `pulp test` try the following:

1.  Run the following to add a mocking library (other libraries are available) to npm devDependencies (or equivalent).

```
> npm install --save-dev mock-local-storage
```

2.  Add the following line into `test/Main.purs`

```purescript
foreign import mockStorage :: forall eff . Eff eff Unit
```

3.  Add a file `test/Main.js` with the following contents (or combine the following with an existing `test/Main.js`)
    
```javascript
"use strict"

global.window = {};
const localStorage = require('mock-local-storage');
window.localStorage = global.localStorage;

exports.mockStorage = function() {
    return window;  
}
```

## Releases

New versions are published when CI succeeds on a tag.
To cut a new version:

1. Ensure the version in [package.json](./package.json) has been updated.
1. Draft a [new release](https://github.com/joneshf/purescript-webstorage/releases/new).
1. Name the tag with a `v` prefix and the version to release.

    <img src="https://user-images.githubusercontent.com/1356417/38399010-87bb9364-38fc-11e8-8c9b-d793b7bc43c9.png" />
1. Choose a specific commit rather than a branch.

    <img src="https://user-images.githubusercontent.com/1356417/38398813-29fe09a6-38fb-11e8-8531-df121f6d221c.png" />
1. Publish the release.

    <img src="https://user-images.githubusercontent.com/1356417/38398905-df501f1a-38fb-11e8-9fbf-ff41f016ebe9.png" />
1. CI will run. Assuming everything builds properly, it will [deploy the new version to Pursuit](https://travis-ci.org/joneshf/purescript-webstorage/builds/363372429#L640).
1. Verify the version was released on [Pursuit](https://pursuit.purescript.org/packages/purescript-webstorage).

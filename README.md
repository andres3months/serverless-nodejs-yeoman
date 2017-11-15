# serverless-nodejs-yeoman

## Install

During development, make the generator available as a global module:

```
git clone https://github.com/SteveHoggNZ/serverless-nodejs-yeoman.git && \
  cd generator-serverless-nodejs && \
  npm link
```

Post development:

Publish as an NPM module and install it globally

## Usage

```
mkdir new-project && \
  cd $_ && \
  yo serverless-nodejs
```

## Notes

### Bootstrapped Using

```
npm install -g generator-generator &&
  mkdir generator-serverless-nodejs &&
  cd $_ &&
  yo generator
```

### Code Coverage

https://github.com/zinserjan/mocha-webpack/issues/19

### babel-polyfill

* For production builds babel-polyfill is required in hander.js
* Mocha includes babel-polyfill for each of the tests i.e. the files can be tested independently of handler.js
* The if around babel-polyfill in handler.js allows Mocha to test it without double requiring the polyfill

### Atom Plugins

* Show non-standard problems as you type
  * linter
  * linter-ui-default
  * linter-js-standard-engine
    * Note: standard needs to be installed in devDependencies in package.json for this to work
* Automatically format using ctrl-alt-f
  * prettier-standard-formatter
    * Note: this installs an old version of the prettier-standard-formatter. See workaround below:

prettier-standard-formatter workaround:

The old version of prettier-standard-formatter bundled with this Atom plugin strips brackets from && || statements. This causes the following warning:

`Unexpected mix of '&&' and '||'`

This fixes the problem:

```
cd ~/.atom/packages/prettier-standard-formatter
yarn add prettier-standard-formatter
```

TODO: a pull request for this fix

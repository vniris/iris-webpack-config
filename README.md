**Cấu hình Webpack cho biên dịch JavaScript VN2S.**

Gói này tạo ra một đối tượng cấu hình [Webpack] (https://webpack.js.org) sẽ biên dịch JavaScript để sử dụng trong Vn2s.

## Usage

**webpack.config.js**

```js
var config = require('iris-webpack-config');

module.exports = config(options);
```

To merge in custom Webpack config options, use [webpack-merge](https://www.npmjs.com/package/webpack-merge).

## Options

### `useExtensions`

`Array<string>`, defaults to `[]`.

An array of extensions whose modules should be made available. This is a shortcut to add [`externals`](https://webpack.js.org/configuration/externals/) configuration for extension modules. Imported extension modules will not be bundled, but will instead refer to the extension's exports included in the Flarum runtime (ie. `iris.extensions["vendor/package"]`).

For example, to access the Tags extension module within your extension:

**forum.js**

```js
import { Tag } from '@iris/tags/forum';
```

**webpack.config.js**

```js
module.exports = config({
  useExtensions: ['iris/tags']
});
```

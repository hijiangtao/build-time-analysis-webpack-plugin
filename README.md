# build-time-analysis-webpack-plugin
A webpack plugin that output the build time file by file as a JSON format with filters

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/c913db53b5a3470f840f5329ea2f54d4)](https://www.codacy.com/app/hijiangtao/build-time-analysis-webpack-plugin?utm_source=github.com&utm_medium=referral&utm_content=hijiangtao/build-time-analysis-webpack-plugin&utm_campaign=badger)
[![npm](https://img.shields.io/npm/v/build-time-analysis-webpack-plugin.svg)](https://www.npmjs.com/package/build-time-analysis-webpack-plugin)
[![Github All Releases](https://img.shields.io/github/downloads/hijiangtao/build-time-analysis-webpack-plugin/total.svg)](https://github.com/hijiangtao/build-time-analysis-webpack-plugin/releases)
[![npm](https://img.shields.io/npm/dt/build-time-analysis-webpack-plugin.svg)](https://www.npmjs.com/package/build-time-analysis-webpack-plugin)
[![GitHub contributors](https://img.shields.io/github/contributors/hijiangtao/build-time-analysis-webpack-plugin.svg)]() 
[![GitHub issues](https://img.shields.io/github/issues/hijiangtao/build-time-analysis-webpack-plugin.svg)](https://github.com/hijiangtao/build-time-analysis-webpack-plugin/issues) 
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/hijiangtao/build-time-analysis-webpack-plugin/pulls) 
[![license](https://img.shields.io/github/license/hijiangtao/build-time-analysis-webpack-plugin.svg)](https://github.com/hijiangtao/build-time-analysis-webpack-plugin/blob/master/LICENSE) 

[![NPM](https://nodei.co/npm/build-time-analysis-webpack-plugin.png)](https://nodei.co/npm/build-time-analysis-webpack-plugin/)

## How to write a webpack plugin (Chinese)

* Blog <https://hijiangtao.github.io/2019/12/01/Introduction-of-webpack-plugin/>
* Zhihu <https://zhuanlan.zhihu.com/p/94577244>

## USAGE

Install the plugin via `npm` or `yarn`:

```shell
npm install --save-dev build-time-analysis-webpack-plugin

// or 
yarn add build-time-analysis-webpack-plugin --dev
```

Then require it in your `webpack.config.js`:

```javascript
const ModuleBuildTimeCalWebpackPlugin = require('build-time-analysis-webpack-plugin');

module.exports = {
  plugins: [
    new ModuleBuildTimeCalWebpackPlugin({
     filename: 'modules.json',
     includeNodeModules: false,
     callback: () => {},
   }),
  ]
};
```

Then you can pack your codes via commands such as `npm run build`, plugin's result will be output to `modules.json` file by default (however, you can customize it via `options` that passed to plugin constructor). The output JSON format is something like this:

```json
{
  'src/index.js': {
    name: 'src/index.js',
    start: 1,
    end: 4,
    time: 3,
    loaders: [ ... ]
  },
  ...
}
```

## API

### filename [String, optional]

A string with file extension, The filename that you want plugin output the result to, default to `modules.json`.

### includeNodeModules [Boolean, optional]

Whether to include the build time result of files inside `node_modules`, default to `false`.

### callback [Function, optional] 

The callback handler you want plugin called after resolve all process (correspondind lifecycle should be `compilation.hooks.finishModules`), default to `() => {}`.

## CONTACT

@hijiangtao

## LICENSE

MIT

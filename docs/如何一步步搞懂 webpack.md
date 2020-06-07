# 如何一步步搞懂 webpack

平时做项目的时候大多数同学都是使用脚手架去搭建项目，很少有同学真正的去了解 `webpack` 内部的配置，而且也很少会修改到 `webpack` 配置里面的东西，基本上都是开箱即用。但是这反而限制了去追求知识的真相，作为一个有理想的 `FE` 怎么可能止步于此呢，那么下面就一步步来搞懂 `webpack` 的相关配置以及概念。

## 核心概念

虽然说在 `webpack 4.0.0` 开始不必去定义一个配置文件，内部已经集成了默认的配置，但是这也不会影响去学习 ``webpack` 的配置。

**四个核心的概念**

1. 入口（`entry`)
2. 输出（`output`）
3. 模块转换器（`loader`）
4. 插件（`plugin`）

### 1. 入口（entry）

入口（`entry`）可以分为 **单入口** 和 **多入口**

配置如下：

- 单入口

可以有字符串写法和对象的写法

字符串的写法

```js
const config = {
  entry: './src/home/index.js'
};

module.exports = config;
```

对象写法

```js
const config = {
  entry: {
    index: './src/home/index.js'
  }
};

module.exports = config;
```

- 多入口

```js
const config = {
  entry: {
    home: './src/home/index.js',
    bill: './src/bill/index.js',
    my: './src/my/index.js'
  }
};

module.exports = config;
```

### 2. 输出（output）

可以配置 `webpack` 如何输出打包后的文件资源。**即使可以存在多个入口起点，但只指定一个输出配置。**

- 基本配置

```js
const config = {
  output: {
    filename: 'bundle.js',
    path: '/dist'
  }
};

module.exports = config;
```

`filename`: 输出文件的名称

`path`: 输出文件所在的路径

- 多个入口输出路径的配置

```js
const config = {
  entry: {
    home: './src/home/index.js',
    bill: './src/bill/index.js',
    my: './src/my/index.js'
  },
  output: {
    filename: '[name].js',
    path: '/dist'
  }
}

module.exports = config;
```

使用占位符 `[name]` 来确保每个文件具有唯一的名称

未完待续...

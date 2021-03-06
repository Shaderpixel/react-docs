# 新手入门

## JSFiddle

开始学习 React 的最简单的方法是用下面 JSFiddle 的 Hello World：

 * **[React JSFiddle](https://jsfiddle.net/reactjs/69z2wepo/)**
 * [React JSFiddle without JSX](https://jsfiddle.net/reactjs/5vjqabv3/)

## 通过 npm 使用 React

我们建议在 React 中使用 CommonJS 模块系统，比如 [browserify](http://browserify.org/) 或 [webpack](https://webpack.github.io/)。使用 [`react`](https://www.npmjs.com/package/react) 和 [`react-dom`](https://www.npmjs.com/package/react-dom) npm 包。

```javascript
// main.js
var React = require('react');
var ReactDOM = require('react-dom');

ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('example')
);
```

要用 browserify 安装 React DOM 和构建你的包。

```sh
$ npm install --save react react-dom babelify babel-preset-react
$ browserify -t [ babelify --presets [ react ] ] main.js -o bundle.js
```

要用 webpack 安装 React DOM 和构建你的包：  

```sh
$ npm install --save react react-dom babel-preset-react
$ webpack
```

> 注意:
>
> 如果你正在使用 ES2015，你将要使用 `babel-preset-es2015` 包。


## 不用 npm 的快速开始

如果你现在还没准备要使用 npm，你可以下载这个已经包含了预构建的 React 和 React DOM 拷贝的入门套件。 

<div class="buttons-unit downloads">
  <a href="/react/downloads/react-0.14.7.zip" class="button">
    下载入门套件 0.14.7
  </a>
</div>

在入门教程包的根目录，创建一个含有如下代码的 `helloworld.html`。

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Hello React!</title>
    <script src="build/react.js"></script>
    <script src="build/react-dom.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.23/browser.min.js"></script>
  </head>
  <body>
    <div id="example"></div>
    <script type="text/babel">
      ReactDOM.render(
        <h1>Hello, world!</h1>,
        document.getElementById('example')
      );
    </script>
  </body>
</html>
```

在 JavaScript 代码里写着 XML 格式的代码称为 JSX；可以去 [JSX 语法](02.1-jsx-in-depth.md)里学习更多 JSX 相关的知识。为了把 JSX 转成标准的 JavaScript，我们用 `<script type="text/babel">` 标签，并引入 Babel 来完成在浏览器里的代码转换。

### 分离文件

你的 React JSX 代码文件可以写在另外的文件里。新建下面的 `src/helloworld.js`。

```javascript
ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('example')
);
```

然后在 `helloworld.html` 引用该文件：

```html
<script type="text/babel" src="src/helloworld.js"></script>
```

注意一些浏览器（比如 Chrome）会在使用 HTTP 以外的协议加载文件时失败。

### 离线转换

先安装 [Babel](http://babeljs.io/) 命令行工具（需要 [npm](https://www.npmjs.com/)）：

```sh
npm install --global babel-cli
npm install babel-preset-react
```

然后把你的 `src/helloworld.js` 文件转成标准的 JavaScript：

```sh
babel --presets react src --watch --out-dir build
```

> 注意:
>
> 如果你正在使用 ES2015, 你将需要使用 `babel-preset-es2015` 包。

`build/helloworld.js` 会在你对文件进行修改时自动生成。阅读 [Babel CLI 文档](http://babeljs.io/docs/usage/cli/) 了解高级用法。

```javascript
ReactDOM.render(
  React.createElement('h1', null, 'Hello, world!'),
  document.getElementById('example')
);
```

对照下面更新你的 HTML 代码

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Hello React!</title>
    <script src="build/react.js"></script>
    <script src="build/react-dom.js"></script>
    <!-- 不需要 Babel! -->
  </head>
  <body>
    <div id="example"></div>
    <script src="build/helloworld.js"></script>
  </body>
</html>
```

## 下一步

去看看[入门教程](tutorial.md)和入门教程包 `examples` 目录下的其它例子学习更多。

我们还有一个社区开发者共建的 Wiki：[workflows, UI-components, routing, data management 等](https://github.com/facebook/react/wiki/Complementary-Tools)

恭喜你，欢迎来到 React 的世界。

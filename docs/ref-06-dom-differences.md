# DOM 的不同之处

React 实现了一个浏览器无关的事件和 DOM 系统，原因是为了性能和跨浏览器的兼容性。我们利用这个机会来清理了一些浏览器 DOM 实现的一些粗糙边缘。

* 所有的 DOM properties 和 attributes (包括事件处理器) 都应该 camelCased 来保持和标准的 JavaScript 风格一致。我们在这里故意打破了这个规范是因为规范是不一致的。 **然而**，`data-*` 和 `aria-*` attributes [conform to the specs](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes#data-*) 应该只 lower-cased。
* `style` attribute 接受 camelCased properties 的 JavaScript 对象而不是一个 CSS 字符串。这保持了和 DOM `style` JavaScript property 的一致,更有效率，而且阻止了 XSS 安全漏洞.
* 因为 `class` 和 `for` 是 JavaScript 的保留字，内建 [DOM nodes](http://javascript.info/tutorial/dom-nodes) 的 JSX 元素应该分别使用 attribute 名 `className` 和 `htmlFor` ，（比如 `<div className="foo" />`）。自定义元素应该直接使用 `class` 和 `for` （例如。 `<my-tag class="foo" />` ）。
* 所有事件对象遵循 W3C 规范，所有事件（包括提交）正确按 W3C 规范冒泡。详见 [Event System](ref-05-events.md)。
* `onChange` 事件表现的像你期望的那样：不论何时一个表单域改变了这个事件就会激发，而不是模糊的不一致.我们故意打破了已有浏览器的行为，因为 `onChange` 对于他的行为来说用词不当，并且 React 依赖于这个事件来实时响应用户的输入。详见 [Forms](07-forms.md)。
* 表单输入attributes 类似 `value` 和 `checked`，就像 `textarea` 一样 [More here](07-forms.md)。

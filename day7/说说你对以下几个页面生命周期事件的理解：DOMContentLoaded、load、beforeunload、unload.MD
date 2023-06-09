# 说说你对页面生命周期事件的理解
DOMContentLoaded：

当HTML文档被完全加载和解析后，DOMContentLoaded 事件会被触发。这意味着 DOM 树已经构建完成，但是可能仍有外部资源（如图像、样式表或脚本）尚未加载完成。通常在此事件中，可以执行一些初始化 DOM 操作或与 DOM 相关的代码。

load：

当所有页面资源（包括图像、样式表、脚本等）都加载并渲染完毕后，load 事件会被触发。这个事件通常用于在页面加载完成后执行一些额外的 JavaScript 代码或其他操作。

beforeunload：

当用户正在关闭页面或切换到另一个页面时，beforeunload 事件会被触发。可以使用此事件来提示用户保存尚未保存的更改或执行其他清理操作。

unload：

在用户离开当前页面并且页面将被卸载时，unload 事件会被触发。可以在此事件中执行一些清理操作，例如取消未完成的请求或释放内存等。请注意，这个事件不适用于所有情况，因为它可能会被某些浏览器阻止。
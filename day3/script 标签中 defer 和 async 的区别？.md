# script 标签中 defer 和 async 的区别

在 HTML 中，`<script>` 标签有两个属性可以用来指定脚本的异步加载方式：defer 和 async。

* defer 属性用于延迟脚本的执行，使它在文档完全解析和显示之后再执行。在使用 defer 属性时，浏览器会并行下载多个脚本，但是脚本的执行将按照它们在 HTML 文档中出现的顺序进行。因此，如果一个脚本文件在另一个文件之前被引入，那么即使它在 HTML 中出现的位置在后面，它仍然会先于其它脚本执行。

* async 属性用于异步加载脚本。当浏览器遇到带有 async 属性的脚本标签时，它会立即开始下载脚本文件，并且不会等待该脚本的下载和执行完成，而是继续解析页面并显示内容。因此，如果多个异步脚本在相同位置出现，它们的执行顺序不确定，具体哪个脚本首先执行取决于每个脚本的下载速度和执行时间。

总的来说， defer 属性适合用于需要保持脚本的执行顺序的情况，而 async 属性则适合用于不依赖执行顺序并能够并行运行的脚本。

**回答：**

defer 和 async 是用于控制 script 标签加载执行行为的两个属性，它们有以下几点区别：

1. 加载顺序：
    * defer：被设置为 defer 的脚本将按照在页面中出现的先后顺序依次加载，但是脚本的执行要等到 DOM 树解析完成之后、文档加载事件 DOMContentLoaded 事件触发之前才会开始。

    * async：被设置为 async 的脚本将不考虑其在文档中的位置和其他资源的加载，在下载完毕后立即执行。因此如果多个 async 脚本互相依赖则无法确保执行顺序。

2. 执行时机：
    * defer：被设置为 defer 的脚本在文档加载事件 DOMContentLoaded 事件之前执行，因此可以通过其操作 DOM 元素。

    * async：被设置为 async 的脚本会在下载完成后立即执行，不会等到文档加载事件 DOMContentLoaded，如果脚本需要操作 DOM 元素，则可能会出现未定义的结果。

总之，defer 是延迟执行脚本，等到页面完成解析后才执行，更适合使用在需要修改 DOM 的脚本上；而 async 是异步执行脚本，适合不依赖其他脚本或者不需要修改 DOM 的脚本上。
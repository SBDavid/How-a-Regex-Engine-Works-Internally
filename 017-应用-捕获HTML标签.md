## 1. 正则表达式应用实例

下面一系列文章中我会介绍许多正则表达式的使用模式和应用实例，它们在实际工作中非常有用。每一个例子中所使用的正则特性都已经在之前的文章中介绍过。如果你想查看这些特性的具体介绍，你可以点击文章中的链接。

对于正则的初学者而言，学习这些应用实例可以让你知道正则表达式能胜任什么样的工作。正则表达式的功能非常强大。虽然学习正则表达式略有难度，但是正则表达式可以高效的完成字符搜索，节约大量开发时间。

## 2. 提取HTML标签
`<TAG\b[^>]*>(.*?)</TAG>`可以匹配一对HTML标签，标签内的内容会保存到第1个[回溯引用](https://github.com/SBDavid/How-a-Regex-Engine-Works-Internally/blob/master/014-%E5%9B%9E%E6%BA%AF%E5%BC%95%E7%94%A8.md)。表达式中的`?`是的`*`成为一个[惰性匹配](https://github.com/SBDavid/How-a-Regex-Engine-Works-Internally/blob/master/012-%E9%87%8F%E8%AF%8D.md)，也就是说它会在字符串的首个闭合标签前停止，而不是在最后闭合标签前停止。这个表达式无法匹配嵌套的标签，例如`<TAG>one<TAG>two</TAG>one</TAG>`。

`<([A-Z][A-Z0-9]*)\b[^>]*>(.*?)</\1>`可以匹配任意的一对HTML标签。注意你需要关闭大小写敏感。这个表达式的关键是[回溯引用](https://github.com/SBDavid/How-a-Regex-Engine-Works-Internally/blob/master/014-%E5%9B%9E%E6%BA%AF%E5%BC%95%E7%94%A8.md)`\1`。标签之间的内容会保存在第2个回溯引用中。这个方法同样不能匹配嵌套了相同标签的字符串。

## 修剪空白字符
通过正则匹配和替换，你可以快速的修剪文本中的空白，包括字符串的开头和结尾处的空白字符，以及文件中的空白字符。你可以使用`^[ \t]+`匹配字符串开头的空白字符（空格和制表符）。`[ \t]+$`可以匹配结尾的空白字符。你可以把这两个表达式通过[选择符](https://github.com/SBDavid/How-a-Regex-Engine-Works-Internally/blob/master/010-%E9%80%89%E6%8B%A9%E7%AC%A6.md)组合起来，也就是`^[ \t]+|[ \t]+$`。你可使用[字符集](https://github.com/SBDavid/How-a-Regex-Engine-Works-Internally/blob/master/005-%E5%AD%97%E7%AC%A6%E7%B1%BB.md)取代`[ \t]`，这样就可以任何你想匹配的空白字符，例如`[ \t\r\n]`可以匹配换行符。你也可以使用[字符集的缩写](https://github.com/SBDavid/How-a-Regex-Engine-Works-Internally/blob/master/006-%E5%AD%97%E7%AC%A6%E9%9B%86%E7%BC%A9%E5%86%99.md)，例如`[\s]`。

---

> 如果文章出现错误，请给我提Issues - -
[Github地址](https://github.com/SBDavid/How-a-Regex-Engine-Works-Internally)

[原文](https://www.regular-expressions.info/examples.html)
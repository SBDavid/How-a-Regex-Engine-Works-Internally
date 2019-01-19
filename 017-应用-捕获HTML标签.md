## 1. 正则表达式应用实例

下面一系列文章中我会介绍许多正则表达式的使用模式和应用实例，它们在实际工作中非常有用。每一个例子中所使用的正则特性都已经在之前的文章中介绍过。如果你想查看这些特性的具体介绍，你可以点击文章中的链接。

对于正则的初学者而言，学习这些应用实例可以让你知道正则表达式所能完成的功能。正则表达式的功能非常强大。虽然学习正则表达式略有难度，但是正则表达式可以高效的完成字符搜索，节约大量开发时间。

## 2. 提取HTML标签
`<TAG\b[^>]*>(.*?)</TAG>`可以匹配一对HTML标签，标签内的内容会保存到第1个[回溯引用](https://github.com/SBDavid/How-a-Regex-Engine-Works-Internally/blob/master/014-%E5%9B%9E%E6%BA%AF%E5%BC%95%E7%94%A8.md)。表达式中的`?`是的`*`成为一个[惰性匹配](https://github.com/SBDavid/How-a-Regex-Engine-Works-Internally/blob/master/012-%E9%87%8F%E8%AF%8D.md)，也就是说它会在字符串的首个闭合标签前停止，而不是在最后闭合标签前停止。这个表达式无法匹配嵌套的标签，例如`<TAG>one<TAG>two</TAG>one</TAG>`。

`<([A-Z][A-Z0-9]*)\b[^>]*>(.*?)</\1>`可以匹配任意的一段HTML。注意你需要关闭大小写敏感。这个表达式的关键是[回溯引用](https://github.com/SBDavid/How-a-Regex-Engine-Works-Internally/blob/master/014-%E5%9B%9E%E6%BA%AF%E5%BC%95%E7%94%A8.md)`\1`。标签之间的内容会保存在第2个回溯引用中。这个方法同样不能匹配嵌套了相同标签的字符串。
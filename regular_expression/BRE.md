# BRE正则引擎

基本正则表达式(Basic Regular Expressions)是速度最快的正则引擎标准。由于其功能少，所以效率高。

绝大多数支持``POSIX``标准的程序都实现了``BRE``正则。

Linux中使用``BRE``引擎的程序主要有``grep``和``sed``，注意由于``sed``注重速度，所以只实现了``BRE``的子集。
意味着``BRE``的特性``sed``并不能全部支持。

正则表达式有``元字符``和非元字符组成，意味着写正则的时候只需要注意元字符的含义就行了。
非元字符代表直接匹配字符本身。

例如: ``123456789``就代表匹配``123456789``这个字符串，``ab.*c``代表
匹配``abc``,``ab11c``,``abbc``等一系列模式。

## BRE正则的元字符

BRE的元字符很少，只有``. [] ^ $ * \ \(\) \{\}``这几种，甚至不支持``|``这种选择模式。

 元字符  |                           描述
------- | -----------------------------------------------------------
 ``.``  | 匹配任意**单字符**，如``a``, ``b``, ``1``等等
 ``^``  | 不匹配任何字符，代表锚定**行首**,如``^abc``代表以``abc``开头的模式
 ``$``  | 不匹配任何字符，代表锚定**行尾**,如``abc$``代表以``abc``结尾的模式
 ``[]`` | 代表匹配**括号内任意一个单字符**,如``[abc]``代表匹配a或b或c任意一个
 ``[^pattern]``| 代表取反匹配,**不匹配*pattern*的模式**,如[^abc]代表除abc之外的其他单字符
 ``*``  | 代表匹配**前面一个单字符任意次(包括0次)** ,如``a*b``代表匹配``b,ab,aab``...
 ``\``  | 转义字符，``\\``会匹配``\``这个字符

``\(\)``,``\{\}``将在``ERE``正则中介绍。

> **TIPS**: 正则都是区分大小写的，意味着[a-z]不能匹配到ABCD。有些程序的命令或参数支持忽略大小写匹配,
> 如``grep -i``。但要注意，对于正则表达式本身是大小写敏感的。

>``^``和``$``出现在模式中间的时候，无特殊含义，如``a^b``匹配的就是``a^b``这个字符串。
> 类似的，只有右半个括号时(``)``,``]``,``}``)也无特殊含义，无需转义,如: ``[]abc]``

> ``[]``里面的``pattern``可以配合``-``简写, 如``[a-zA-Z]``, ``[0-9]``。

此外，``POSIX class``也可以在正则表达式中运用，以下是对照表:


 POSIX class | similar to | meaning
------------ | ---------- | ---------
 [:upper:]   |  [A-Z]	  | uppercase letters
 [:lower:]   |	[a-z]     |	lowercase letters
 [:alpha:]	 | [A-Za-z]   |	upper- and lowercase letters
 [:digit:]	 | [0-9]      |	digits
 [:xdigit:]  |	[0-9A-Fa-f] | hexadecimal digits
 [:alnum:]   |	[A-Za-z0-9] | digits, upper- and lowercase letters
 [:punct:]	 |	punctuation | (all graphic characters except letters and digits)
 [:blank:]	 | [ \t]         | space and TAB characters only
 [:space:]	 | [ \t\n\r\f\v] | blank (whitespace) characters
 [:cntrl:]	 |               | control characters
 [:graph:]	 | [^ [:cntrl:]] | graphic characters (all characters which have graphic representation)
 [:print:]	| [[:graph] ]    | graphic characters and space

## BRE正则引擎的运用

```
echo {1..9} | grep '^1.*9$'
echo {a..z}{0..9}{9..1} | grep -o '[[:digit:]][[:digit:]]'  # grep -o仅打印出匹配到的部分
echo "This is a book" | grep 'book$'
```

删除文件中所有的注释(#之后的部分)和空行:
```
grep -v '^\s*#' /etc/services | grep -v '^\s*$' | sed 's/\s*#.*$//'
sed 's/\s*#.*$//; /^\s*$/d' /etc/services
```

## ``\``的妙用
``\``的作用是转义字符，对元字符使用会失去元字符的作用，但对于某些非元字符使用会带来意想不到的妙用。
这里讲解一些边界的匹配问题，后面还会看到更多关于`\`的奇妙的用法。

上面我们可以看到``^``,``$``可以分别锚定行首和行尾，如果要匹配单词的起始和结束呢？

如果要匹配单词的起始(左边界)，可以用``\<``匹配。例如:``\<book``可以匹配``book``,
``bookooooo``,但是不能匹配``abook``。

类似的，如果要匹配单词的结尾(右边界),可以用``\>``匹配。例如: ``do\>``不能匹配到``doing``,
但能匹配到``todo``

左右边界的匹配合起来可以使用``\b``。例如``\bset\b``匹配的就是``set``这个单词，等同于``\<set\>``。

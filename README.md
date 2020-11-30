#简介
This is a reference manual for the Go programming language. For more information and other documents, see golang.org.
这是GO语言参考手册。更多信息及文档，请访问golang.org。

Go is a general-purpose language designed with systems programming in mind. It is strongly typed and garbage-collected and has explicit support for concurrent programming. Programs are constructed from packages, whose properties allow efficient management of dependencies.
Go是一种通用语言，它被设计时将系统编程铭记于心。Go是强类型且有垃圾回收机制，显式支持并发编程。代码以包的形式组织，包的属性允许高效地组织依赖关系。

The grammar is compact and simple to parse, allowing for easy analysis by automatic tools such as integrated development environments.
语法紧凑且易于解析，可通过集成开发环境等自动工具轻松进行分析。

#符号表示法
The syntax is specified using Extended Backus-Naur Form (EBNF):
语法以EBNF来说明：

> Production  = production_name "=" [ Expression ] "." .
Expression  = Alternative { "|" Alternative } .
Alternative = Term { Term } .
Term        = production_name | token [ "…" token ] | Group | Option | Repetition .
Group       = "(" Expression ")" .
Option      = "[" Expression "]" .
Repetition  = "{" Expression "}" .

Productions are expressions constructed from terms and the following operators, in increasing precedence:
Productions是由terms和以下运算符构成的表达式，其优先级递增：
> |   alternation
()  grouping
[]  option (0 or 1 times)
{}  repetition (0 to n times)

Lower-case production names are used to identify lexical tokens. Non-terminals are in CamelCase. Lexical tokens are enclosed in double quotes "" or back quotes \`\`.
小写production名称用于标识词法tokens。非终结符一般用驼峰式命名。 词法token用双引号“”或反引号\`\`括起来。

The form a … b represents the set of characters from a through b as alternatives. The horizontal ellipsis … is also used elsewhere in the spec to informally denote various enumerations or code snippets that are not further specified. The character … (as opposed to the three characters ...) is not a token of the Go language.
a … b这种形式代表的是从a到b可选的字符集合。省略号…在本规范中也用于某些处的表示不完全枚举或是不再详细列出的代码分片。 字符…(不同于三个字符的...)，它不是 Go 语言的一个词法单元/符号。

#源代码表示

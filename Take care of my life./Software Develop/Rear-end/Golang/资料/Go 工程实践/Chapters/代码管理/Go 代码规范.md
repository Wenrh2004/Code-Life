如果团队不能对代码规范中达成一致，很容易在业务迭代时出现风格不统一、用法各式各样的问题，经常在一些语言用法和风格上形成争议。

**代码规范的作用就在于形成研发团队的最大共识**， 这里列举了一些本章节中提到的代码风格问题的正确实践。

## package

package 的命名应该遵循如下原则：

- 只由小写字母组成。不包含大写字母和下划线等字符；
- 简短并包含一定的上下文信息。例如 `time`、`list`、`http` 等；
- 不能是含义模糊的常用名，或者与标准库同名。例如不能使用 `util` 或者`strings`；
- 包名能够作为路径的 base name，在一些必要的时候，需要把不同功能拆分为子包。例如应该使用`encoding/base64`而不是`encoding_base64`或者`encodingbase64`。

**以下规则按照先后顺序尽量满足：**

- 不使用常用变量名作为包名。例如使用`bufio`而不是`buf`；
- 使用单数而不是复数。例如使用`encoding`而不是`encodings`；
- 谨慎地使用缩写。例如使用`fmt`在不破坏上下文的情况下比`format`更加简短，以及一些需要用多个单词表达上下文的命名可以使用缩写，例如使用`strconv`而不是`stringconversion`。

## function

Function 的命名应该遵循如下原则：

- 对于可导出的函数使用`MixedCaps`，对于内部使用的函数使用`mixedCaps`；
    
- 函数名不携带包名的上下文信息。例如使用`http.Server`而不是`http.HTTPServer`，因为包名和函数名总是成对出现的。
    
- 函数名尽量简短：
    
    - 当名为`foo`的包某个函数返回类型`Foo`时，往往可以省略类型信息而不导致歧义。例如使用`time.Now()`以及`time.Parse()`，两者返回的都是`time.Time`类型；
    - 当名为`foo`的包某个函数返回类型`T`时（`T`并不是`Foo`），可以在函数名中加入类型信息。例如使用`time.ParseDuration()`返回的是`time.Duration`类型；
    - 当名为`foo`的包某个函数返回类型`Foo`，且`Foo`是其所有方法的入口时，可以使用`New()`来命名而不导致歧义。例如使用`list.New()`返回的是`*list.List`类型。

## function with struct receiver

Function with struct receiver 的命名应该遵循的原则是：未导出字段的`getter`中不加入`Get`前缀。例如某个名为`Foo`的 struct 含有未导出的字段`bar`，其`setter`为`SetBar`，但其`getter`应该为`Bar`而不是`GetBar`。

## receiver

Receiver 的命名应该遵循如下原则：

- 不要使用面向对象编程中的常用名。例如不要使用`self`、`this`、`me`等；
- 一般使用 1 到 2 个字母的缩写代表其原来的类型。例如类型为`Client`，可以使用`c`、`cl`等；
- 在每个此类型的方法中使用统一的缩写。例如在其中一个方法中使用了`c`代表了`Client`，在其他的方法中也要使用`c`而不能使用诸如`cl`的命名。

## interface

Interface 的命名应该遵循如下原则：

- 对于只有一个方法的 interface，通常将其命名为方法名加上`er`。例如`Reader`和`Writer`。
- interface 的方法不要占用一些惯用名，除非此方法具有同样的作用。例如`Read`、`Write`、`Flush`、`String`、`ServeHTTP`。

## variable

Variable 的命名应该遵循如下原则：

- 对于可导出的变量使用`MixedCaps`，对于内部使用的变量使用`mixedCaps`；
- [缩略词](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fgolang%2Fgo%2Fwiki%2FCodeReviewComments%23initialisms "https://github.com/golang/go/wiki/CodeReviewComments#initialisms")全大写，但当其位于变量开头且不需要导出时，使用全小写。例如使用`ServeHTTP`而不是`ServeHttp`，以及使用`XMLHTTPRequest`或者`xmlHTTPRequest`；
- 简洁胜于冗长。例如在循环中，使用`i`代替`sliceIndex`；
- 变量距离其被使用的地方越远，则需要携带越多的上下文信息。例如全局变量在其名字中需要更多的上下文信息，使得在不同地方可以轻易辨认出其含义。

## 📒 课件

- [**点击此处，查看本节课件**](https://bytedance.feishu.cn/file/boxcnVnGXdo9LA4V1erK4iHHOOg?from=from_copylink "https://bytedance.feishu.cn/file/boxcnVnGXdo9LA4V1erK4iHHOOg?from=from_copylink")

## 📚 推荐资料

Go 官方代码规范相关内容，请点击下面链接了解：

- [_Go Code Review Comments_](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fgolang%2Fgo%2Fwiki%2FCodeReviewComments "https://github.com/golang/go/wiki/CodeReviewComments")
- [_Effective Go_](https://link.juejin.cn/?target=https%3A%2F%2Fgolang.org%2Fdoc%2Feffective_go "https://golang.org/doc/effective_go")
- [_The Go Blog_](https://link.juejin.cn/?target=https%3A%2F%2Fblog.golang.org%2F "https://blog.golang.org/")
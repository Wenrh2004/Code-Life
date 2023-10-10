在课程的第一部分，我们主要介绍 Go 工程和依赖管理基本机制。目前 Go 依赖管理大多采用 go mod，开发者们几乎每天都在使用，但经常会遇到一些令人困惑的问题。这也很正常，因为依赖管理本就是一件很复杂的事情，而大家经常忽略它。因此第一部分着重介绍 go mod 的基本原理和使用方法，帮助大家系统认识 go mod。

Golang 依赖管理机制发展到现在，主要经历了 GOPATH、govendor、go mod三个时期。而 go mod 发展到现在，已经能够较好地解决依赖管理中的问题了。go mod 的核心原理主要包含三部分内容：

- 版本的两种表达方式：semver (Semantic Versioning) 语义化版本、基于某一 commit 的伪版本号；
- 管理 go.mod 的两个重要工具：go get & go mod；
- 版本选择算法：Minimal Version Selection(MVS)。

在实际工程实践中，开发者们在 go.mod 文件中还会经常遇到一些非理想状态：

- **// indirect** 标记：非本项目所直接依赖，但在本项目中指定该依赖项的版本；
- **+incompatible** 标记：该依赖未使用 go mod 管理依赖。

大家需要注意这些依赖项会存在一些特殊的行为。此外，我们还需要掌握一些常用工具和方法。

在依赖分析和处理层面主要有：

- 查询依赖关系和依赖库代码：go mod graph & go mod vendor；
- 修改依赖库：replace；
- 批量更新和安装/运行二进制：go get ...后缀、携带版本后缀的 go run/install。

在工程管理实践经验层面主要有：

- 庞大项目的依赖管理：拆库或 submodule；
- 版本撤回标记：retract；
- 本地工程目录组织：在 $GOPATH 按路径管理。

## 📒 课件

- [**点击此处，查看本节课件**](https://bytedance.feishu.cn/file/boxcn7nDL8wjqgPJcnRy9dwvD1S?from=from_copylink "https://bytedance.feishu.cn/file/boxcn7nDL8wjqgPJcnRy9dwvD1S?from=from_copylink")

## 📚 推荐资料

- [_Go Modules Reference_](https://link.juejin.cn/?target=https%3A%2F%2Fgolang.org%2Fref%2Fmod "https://golang.org/ref/mod")
- [_modget_](https://link.juejin.cn/?target=https%3A%2F%2Fpkg.go.dev%2Fcmd%2Fgo%2Finternal%2Fmodget%40go1.15.11 "https://pkg.go.dev/cmd/go/internal/modget@go1.15.11")
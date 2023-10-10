我们需要在不断的业务迭代中保持代码的规范性和正确性，本章节会讲述 Go 生态中常见的 linters 以及它们的原理。其中，gofmt 和 go vet 是每个 Go SDK 自带的 linter 工具，golangci-lint 是社区基于 Go team 的 [golang/analysis](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fgolang%2Ftools%2Ftree%2Fmaster%2Fgo%2Fanalysis "https://github.com/golang/tools/tree/master/go/analysis") 开发的 linter 工具（go vet 也是基于此开发的）。

- gofmt: [pkg.go.dev/cmd/gofmt](https://link.juejin.cn/?target=https%3A%2F%2Fpkg.go.dev%2Fcmd%2Fgofmt "https://pkg.go.dev/cmd/gofmt")
- go vet: [pkg.go.dev/cmd/vet](https://link.juejin.cn/?target=https%3A%2F%2Fpkg.go.dev%2Fcmd%2Fvet "https://pkg.go.dev/cmd/vet")
- golint(deprecated): [github.com/golang/lint](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fgolang%2Flint "https://github.com/golang/lint")
- golang/analysis: [github.com/golang/tool…](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fgolang%2Ftools%2Ftree%2Fmaster%2Fgo%2Fanalysis "https://github.com/golang/tools/tree/master/go/analysis")
- golangci-lint: [github.com/golangci/go…](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fgolangci%2Fgolangci-lint "https://github.com/golangci/golangci-lint")

## 📒 课件

- [**点击此处，查看本节课件**](https://bytedance.feishu.cn/file/boxcnytZaHj1gN17MGwAu6mLJve?from=from_copylink "https://bytedance.feishu.cn/file/boxcnytZaHj1gN17MGwAu6mLJve?from=from_copylink")
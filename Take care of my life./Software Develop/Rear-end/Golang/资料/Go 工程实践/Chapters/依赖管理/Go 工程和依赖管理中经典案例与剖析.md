这一讲，我们会 case by case 讲解 5 个生产场景中实际发生的案例，总结一些经验教训，避免大家在工程管理中使用错误的工具和方法：

- case 1: 误用 go get 的 -u 参数导致更新了依赖的依赖；
- case 2: 一些项目由于 tag major 版本 >1 的客观原因导致无法使用 go mod，但新项目均应使用 go mod；
- case 3: 部分项目不使用 go mod 导致依赖项引入了错误的版本；
- case 4: 删 tag/branch/commit 引发的血案；
- case 5: 循环依赖陷阱。

## 📒 课件

- [**点击此处，查看本节课件**](https://bytedance.feishu.cn/file/boxcn0iRgK2fA53y4KT7epuYqJh?from=from_copylink "https://bytedance.feishu.cn/file/boxcn0iRgK2fA53y4KT7epuYqJh?from=from_copylink")
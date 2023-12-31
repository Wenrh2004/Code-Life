集成开发环境，英文缩写为 IDE，全部展开的话是 Integrated Development Environment，本文后续将称之为 IDE。

我们都知道，使用普通的文本编辑器也能编译和运行 Go 程序，那么为何还要使用集成开发环境呢？这就要从它的定义说起。

> 集成开发环境是用于提供程序开发环境的应用程序，一般包括代码编辑器、编译器、调试器和图形用户界面等工具。集成了代码编写功能、分析功能、编译功能、调试功能等一体化的开发软件服务套件。所有具备这一特性的软件或者软件套（组）都可以叫集成开发环境。该程序可以独立运行，也可以和其它程序并用。

简而言之，IDE 可以看作是“更高级”的文本编辑器。它增加了代码智能提示、程序运行时调试等等实用功能，能大大提高代码编写和修改的效率。对于 C、C++ 或 C# 语言，通常使用 Visual Studio；对于 Web 开发者，通常使用 WebStorm；对于 iOS App 开发者，通常使用 XCode…… 对于 Go 语言，我们将使用 GoLand。

### GoLand简介

GoLand 是 JetBrains 公司推出的智能 Go IDE，且适用于Windows、Linux、macOS 下运行。

对于 Go 语言而言，GoLand 会在代码编写过程中实时检测错误并给出修改建议，能够智能显示代码提示，帮助我们准确无误地编写代码，并尽可能地在代码编译前就规避掉某些错误。

GoLand 中的代码

调试器可以在程序运行时观察内存中变量的值，帮助我们跟踪代码的运行。在团队开发中，团队成员可以借助 GoLand 内置的版本控制插件完成协同编码。GoLand 还提供了丰富的工具集，可与JavaScript、TypeScript、NodeJS、SQL、数据库、Docker、Kubernetes 和 Terraform 等协同运作。

此外，GoLand 还支持从插件市场中安装插件（目前已有数以千计可选），进一步增强了它的定制和扩展能力。

### GoLand的安装

GoLand 的安装非常简单，只需打开官网的下载地址：[www.jetbrains.com/zh-cn/go/do…](https://link.juejin.cn/?target=https%3A%2F%2Fwww.jetbrains.com%2Fzh-cn%2Fgo%2Fdownload%2F) ，网页将会自动匹配当前操作系统，选取最适合的版本。我们只需点击下载，并像安装其他软件程序一样安装它即可。

> ❗️ 注意： GoLand IDE 依赖 Go SDK，请确保 Go SDK 已经被正确安装，``并配置了相关环境变量。这部分请参考小册第2讲的内容。对于macOS，使用 Apple 芯片的朋友记得选择 Apple Silicon 的 dmg 软件包。`

`
> 💡 提示： 不同版本的 GoLand 可以并存，若要安装旧的 Go Land 版本，访问：[https://www.jetbrains.com/zh-cn/go/download/other.html](https://www.jetbrains.com/zh-cn/go/download/other.html) 可以找到几乎所有版本的下载链接。

### 收费和购买方式

GoLand 本身并不是免费软件。官方提供了 30天 的免费试用期，到期后需要付费购买才能继续使用。值得一提的是，如果你是学生或是教师，或是在学校实验室中部署 GoLand，抑或是用于符合条件的开源项目，是可以申请免费使用的。有关定价的详细说明请点击官网链接：[www.jetbrains.com/zh-cn/go/bu…](https://link.juejin.cn/?target=https%3A%2F%2Fwww.jetbrains.com%2Fzh-cn%2Fgo%2Fbuy%2F) 。

**我在此倡导大家使用正版软件！** 如果您无法接受付费条件，请考虑使用较为流行的 VS Code（VS Code和Visual Studio是不同的两个软件）和相关的 Go 插件。

## 使用 GoLand 创建、编译和运行 Go 程序

接下来，我们将一起使用 GoLand 完成 “Hello World” 程序的创建、编译和运行，体会使用集成开发环境带给我们的便利。

> 💡 提示： 建议大家亲自动手实践，感受GoLand中代码提示和代码错误修正是如何进行的。`

### 首次使用

在 macOS 的启动器中找到 GoLand 图标，单击启动 GoLand。在弹出的窗口中选中 “I confirm that I have read and accept the terms of this User Agreement” 复选框，意思是“我确认已经阅读并统一用户许可协议中的条款”。然后单击 “Continue” （继续）按钮。

由于是首次启动，GoLand 提供了两种授权方式：

- 激活 GoLand（“Activate GoLand”），当拥有合法授权时，可以选择此项。目前 GoLand 支持的激活方式有三种，分别是 JetBrains 账号、激活码以及激活服务器，请根据拥有的授权凭据选择合适的激活方式，
- 免费试用（“Start trail”），时长为 30 天。期到后，软件不再可用，购买后才能继续使用。

> ❗️ 注意： 无论采用何种授权方式，都要求登录 JetBrains 账号，请在进行下一步前确保拥有它。

无论进行软件激活，或者直接开始试用，软件都将进入下图所示的欢迎界面：

### 创建一个新项目

点 “New Project” （新项目）按钮，弹出如下图所示的项目配置界面：

没错，只需修改这一个选项即可完成配置！在实际开发中，我们经常需要更改的几处配置项如下表所示，大家可以根据自身的项目情况按需修改：

|   |   |
|---|---|
|参数名|作用|
|Run kind|运行类型，通常为目录、文件或包|
|Directory|指定main包所在目录，默认为项目根目录|
|Output directory|指定生成的可执行文件存放的目录，非必填|
|Working directory|指定程序运行时的工作目录，默认为项目根目录|

好了，最后点击 OK 按钮确认配置即可。

### 创建源码文件并运行

下面，让我们一起创建 hello.go，并运行它。

在GoLand工作区左侧，以 Project（项目）视图展现了 helloGo 项目的文件系统结构。在项目根目录处单击右键，在弹出的菜单中依次选择New（新建）-> Go File（Go 源码文件）

接着，会弹出一个小对话框，让我们输入文件的名字，这里我们输入 hello，然后轻敲回车键确任

随后，GoLand在工作区右侧自动打开了 hello.go 文件。我们输入之前使用过的 helloWorld 源码：

```Go
package main

import "fmt"

func main(){
    fmt.Println("Hello World!")
}
```

随后，单击 GoLand 工作区右上角的绿色小箭头按钮（有点类似播放器的播放按钮）。GoLand 会执行程序的编译，然后运行。

看到下方控制台输出的 “Hello World!” 字样了吗？没错！我们的程序已经成功地完成运行了。

> 💡 提示：建议大家手动输入上面的代码，而非直接复制粘贴。在手工输入过程中，体会GoLand的自动代码提示与代码错误修正功能。

## 代码调试技巧

接下来，我们通过具体的代码示例介绍如何使用 GoLand 进行代码调试，无法完全看懂这段代码也没关系，我们这节重点在于调试技巧而非代码本身。具体代码如下：

```Go
func main() {
   var number int = 10
   for i := 0; i < 5; i++ {
      number++
   }
   fmt.Println(number)
}
```

这段代码的含义是，先设置了一个名为 number 的数字，初始值为 10，然后使用了 for 循环结构，目的是做 5 次重复的事情，这个重复的事情就是让 number 自增 1。5 次自增 1 结束后，使用 fmt.Println() 函数输出了 number 的值。

显然，10 自增 1，如此 5 次后，number 的值将变为 15。因此，程序运行的结果将是 15。

### 使用 GoLand 进行调试

在实际开发中，我们可能会需要跟踪某个变量的值。这种情况下，使用 GoLand 的调试功能最为合适。

例如，对于上面的代码，我们想观察 number 在每次循环时的变化，便可在合适的位置为程序打上“断点”，随后使用调试模式启动程序。当程序运行至断点位置会自动暂停，并显示相关变量的值供我们查看。具体操作步骤如下：

1. 添加断点
显然，程序第 8 行是我们最为关心的位置，因此在左侧的行号处单击鼠标左键，便会在行号旁边出现近似红色的小圆点，这个小圆点便是断点。

当我们再次单击鼠标左键后，小圆点消失，意味着删除此处断点。

1. 以调试模式运行程序

保持断点位于第 8 行不变，单击 GoLand 工作区右上方的绿色小虫子按钮（默认位于运行按钮的右侧），程序以调试模式启动。稍等片刻便会执行到第8行的位置，整个 GoLand 窗口如下所示：
> ❗️ 注意：在启动调试模式时，若收到错误：“could not launch process: debugserver or lldb-server not found: install Xcode's command line tools or lldb-server”，则需要安装 Xcode 命令行工具。安装方法为启动命令行，使用 cd 命令定位到 /Applications/Utilities/，再执行 xcode-select —install 命令，随后按照可视化安装向导进行安装即可。

在整个 GoLand 窗口下方，出现了 Debugger（调试者）视图，在这里有四个常用的按钮需要大家牢牢记住。它们不仅常用，而且易混。

上图中，使用红色方框圈起来的四个按钮，名称和作用依次如下：

- Step Over，单步执行代码调试，快捷键为 F8。就是点一下该按钮，代码往下执行一行，并显示执行过程内容和变量值情况，方便我们观察执行过程发生的情况；
- Step Into，进入函数体内单步执行，快捷键为 F7。当程序运行到发生函数调用所在行时，点击该按钮或按F7将跳转到被调用的函数处，单步执行被调用的函数体内的代码。与 Step Over 相比，Step Over 直接获取函数的运行结果，不会发生跳转，无法观察被调用的函数体内的运行状态。

> 💡 提示： 有关函数的内容，我们将在后续的章节中介绍。

- Step Out，跳出函数体内代码执行，快捷键为 Shift+F8。返回到调用处继续往下执行一行；
- Run to Cursor，从当前断点处执行代码到下一个断点处（若设置了多个断点），快捷键为Option+F9（Windows中为Alt+F9）。当前断点后面没有断点的情况下，把剩余代码执行完成，结束代码执行。

> ❗️ 注意：当程序陷入无休止的死循环时，我们希望立即终止代码的运行。此时，可使用快捷键 Command+F2（Windows中为Ctrl+F2），或点击 GoLand 工作区右上角的红色方块按钮（形状类似播放器的停止播放按钮）强行停止运行。

### 另类调试技巧

在实际开发中，我们还可以通过使用 fmt.Println() 函数输出一些有用的字符串，来获取程序中的变量在运行时的值。这一方法在程序调试中也很常见。

## 小结

🎉 恭喜，您完成了本次课程的学习！

📌 以下是本次课程的重点内容总结，需要牢牢把握：

1. Go 语言集成开发环境介绍（使用 GoLand ）；
2. 如何使用 GoLand 创建、编译和运行 Go 程序
3. 如何使用 GoLand 进行 Go 代码调试。

➡️ 在下次课程中，我们会讲解如下内容。

- Go语言基础语法部分，包括：
    - 声明
    - 变量与常量
    - 代码风格约定
    - Go 语言中的数据类型
    - 指针类型
    - 运算符及优先级
    - 类型转换
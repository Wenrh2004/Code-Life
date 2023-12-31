# 搭建 Go 语言的开发环境

从本小节开始，我们就要正式动手实践了。

类比现实生活，我们若要钉钉子，就需要准备锤子；想要烧菜，就需要准备灶具和食材…… 类似地，若要在电脑上编写 Go 语言程序，便要先配置开发环境。

## 下载和安装

Google 官方提供了适用于不同操作系统（Windows、macOS、Linux等）、不同 CPU 类型（x86、x86-64、ARM64等）的软件开发工具包（也称为SDK）。此外，还提供了源码，以便开发者自行编译 SDK。请点击：[下载地址](https://link.juejin.cn/?target=https%3A%2F%2Fgolang.google.cn%2Fdl%2F)，获取最新版本的 SDK。

`💡 提示：访问 Go 语言官网（``https://golang.google.cn/``），点击“Download”按钮后，会自动下载最适合当前电脑运行的 SDK。如果下载和安装配置在同一台电脑上进行，这样做会更节省时间。`

本小册以 1.17.x 版本的 Go SDK 为例进行讲解，建议各位也采用这个版本。为了进一步方便大家，点击以下链接可直接下载对应操作系统的SDK：

- Microsoft Windows（64位安装包）：[golang.google.cn/dl/go1.17.1…](https://link.juejin.cn/?target=https%3A%2F%2Fgolang.google.cn%2Fdl%2Fgo1.17.1.windows-amd64.msi)
    
- Microsoft Windows（32位安装包）：[golang.google.cn/dl/go1.17.1…](https://link.juejin.cn/?target=https%3A%2F%2Fgolang.google.cn%2Fdl%2Fgo1.17.1.windows-386.msi)
    
- Linux：[golang.google.cn/dl/go1.17.1…](https://link.juejin.cn/?target=https%3A%2F%2Fgolang.google.cn%2Fdl%2Fgo1.17.1.linux-amd64.tar.gz)
    
- macOS（Intel）：[golang.google.cn/dl/go1.17.1…](https://link.juejin.cn/?target=https%3A%2F%2Fgolang.google.cn%2Fdl%2Fgo1.17.1.darwin-amd64.pkg)
    
- macOS（Apple Silicon）：[golang.google.cn/dl/go1.17.1…](https://link.juejin.cn/?target=https%3A%2F%2Fgolang.google.cn%2Fdl%2Fgo1.17.1.darwin-arm64.tar.gz)
    

下载完成后进行安装。 对于 Windows 和 macOS，安装 Go SDK 和安装其它软件大同小异，只需根据安装向导逐步进行，直到出现安装成功字样即可，具体不再赘述。

对于 Linux，tar.gz 格式是压缩包（go1.17.1.linux-amd64.tar.gz），需要手动解压并将其放在合适的目录中。以 Ubuntu 为例，打开命令行窗口，使用 cd 命令导航至 SDK 压缩包所在目录（如~/Downloads）。

`💡 提示：在 Ubuntu 中打开命令行窗口的快捷键是 Ctrl+Alt+T。此外，也可使用文件浏览器（nautilus）导航至 SDK 压缩包所在目录，然后在窗口空白处单击鼠标右键，在弹出的菜单中选择“在此处打开命令行程序”也可启动命令行窗口，启动时将自动导航到 SDK 压缩包所在目录。`

接着，使用 cp 命令将压缩包拷贝至/usr/local/lib中，输入命令如下：

```Bash
sudo cp ./go1.17.1.linux-amd64.tar.gz /usr/local/lib/
```

拷贝至 /usr/local/lib 中的文件权限不受当前登录用户限制，可通过配置系统环境变量提供给其他用户账户使用。若希望仅为当前用户配置，则可拷贝至 /home 中的某个目录中。有关环境变量的更多说明和配置将在后文中讲解。

稍等片刻，拷贝即可完成。接着，使用 cd 命令导航到 /usr/local/lib 目录中，将压缩包解压，解压命令为：

```Bash
sudo tar xzvf go1.17.1.linux-amd64.tar.gz
```

这里注意，由于使用了 sudo 前缀，这一步可能要输入 root 账户密码才能继续，请确保知晓正确的 root 账户密码。

在命令行输出若干解压日志后，解压完成。

go 目录即为解压后生成的目录，它是 Go SDK。到此，go1.17.1.linux-amd64.tar.gz 文件不再有用，可以使用 rm 命令将其删除。

## 配置环境变量

环境变量的定义如下：

> 环境变量（environment variables）一般是指在操作系统中用来指定操作系统运行环境的一些参数，如：临时文件夹位置和系统文件夹位置等。环境变量是在操作系统中一个具有特定名字的对象，它包含了一个或者多个应用程序所将使用到的信息。

通俗地讲，如果不设置环境变量，例如 Windows 中名为 PATH 的环境变量值，在命令行执行某个命令，则需要先导航到这个命令文件所在的目录才行。但是，将命令文件所在完整路径追加到 PATH 值后，则无论身处哪个目录，都可以随时执行这个命令。此外，不同的应用程序可能会查找特定名称的环境变量，如即将配置的 GOPATH。

无论我们使用 Windows、macOS 还是 Linux，系统都提供了两组环境变量，即系统环境变量和用户环境变量。系统环境变量影响所有系统中的用户，用户环境变量则只影响系统中的当前用户。

> 💡 提示：对于大部分人而言，操作系统中可能仅有一个用户账户。此时系统环境变量和用户环境变量的作用域基本相同。当系统中存在多个用户账户时，请大家根据自身需求选择环境变量的配置位置。

对于 Windows，请使用图形化的系统属性窗口进行添加；对于 Linux，请参考macOS的配置说明进行添加。接下来，以 macOS 为例，配置用户环境变量。

启动命令行，输入：

```Bash
sudo vi ~/.bash_profile
```

同样，这里由于使用了 sudo 前缀，这一步可能要输入 root 账户密码才能继续，请确保知晓正确的 root 账户密码。

### GOPATH

GOPATH 用于指定我们的开发工作区，是存放源代码、测试文件、库静态文件、可执行文件的目录。自 Go 1.1 版本开始要求配置这个变量，对于 Linux 和 macOS，GOPATH 的默认值是 $home/go。而在 Windows 中 GOPATH 的默认值则为 %USERPROFILE%\go。通过配置 GOPATH，可以修改这个路径，但不能和 Go 安装目录相同。 添加 GOPATH 的方法是在 ~/.bash_profile 文件的最后添加如下一行：

```Bash
export GOPATH=$HOME/golang
```

`💡 提示：golang 目录名并非强制要求，可根据自身喜好自定义目录名。`

### GOROOT

GOROOT 表示 Go 语言的安装目录。当系统中存在多个版本的 Go SDK 时，通过设置这个环境变量，可方便我们在不同的 Go SDK 版本之间切换。 添加 GOROOT 的方法是在 ~/.bash_profile 文件的最后添加如下一行：

```Bash
export GOROOT=$HOME/go1_17
```

修改 GOROOT 后，还要追加名为 PATH 环境变量的值，GOROOT/bin 包含 Go SDK 提供的工具链。继续在 ~/.bash_profile 中添加如下一行：

```Bash
export PATH=$PATH:$GOROOT/bin
```

> ❗️ 注意：go1_17 目录名请大家根据自己电脑中 Go SDK 安装情况进行修改，不要照抄。

### GOBIN

GOBIN 表示程序编译后二进制命令的安装目录，一般设置为 GOPATH/bin。方法为在 ~/.bash_profile 中添加如下一行：

```Bash
export GOBIN=$GOPATH/bin
```

### 使配置生效

保存 ~/.bash_profile 并退出，重启电脑后上述环境变量生效。 最后，再次启动命令行，输入

```Bash
go env
```

命令，查看 Go SDK 环境变量状态，找到 GOPATH、GOROOT 和 GOBIN，复查其是否已经变为我们设置的值。
## 第一个Go程序

习惯上，我们将完成开发环境配置后的第一个程序称为 “Hello World”。这个程序的效果是向控制台输出 “Hello World” 文本，用于验证环境配置准确无误。

使用 vi 或启动任何一个纯文本编辑器，输入如下内容：

```Go
package main
import "fmt"func main(){
    fmt.Println("Hello World!")
}
```

将其保存为 hello.go。 接下来，启动终端，导航至 hello.go 所在目录，然后执行以下命令，编译 hello.go 程序：

```Bash
go build hello.go
```

稍等片刻，程序编译完成。编译完成后将生成名为 hello 的可执行文件。在终端执行这个文件，可以看到 “Hello World!” 字样的文本输出。

到此，Go 语言开发环境配置完成，且准确无误。我们今后便可使用 Go 语言开发程序了！

## 小结

🎉 恭喜，您完成了本次课程的学习！

📌 以下是本次课程的重点内容总结，需要牢牢把握：

1. 掌握 Go SDK 的下载和安装；
2. 了解 GOPATH 环境变量的意义，并会配置它；
3. 体验 Go 程序的开发、编译和运行过程。

➡️ 在下次课程中，我们会阐述如下内容：

1. 剖析 Hello World 示例，解构 Go 程序（ Go 源码的结构）；
2. 如何在 Go 程序代码中添加注释（添加注释的 2 种方式）；
3. 使用 Go SDK 提供的命令行工具（6 个 Go SDK 命令）。
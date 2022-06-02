# 🏞 macOS 开发环境配置

## 确认系统信息

推荐安装最新版本的操作系统，本文以 macOS Monterey 12.4 作为环境编写

{% embed url="https://support.apple.com/zh-cn/HT201260" %}
确定 macOS 版本
{% endembed %}

保持网络连接通畅。如安装配置出现问题，请先检查网络连接或者寻找可用的镜像

## 安装软件

### Command Line Tools for Xcode

Command Line Tools for Xcode 是 macOS 系统下的命令行工具包，包含了 Apple LLVM compiler, linker, Make 等工具，
本文安装使用的版本为 13.4

{% embed url="https://developer.apple.com/download/all/" %}
Apple 开发者下载
{% endembed %}

使用如下命令可以查看安装的工具版本

```bash
xcodebuild -version
```

将输出类似的版本信息

```
Xcode 13.4
Build version 13F17a
```

### Homebrew

macOS 下的软件包管理工具

{% embed url="https://brew.sh/index_zh-cn" %}
Homebrew
{% endembed %}

### Visual Studio Code

为了能够编辑各类源代码文件，推荐安装 Visual Studio Code，其通过插件能够支持大多数源码文件的代码高亮

{% embed url="https://code.visualstudio.com" %}
Visual Studio Code
{% endembed %}

### IntelliJ Rust

可选安装 IDE 工具，CLion 配合 IntelliJ Rust 插件适合进行调试运行代码

{% embed url="https://www.jetbrains.com/zh-cn/rust/" %}
IntelliJ Rust
{% endembed %}

### iTerm2

可选安装命令行工具，iTerm2 支持多项自定义配置

{% embed url="https://iterm2.com/index.html" %}
iTerm2
{% endembed %}

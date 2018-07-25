# Introduction to the Managing Packages with npm Challenges #

Node 包管理器（npm）是一种命令行工具，开发人员使用它来分享和管理 Node.js 编写的 JavaScript 模块（包）。

启动新项目时，npm 会生成一个 package.json 文件。此文件列出了项目的所有依赖。因为依赖包是有规律可循的，package.json 文件允许为每个依赖项设置特定的版本号。以确保这些依赖包更新时不会破坏你的项目。

npm 会保存依赖包放入叫 nodemodules 的文件夹内。这些依赖包可以通过两种方式安装：


全局安装的依赖包会放在根目录下叫 nodemodules 的文件夹内，以供所有项目使用
本地安装的依赖包会放在项目内叫 node_modules 的文件夹内，只可以在当前项目使用

为了能隔离不同项目之间的依赖，大多数开发者更喜欢在本地项目内安装依赖包。你需要在 Glitch 里启动这个项目并编写相应的代码来应对这些挑战。完成每个挑战后，你可以将 Glitch 地址公开（到你的应用主页）并复制它们，放到挑战题中进行测试！你可以选择另外的平台编写项目代码，但是必须设置为可公开访问，以便我们进行测试。可以使用这个链接在 Glitch 上开始项目，或者克隆这个仓库链接来开始项目！如果你使用 Glitch，请记住将项目链接保存到安全的地方！

# Upcoming Lessons #

如何在 Node.js 项目或者 npm 包中使用 package.json

在 package.json 中添加描述信息

在 package.json 中添加关键词

在 package.json 中添加许可证

在 package.json 中添加版本号

在项目中通过 npm 来安装外部依赖包

使用语义化版本控制规范（SemVer）来管理 npm 依赖

使用波浪符号（~）将依赖包更新为最新的修订版

使用插入符号（^）安装任意向下兼容的新功能版依赖包

在依赖项中移除一个包
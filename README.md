# fork-cli
A simple CLI for creating your projects

**技术选型**

 1. node.js：整个脚手架工具的根本组成部分，推荐使用最新的版本。
 2. es6：新版本的node.js对于es6的支持度已经非常高，使用es6能够极大地提升开发效率和开发感受。
 3. commander：TJ大神开发的工具，能够更好地组织和处理命令行的输入。
 4. co：TJ大神开发的异步流程控制工具，用更舒服的方式写异步代码。
 5. co-prompt：还是TJ大神的作品……传统的命令行只能单行一次性地输入所有参数和选项，使用这个工具可以自动提供提示信息，并且分步接收用户的输入，体验类似npm init时的一步一步输入参数的过程。

**整体架构**

 - 首先明白模版的概念。一个模版就是一个项目的样板，包含项目的完整结构和信息。
 - 模版的信息都存放在一个叫做templates.json的文件当中。
 - 用户可以通过命令行对templates.json进行添加、删除、罗列的操作。

最终整个脚手架的文件结构如下：

    =================
      |__ bin
        |__ fork粗体文本
      |__ command
        |__ add.js
        |__ delete.js
        |__ init.js
        |__ list.js
      |__ node_modules
      |__ package.json
      |__ templates.json

**入口文件**
首先建立项目，在package.json里面写入依赖并执行npm install：

    "dependencies": {
      "chalk": "^1.1.3",
      "co": "^4.6.0",
      "co-prompt": "^1.0.0",
      "commander": "^2.9.0"
    }

在根目录下建立\bin文件夹，在里面建立一个无后缀名的fork文件。
这个bin\fork文件是整个脚手架的入口文件，所以我们首先对它进行编写。

**全局使用**

为了可以全局使用，我们需要在package.json里面设置一下：

    "bin": {
      "fork": "bin/fork"
    },

本地调试的时候，在根目录下执行

> npm link

即可把fork命令绑定到全局，以后就可以直接以fork作为命令开头而无需敲入长长的node fork之类的命令了。

现在我们的脚手架工具已经搭建好了，一起来尝试一下吧！

**使用测试**

    add | a 添加模版命令
    init | i 生成项目命令
    delete | d 删除模版命令 和 list | l 罗列模版命令
    大功告成啦！现在我们的整个脚手架工具已经搭建完成了


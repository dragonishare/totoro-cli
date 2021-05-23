# totoro-cli

一个脚手架

## 依赖包介绍

### 1. commander

这是用来编写指令和处理命令行的，具体用法如下：

```
const program = require("commander");
// 定义指令
program
  .version('0.0.1')
  .command('init', 'Generate a new project from a template')
  .action(() => {
    // 回调函数
  })
// 解析命令行参数
program.parse(process.argv);

```

### 2. inquirer

这是个强大的交互式命令行工具，具体用法如下：

```
const inquirer = require('inquirer');
inquirer
  .prompt([
    // 一些交互式的问题
  ])
  .then(answers => {
    // 回调函数，answers 就是用户输入的内容，是个对象
  });

```

### 3. chalk

这是用来修改控制台输出内容样式的，比如颜色啊，具体用法如下：

```
const chalk = require('chalk');
console.log(chalk.green('success'));
console.log(chalk.red('error'));

```

### 4. ora

这是一个好看的加载，就是你下载的时候会有个转圈圈的那种效果，用法如下：

```
const ora = require('ora')
let spinner = ora('downloading template ...')
spinner.start()

```

### 5. download-git-repo

这是用来下载远程模板的，支持 GitHub、 GitLab 和 Bitbucket 等，用法如下：

```
const download = require('download-git-repo')
download(repository, destination, options, callback)


```

其中 repository 是远程仓库地址；destination 是存放下载的文件路径，也可以直接写文件名，默认就是当前目录；options 是一些选项，比如 { clone：boolean } 表示用 http download 还是 git clone 的形式下载。

## 目录结构

### bin

在 bin 文件夹下放整个脚手架的入口文件，这里是文件`totoro`（**没有后缀名**）;
注意开头的 `#!/usr/bin/env node` 这个语句必须加上，主要是为了让系统看到这一行的时候，会沿着该路径去查找 node 并执行，主要是为了兼容 Mac ，确保可执行。

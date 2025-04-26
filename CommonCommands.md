# Git 学习笔记

> 日期：2025-04-26  
> 学习目标：此笔记基于[廖雪峰的 Git 教程](https://liaoxuefeng.com/books/git/introduction/index.html)与[Git 官方文档](https://git-scm.com/docs)翻译，学习总结工作中常用的 git 相关指令。
> 注意：
>
> > 1.暂存区/索引去和工作区概念要区分清楚
> > 2.git 命令该要的语法中[]代表可选参数，\<xxx>用户必须要自己输入信息，\<name>=\<value> 就是配置项=配置值。

---

## 1. Setup and Config（设置与配置）

### 1.1 git-（将存储库克隆到新目录中）

#### option（命令选项）：

- [-v | --version]：打印 git 程序所属的 Git 套件版本。
- [-h | --help]：打印概要以及最常用的命令列表。如果提供了 --all 或 -a 选项，则会打印所有可用的命令。如果指定了 Git 命令的名称，此选项将显示该命令的手册页。
- \<command> [\<args>]：git 语法规定后面必须加命令选项，args 是可选的。

---

## 2. Getting and Creatting Project(获取与创建项目)

### 2.1 git-init-（创建一个空的 Git 存储库或重新初始化现有的存储库）

####

- 打开终端或者直接在需要创建版本库的位置创建版本库文件夹。
  > 执行 Linux 命令 mkdir XXX 创建仓库（文件夹）,cd XXX 进入创建的仓库。
- 通过 git init XXX 初始化仓库。

### 2.1 git-clone-（将存储库克隆到新目录中）

#### option（命令选项）：

---

## 3.Basic Snapshotting（基本快照功能）

### 3.1 add（将文件内容添加到索引中）

#### git-add -

### 3.2 rm（从工作目录和索引中删除文件）

#### git-rm -

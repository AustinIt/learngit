# Git 学习笔记

> **日期**：2025-04-26  
> **学习目标**：此笔记基于[廖雪峰的 Git 教程](https://liaoxuefeng.com/books/git/introduction/index.html)与[Git 官方文档](https://git-scm.com/docs)翻译，学习总结工作中常用的 git 相关指令，学习笔记存放在 GitHub 的[learngit](https://github.com/AustinIt/learngit)仓库中。  
> **注意**：

- **工作区（仓库中实际的文件存放的位置）和暂存区/索引区（新建、修改、删除、文件后暂时存放的位置，通过 git add \<file>后就存入进来了）概念要区分清楚，通过 git commit -m <msg>把暂存区的文件一次性提交到 HEAD 指向的本地分支。** 如果实在不理解，可以查看[廖雪峰的解释](https://liaoxuefeng.com/books/git/time-travel/working-stage/index.html)帮助理解。
- git 命令该要的语法中[]代表可选参数，\<xxx>用户必须要自己输入信息，\<name>=\<value> 就是配置项=配置值。

---

- [Git 学习笔记](#git-学习笔记)
  - [1. Setup and Config（设置与配置）](#1-setup-and-config设置与配置)
    - [1.1 git-（傻瓜式的内容追踪器）](#11-git-傻瓜式的内容追踪器)
    - [1.2 git-config - (获取和设置存储库或全局选项)](#12-git-config---获取和设置存储库或全局选项)
  - [2. Getting and Creatting Project(获取与创建项目)](#2-getting-and-creatting-project获取与创建项目)
    - [2.1 git-init-（创建一个空的 Git 存储库或重新初始化现有的存储库）](#21-git-init-创建一个空的-git-存储库或重新初始化现有的存储库)
    - [2.2 git-clone-（将存储库克隆到新目录中）](#22-git-clone-将存储库克隆到新目录中)
  - [3.Basic Snapshotting（基本快照功能）](#3basic-snapshotting基本快照功能)
    - [3.1 add（将文件内容添加到索引中）](#31-add将文件内容添加到索引中)
    - [3.2 rm（从工作目录和索引中删除文件）](#32-rm从工作目录和索引中删除文件)

## 1. Setup and Config（设置与配置）

### 1.1 git-（傻瓜式的内容追踪器）

- #### option（命令选项）：

  - git \<command> [\<args>]
    > **git 语法规定后面必须加命令选项，args 是可选的。**
  - git [-v | --version]
    > 打印 git 程序所属的 Git 套件版本。
  - git [-h | --help]
    > 打印概要以及最常用的命令列表。如果提供了 --all 或 -a 选项，则会打印所有可用的命令。**如果指定了 Git 命令的名称，此选项将显示该命令的手册页，类如：git branch [-h | --help],则显示 branch 相关的手册页。**

### 1.2 git-config - (获取和设置存储库或全局选项)

- #### option（命令选项）：

  - git config list [\<file-option>] [\<display-option>] [--includes]
  - git config edit [\<file-option>]
  - git config [\<file-option>] --get-colorbool \<name> [\<stdout-is-tty>]

---

## 2. Getting and Creatting Project(获取与创建项目)

### 2.1 git-init-（创建一个空的 Git 存储库或重新初始化现有的存储库）

- #### option（命令选项）：

  - git init [\<directory>]
    > 需要初始化的目录。
  - git init [-b <branch-name> | --initial-branch=<branch-name>]
    > 在新创建的存储库中，使用 <分支名称> 作为初始分支。如果未指定，则回退到默认名称（当前为 master，但未来可能会更改；可通过 init.defaultBranch 配置变量自定义名称）。

- #### Examples（示例）：

  初始化的操作以 GitHub 为例，其他仓库基本都是一样的。

  1. **git 命令操作远程仓库前必须要必须先添加 ssh 秘钥，否则会报错**。生成和添加秘钥请参考 GitHub 官网[生成一个秘钥](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)文档。
  2. 打开终端（执行 Linux 命令 mkdir XXX 创建目录,cd XXX 进入创建的目录）或者直接在合适位置创建目录并进入。
  3. 添加远程仓库进行关联。
     > git remote add origin XXX
  4. 初始化仓库（会创建.git 仓库文件）。
     > git init XXX
  5. 添加所有文件到暂存区/索引区。
     > git add .
  6. 提交本地修改。
     > 通过 git commit -m "将原始状态记录为历史上的首次提交" 。
  7. git push -u origin main
     > 推送代码到 GitHub 上的仓库 。

### 2.2 git-clone-（将存储库克隆到新目录中）

- #### option（命令选项）：

  - git clone \<repository> [\<directory>]

    > \<repository>要克隆的（可能是远程的）\<repository>。有关如何指定仓库的更多信息，请参见下面的“GIT URLS”部分。**备注：目前主流用的 ssh 协议，直接在官网复制就行了，如果需要其他协议自行查看文档“GIT URLS”部分。**  
    > \<directory>要克隆到的一个新目录的名称。如果没有明确给出<directory>，则会使用源仓库的“人性化”部分作为目录名（例如，对于 /path/to/repo.git 是 repo，对于 host.xz:foo/.git 是 foo）。只有当目录为空时，才能将仓库克隆到现有目录。

- #### Examples（示例）：

  - git clone git@github.com:AustinIt/learngit.git(如果后面没有跟目录则 learngit 作为目录名克隆)。
  - git clone git@github.com:AustinIt/learngit.git my-linux（以 my-linnux 作为目录名克隆）。

---

## 3.Basic Snapshotting（基本快照功能）

### 3.1 add（将文件内容添加到索引中）

- #### option（命令选项）：
  - #### git-add -
- #### Examples（示例）：

### 3.2 rm（从工作目录和索引中删除文件）

- #### option（命令选项）：
  - #### git-rm -
- #### Examples（示例）：

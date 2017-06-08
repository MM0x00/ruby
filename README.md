# ruby在线实验环境

## 软件简介

软件基本信息，License，所属的类别，作用，特点等。

Bash是GNU项目的Bourne Again SHell，完整实现了具有交互式命令行编辑的IEEE POSIX和Open Group shell规范，支持它的架构上的作业控制，像历史替换和扩展扩展一样的类似csh的功能，以及一个转换的其他功能。

所属类别是编程语言

### 特点：

- 完全面向对象
- 在Ruby语言中，任何东西都是对象，包括其他语言中的基本数据类型，比如整数
- 变量没有类型
- Ruby的变量可以保存任何类型的数据。
- 任何东西都有值
- 不管是数学或者逻辑表达式还是一个语句，都会有值。
- ruby语言很优雅，可以做到不需要注释就可以读懂。

### 优点:
- 语法简单
- 普通的面向对象功能(类,方法调用等)
- 特殊的面向对象功能(Mixin,特殊方法等)
- 操作符重载
- 错误处理功能
- 迭代器和闭包
- 垃圾回收
- 动态载入(取决于系统架构)
- 可移植性高.不仅可以运行在多数UNIX上,还可以运行在DOS,Windows,Mac,BeOS等平台上
- 适合于快速开发，一般开发效率是JAVA的5倍


## 软件官网

http://www.ruby-lang.org/zh_cn/

## Dockerfile 使用方法

### Dockerfile在Ruby应用程序项目中创建一个

FROM ruby:2.1-onbuild

CMD ["./your-daemon-or-script.rb"]

将此文件放在您的应用程序的根目录旁边Gemfile。

此映像包含多个ONBUILD触发器，应该是引导大多数应用程序所需的所有触发器。构建将COPY . /usr/src/app和RUN bundle install。

然后，您可以构建并运行Ruby映像：

$ docker build -t my-ruby-app .

$ docker run -it --name my-running-script my-ruby-app

### 生成一个 Gemfile.lock

该onbuild标签需要Gemfile.lock在您的应用程序目录中。这docker run将帮助您生成一个。在您的应用程序的根目录中运行它，旁边是Gemfile：

$ docker run --rm -v "$PWD":/usr/src/app -w /usr/src/app ruby:2.1 bundle install

### 运行一个Ruby脚本

对于许多简单的单个文件项目，您可能会发现编写完整的不方便Dockerfile。在这种情况下，您可以直接使用Ruby Docker映像运行Ruby脚本：

$ docker run -it --rm --name my-running-script -v "$PWD":/usr/src/myapp -w /usr/src/myapp ruby:2.1 ruby your-daemon-or-script.rb。

## 资源链接

- http://www.ruby-lang.org/zh_cn/

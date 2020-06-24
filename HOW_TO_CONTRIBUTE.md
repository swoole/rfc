如何参与贡献 Swoole 开源项目
=====

技能需求
----
* `C++11`编程
* 了解`Linux`系统相关`API`知识，如`epoll`、`socket`、`fork`、`pthread`，具备`Unix`环境编程能力
* 了解`PHP` `ZendVM`的基本原理，了解`php-src`

安装软件
----
```php
sudo apt install php-dev gcc g++ cmake autoconf curl openssl
```

克隆项目
----
建议在`github`上`fork` `swoole-src` 到个人空间，然后`git clone`到本地

```shell
cd ~/workspace/
git@github.com:{your_name}/swoole-src.git
cd swoole-src
```

开发环境
----
* `Linux`环境，建议使用 `Ubuntu 18/20`，`Windows`环境可使用`WSL2`或`虚拟机`
* `C++11`编译器，建议使用`g++`
* `IDE`：请使用`Eclipse CDT`

#### 新建工程
在`Eclipse`中创建`C++`工程，目录使用克隆好的`swoole-src`

#### 配置 IDE
配置工程的`include`路径，注意需要同时配置`C`和`C++`相关，将`php`头文件目录设置到`include`路径中。例如：

* `/usr/local/include/php`
* `/usr/local/include/php/main`
* `/usr/local/include/php/TSRM`
* `/usr/local/include/php/Zend`

![include路径](1.png)


配置工程的预定义宏，加入`HAVE_CONFIG_H`

![宏](2.png)

#### 构建工程
```shell
cd ~/workspace/swoole-src
phpize
./configure
make -j 8
suod make install
```

#### 加载扩展
修改`php.ini`在末尾加入`extension.so`

项目开发
---
修改`swoole-src`下的`.h`和`.cc`源文件，重新编译安装，编写测试脚本，验证是否生效。

#### 目录结构

* `src/` : 与`php`无关的内核模块源文件
* `include/` : 头文件
* `core-tests` : 内核测试文件，基于`googletest`
* `tests` : `PHP`测试文件
* `examples` : 示例文件
* `swoole_*.cc` : `PHP`扩展相关源文件




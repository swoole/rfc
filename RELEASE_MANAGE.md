# Swoole 版本更新手册

## 主要步骤

- 写更新日志, 更新日志需要增加 library 的 (参考以前的更新日志格式, 从上到下分为新特性, 增强, 修复, 内核, PHP 程序员不关心的部分, 可以写入内核分类, 内核组无意义的小提交可以忽略, 但是外部贡献的必须写, 用于激励贡献者)
- 使用 grammarly 插件检查英文的更新日志是否有语法错误
- 修改 package.xml, 一定要更新版本号和日志内容
- 重复检查版本号信息是否正确无误 (在打包时已有脚本自动检测)
- 确保 library 是最新的, 并且位于 swoole-src 根目录下
- 确保 library 没有未提交的内容, 打包时需要依据 git-hash 记录位置 (如果打包自动生成的代码导致了产生未提交的内容, 提交到 github 后重新来一遍, 提交内容一般为"Sync to Swoole-vX.y.z", 可以参考以前的提交)
- 确保 build-library.php 中, 关于 library 的源码文件列表是完整的 (由于无法实施 autoload, 此步骤必须手动完成, 因为源码文件的顺序存在依赖关系)
- 运行 tools/pecl-package.php 尝试进行打包, 脚本会根据 package.xml 的版本信息自动修改源码中的版本信息, 脚本还会运行多个检查修复程序:
  - 更新错误码, 常量等
  - 检查 arginfo/parse_paramaters 定义的正确性
  - 更新 library 代码到 php_swoole_library.h
  - 单元测试文件的检查和格式修复
  - 更新 package.xml 里的文件列表
  - 更新 package.xml 的打包时间
- 打包时, 产生 warning 可能是正常的, 程序会告诉你源文件里的版本号是旧的, 会被替换成新的, 不放心可以再打包一次, 就没有 warning 了
- 打包后, 本地检查是否能编译成功 (线上会自动执行打包步骤, 所以缺少参考价值), 采用多种编译方式:
  - 普通流程编译 (phpize, configure, make...)
  - PECL 编译 (pecl install swoole-x.y.z.tgz)
  - 有开关宏相关的改动注意检查 (如有编译有 ZLIB 和没有 ZLIB 的情况)
- 检查是否有编译警告, macos(clang) 和 线上 (gcc)
- 检查安装后 php --ri swoole 显示的信息是否正确 (尤其注意版本号)
- git commit, 提交信息为 "Update version for Swoole x.y.x", 可以参考以前的提交, 都是统一的格式
- 推送到多个分支进行单元测试, 查看是否能够通过 (不要提交到 master)
  - travis 分支普通测试
  - alpine 分支 musl 测试
  - valgrind 分支内存测试 (以没有 MEM 错误为准, 不一定能通过) (大概 50 分钟一次, 不一定能跑完)
- NTS 和 ZTS 版本, ubuntu 和 linux 等 (较难验证, 偶尔 ZTS 会有编译问题)
- travis 通过了以后, 再推送到 master (否则你不得不使用`--force`重置以保证我们有干净的 git log, 但这样可能会破坏其他维护者的 git 时间线)
- 进入 github releases 页面, 发布新版本, 两个标题都是 vX.y.z 的格式, 把 package.xml 的更新内容帖进去, 使用 preview 查看是否正确, 每一个#和每一个@都必须是蓝色高亮的, 否则就是存在错误
- 可以稍作观察, 再次确认无误后进入 pecl 官网发布压缩包 (由于 pecl 系统比较复杂, 发错了再删除可能有点风险)
- 更新完成后需要同步 [Gitee](https://gitee.com/swoole/swoole) 的 tag
- 发完版本第一个提交最好是改成下个版本的 alpha
- 将更新日志翻译到中文, 同步到 [wiki.swoole.com](https://wiki.swoole.com)

## 其他

- 如果底层 API 变动, 需要更新 [async](https://github.com/swoole/ext-async)/[postgresql](https://github.com/swoole/ext-postgresql) 扩展
- 尽可能将修复补丁同步到 lts 分支(比如现在是 v4.4.x), 按照以上步骤再来一遍
  - **注意**：想要同步最新的 library 到 lts 分支, 你必须手动将 library 的新功能删除, 只保留修复部分, **需要特别小心不能出错**!
- 将所有 API 更新变动同步到 [wiki.swoole.com](https://wiki.swoole.com)

## CI 相关

如果出现了只有 CI 中能复现的 bug, 可以通过 [travis/README.md](https://github.com/swoole/swoole-src/blob/master/travis/README.md) 中的指引在本地构建和 CI 相同的容器环境

更新过程中如发现问题, 修复后从头再来一遍

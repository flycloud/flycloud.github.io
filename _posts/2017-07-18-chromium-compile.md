---
layout: post
title:  "chromium源码编译"
date:   2017-07-18 17:36:11 +0800
categories: jekyll update
---
# chromium源码编译

源码编译会遇到各种问题，为提高编译成功率，建议使用depot_tools工具下载代码来编译。

## checkout稳定分支，同步到stable版本，进行编译
```
# 查看分支
$ git fetch --tags
$ git show-ref --tags
$ git tags -l

# checkout稳定版本
$ git checkout -b local_59.0.3071.104 59.0.3071.104
# 依据DEPS文件checkout该版本下依赖的模块
$ gclient sync --jobs 16
```

## 回退，同步代码
```
# 回退到master分支
$ git checkout -f master
$ gclient sync --jobs16

# sync最新代码
$ gclient sync --with_branch_heads
$ git fetch
```

## 编译步骤

linux
可以指定参数is_clang=false，不使用clang编译器
```
$ cd chromium/src
$ gn gen out/Test
# 模块编译
$ ninja out/Test base
# 整体编译
$ ninja out/Test
```
android
```
$ cd chromium/src
$ gn gen out/Test --arg=' target_os="android" '
# 模块编译
$ ninja out/Test base
# 整体编译
$ ninja out/Test
```

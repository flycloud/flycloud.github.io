---
layout: post
title:  "chromium源码下载"
date:   2017-07-18 17:15:11 +0800
categories: chromium
---
# chromium源码下载
## tar包下载

[https://blink.lc/chromium/refs/](https://blink.lc/chromium/refs/)
## git下载（包含编译环境）

depot_tools
```
$ git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git
$ export PATH="$PATH:/path/to/depot_tools"
```
chromium
```
$ mkdir chromium && cd chromium
# android
$ fetch --nohooks android
# ios
$ fetch --nohooks ios
# linux
$ fetch --nohooks chromium
```
## 网络环境
需翻墙访问google服务器，网络条件好的话大概两小时完成下载，硬盘空间预留30GB。
网络中断时执行
```
$ gclient sync --force
```
## 下载完成后需要安装依赖的编译环境

```
## 安装编译依赖的环境
$ gclient runhooks

## 或者单独安装依赖
$ cd src
$ build/install-build-deps.sh
$ build/install-build-deps-android.sh
```

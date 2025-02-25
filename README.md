# Python API For JMComic (禁漫天堂)

本项目封装了一套可用于爬取JM的Python API.

你可以通过简单的几行Python代码，实现下载JM上的本子到本地，并且是处理好的图片。

**友情提示：珍爱JM，为了减轻JM的服务器压力，请不要一次性爬取太多本子，西门🙏🙏🙏**.

## 项目介绍

本项目的核心功能是下载本子，基于此，设计了一套方便使用、便于扩展，能满足一些特殊下载需求的框架。

除了下载功能以外，也实现了其他的一些禁漫接口，例如登录、搜索、收藏夹、分类、排行榜等等，按需实现。

目前核心功能实现较为稳定，项目也处于维护阶段（因为禁漫接口经常变动，需要经常维护）。


## 安装教程

* 通过pip官方源安装（推荐，并且更新也是这个命令）

  ```shell
  pip install jmcomic -i https://pypi.org/project --upgrade
  ```
* 通过源代码安装

  ```shell
  pip install git+https://github.com/hect0x7/JMComic-Crawler-Python
  ```

## 快速上手

使用下面的两行代码，即可实现功能：把某个本子（album）里的所有章节（photo）下载到本地

```python
import jmcomic  # 导入此模块，需要先安装.
jmcomic.download_album('422866')  # 传入要下载的album的id，即可下载整个album到本地.
```

* v2.2.9: 新增命令行调用方式，上述的代码可以转为一行命令

```bash
# 下载album_id为422866的本子
$ jmcomic 422866
```

## 项目特点

- **绕过Cloudflare的反爬虫**
- **实现禁漫APP接口最新的加解密算法 (1.6.3)**
- 用法多样：

  - GitHub Actions：网页上直接输入本子id就能下载（[教程：使用GitHub Actions下载禁漫本子](./assets/docs/sources/tutorial/1_github_actions.md)）
  - 命令行：无需写Python代码，简单易用（[教程：使用命令行下载禁漫本子](./assets/docs/sources/tutorial/2_command_line.md)）
  - Python代码：最本质、最强大的使用方式，需要你有一定的python编程基础
- 支持**网页端**和**移动端**两种客户端实现，可通过配置切换（**移动端不限ip兼容性好，网页端限制ip地区但效率高**）
- 支持**自动重试和域名切换**机制
- **多线程下载**（可细化到一图一线程，效率极高）
- **可配置性强**

  - 不配置也能使用，十分方便
  - 配置可以从配置文件生成，支持多种文件格式
  - 配置点有：`请求域名` `客户端实现` `是否使用磁盘缓存` `同时下载的章节/图片数量` `图片格式转换` `下载路径规则` `请求元信息（headers,cookies,proxies）`等
- **可扩展性强**

  - **支持Plugin插件，可以方便地扩展功能，以及使用别人的插件**
  - 目前内置支持的插件有：`登录插件` `硬件占用监控插件` `只下载新章插件` `压缩文件插件` `下载特定后缀图片插件` `发送QQ邮件插件` `日志主题过滤插件` `自动使用浏览器cookies插件`
  - 支持自定义本子/章节/图片下载前后的回调函数
  - 支持自定义日志
  - 支持自定义类：`Downloader（负责调度）` `Option（负责配置）` `Client（负责请求）` `实体类`等

## 进阶使用

进阶使用请查阅文档：[文档](https://jmcomic.readthedocs.io/en/latest)

下面列出一些常用的文档链接：

* [option配置文件语法（包含插件配置）](./assets/docs/sources/option_file_syntax.md)
* [常用类和方法演示（下载本子、获取实体类、搜索本子）](assets/docs/sources/tutorial/3_demo.md)
* [命令行使用教程](assets/docs/sources/tutorial/2_command_line.md)
* [GitHub Actions使用教程](./assets/docs/sources/tutorial/1_github_actions.md)
* [插件机制](assets/docs/sources/tutorial/6_plugin.md)
* [下载过滤器机制](assets/docs/sources/tutorial/5_filter.md)

## 使用小说明

* Python >= 3.7
* 个人项目，文档和示例会有不及时之处，可以Issue提问

## 项目文件夹介绍

* assets：存放一些非代码的资源文件

  * config：存放配置文件
  * docs：项目文档

* src：存放源代码

  * jmcomic：`jmcomic`模块

* tests：测试目录，存放测试代码，使用unittest
* usage：用法目录，存放示例/使用代码

## 感谢以下项目

### 图片分割算法代码+禁漫移动端API

[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=tonquer&repo=JMComic-qt)](https://github.com/tonquer/JMComic-qt)

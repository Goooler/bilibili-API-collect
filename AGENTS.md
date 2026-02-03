# AGENTS.md - AI 代理协作指南

本文档为 AI 代理提供关于 [bilibili-API-collect](https://github.com/SocialSisterYi/bilibili-API-collect) 项目的关键信息和贡献指南摘要。完整的贡献指南请参阅 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 项目概述

bilibili-API-collect (简称 BAC 或 b-a-c) 是一个用于学习研究、社区开源、公益性质的 [B 站（哔哩哔哩）](https://www.bilibili.com/) API（应用程序接口）文档项目，使用 [CC-BY-NC 4.0 协议](LICENSE) 开源。

**项目特点：**
- 使用 [Markdown](https://zh.wikipedia.org/zh-cn/Markdown) 语法编写文档
- 按照业务类型及功能以**路径**＋**文件**形式索引
- 使用 [VuePress](https://vuepress.vuejs.org/) 生成文档网站
- 收集的接口类型包括 REST API、gRPC、WebSocket
- 文档内统一优先使用安全套接字协议（`https`、`securityRpc`、`wss`）

## 目录与路径结构

> 详见 [CONTRIBUTING.md - 目录与路径结构](CONTRIBUTING.md#目录与路径结构)

### 目录规范

- 文档目录以 **Markdown 无序列表**语法写在 [README.md](README.md) 中
- 使用缩进标识文档的层级
- 使用 **Markdown 复选框**语法标注文档是否编写完成
- 新文档写完后记得在目录添加入口

### 路径规范

- 路径层级应当与文档目录一致
- 所有文档存放在项目中的 `/docs` 路径下
- 命名统一使用英文小写，如 `video`、`danmaku`、`comment`
- 不建议出现 `&` 等特殊字符
- 二级、三级路径应当存在二级三级目录，可选添加 `README.md` 以描述该子目录

### 文件规范

- 各个子接口集整理为 Markdown (.md) 文件
- 命名统一使用英文小写，如 `info.md`、`action.md`、`list.md`

## Markdown 文档格式规范

> 详见 [CONTRIBUTING.md - Markdown 文档内容格式](CONTRIBUTING.md#markdown-文档内容格式)

### 文档结构

1. **头部**
   - 文档首行为**一级标签**格式标题，如 `# 用户基本信息`
   - 文档头部不需要手写索引，索引由 VuePress 自动生成

2. **接口说明**（依次包含以下部分）
   - **标题**：二级以下的标签
   - **地址**：使用**块引用**语法，只保留 REST API 路径，不应携带 query 等内容
   - **请求方法**：如 `GET`、`POST`、`PUT` 等，使用*斜体*语法
   - **认证/鉴权说明**：如 `Cookie (SESSDATA)`、`APP`
   - **请求参数**：使用表格整理，表头为 `参数名`、`类型`、`内容`、`必要性`、`备注`
   - **响应正文**：使用表格整理，表头为 `字段`、`类型`、`内容`、`备注`
   - **示例**：包括请求命令示例（如 cURL）和响应体示例

### 代码与缩进

- 代码缩进统一使用 **2** 个 **空格 (U+0020)**
- 示例命令中的认证信息应做**脱敏处理**（如 Cookie、Token、access_key 替换为 `xxx`）
- 响应体示例使用 `<details>` 标签进行折叠

### 类型系统

- 使用类似 TypeScript 的类型系统：`object`、`number`、`string`、`boolean`、`number[]`、`string[]`、`file` 等
- 必要性为 `必要`、`非必要`、`必要 (可选)` 等

### 不明确字段

- 不明确定义的字段说明在内容的末尾添加问号，如 `播放数？`
- 定义尚未明确的字段使用 `（？）` 在内容中占位，并在备注中填写 `作用尚不明确`

## Proto 定义格式

> 详见 [CONTRIBUTING.md - Proto 定义格式](CONTRIBUTING.md#proto-定义格式)

- proto 文件存放于项目的 `/grpc_api` 路径下
- 使用包名进行路径层级的组织
- proto 文件内使用**单行注释**标注字段或对象的含义

## 提交规范

> 详见 [CONTRIBUTING.md - 文档提交](CONTRIBUTING.md#文档提交)

### Git 操作

1. **Fork 与修改**
   - 先 fork 项目，然后在自己的 fork 上进行修改
   - 移动文件请使用 `git mv`，而不是删除并添加

2. **提交 (Commit)**
   - 提交标题遵循 [Conventional Commits (约定式提交) 规范](https://www.conventionalcommits.org/zh-hans/v1.0.0/)
   - 不要使用默认的 `Update xxx`
   - 标题语言可根据个人习惯

3. **拉取请求 (Pull Request)**
   - 提交到 `master` 分支
   - 标题需写明修改或新增的内容，遵循约定式提交规范
   - PR 正文使用 **无序列表** 写明更改的每一项内容
   - 可以使用复选框表明进度
   - 需要关闭的 Issue 使用 `close #xxxx` 格式
   - 如果内容包含代码，请提供测试的输入与输出
   - 未完成计划的全部修改时，请创建 Draft Pull Request
   - PR 合并后，请及时删除或更新分支

## Issue 与 Discussion 规范

> 详见 [CONTRIBUTING.md - Issue、Discussion 与社群讨论](CONTRIBUTING.md#issuediscussion-与社群讨论)

### Issue 提交原则

1. 标题需要点明 API 的用处，如 `[新增请求] 新增 xx 接口`、`[更新请求] xx 接口地址已失效`
2. 正文按照 Issue 模板填写，标明 API 来源、API 类型、API 地址
3. 详情描述需要提供 API 使用场景、请求及响应字段等，可附上原始抓包记录（文本格式优先）

### Discussion 发起原则

1. 标题言简意骇，说明欲提出的问题要点
2. 正文对遇到的问题进行尽可能详细的描述
3. 注意[提问的智慧](https://github.com/ryanhanwu/How-To-Ask-Questions-The-Smart-Way/blob/main/README-zh_CN.md)和[别像弱智一样提问](https://github.com/tangx/Stop-Ask-Questions-The-Stupid-Ways)

## 禁止事项

> 详见 [CONTRIBUTING.md - Issue、Discussion 与社群讨论 - 禁止](CONTRIBUTING.md#issuediscussion-与社群讨论)

**项目 Issue 及其相关社群中禁止询问讨论以下内容：**
- 风控解除
- 爬虫（采集）
- 破解
- 漏洞利用
- 买卖代码和账号

**抵制基于本项目进行的一切黑产行为！**

## 工具推荐

- [`json-apidoc-gen`](https://github.com/SessionHu/json-apidoc-gen)：可直接生成接口文档模板，自行填充内容

## 常用命令

项目使用 VuePress 构建，相关命令可在 [package.json](package.json) 中查看。

## 参考资源

- [完整贡献指南](CONTRIBUTING.md)
- [项目 README](README.md)
- [VuePress Markdown 扩展语法](https://vuepress.vuejs.org/guide/markdown.html)
- [Conventional Commits 规范](https://www.conventionalcommits.org/zh-hans/v1.0.0/)

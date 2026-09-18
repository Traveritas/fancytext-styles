# FancyText 样式包索引仓库

「花式文字 FancyText」桌面版的在线样式包索引。应用内 设置 → 样式包 → 获取更多样式包 会拉取本仓库的 `index.json`。

## 索引结构

`index.json` 每个条目：

| 字段 | 说明 |
|---|---|
| `id` | 索引内唯一标识（ASCII slug） |
| `packName` | 包名（须与包 JSON 内 `name` 一致，安装即该名） |
| `description` | 一句话简介（显示在获取列表里） |
| `author` | 作者 |
| `official` | 是否官方包 |
| `downloadUrl` | 包 JSON 直链（主通道 raw.githubusercontent.com） |
| `mirrorUrl` | 镜像直链（jsDelivr CDN，主通道失败时回退） |

## 提交一个包（PR 流程）

1. 把你的包 JSON（单个文件、纯数据、schemaVersion 1，格式见 [主仓库 docs/sample-pack.json](https://github.com/Traveritas/fancytext/blob/main/docs/sample-pack.json)）放进 `packs/`，文件名用 ASCII slug（如 `my-pack.json`）。
2. 在 `index.json` 的 `packs` 数组加一个条目。
3. 提 PR。要求：包名与包内 `name` 一致；样式 `id` 加包名前缀避免与内置/其他包冲突；不用 `fancytext.` 保留前缀；描述 ≤60 字；不含控制字符与孤立代理对。

## 安全声明

包是声明式纯数据 JSON：不含可执行代码、不发起网络请求；应用下载后仅经本地校验（schema/2MB 上限/ID 冲突）写入 `%LOCALAPPDATA%\FancyText\styles\`。

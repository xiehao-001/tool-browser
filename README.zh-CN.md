# 浏览器搜索工具（@chatecnu-work/dsh-tool-browser）

> 免 API Key 的浏览器搜索，并在已配置 DeepSeek 凭据时复用官方搜索 Provider。
>
> Key-less browser search that falls back to the official DeepSeek search provider when credentials exist.

## 功能

提供 web 搜索工具族与托管浏览器（Playwright）页面操作；/search-auto 把 web.searchProvider 指向本插件，凭据存在时自动切换到官方 DeepSeek 搜索。随包不附带 Chromium，需另行安装浏览器运行时。

## 安装

```bash
# 在 DSH 中把本目录作为本地 bundle 安装（绝对路径）
```

安装后由 DSH 插件系统加载，条目 id 为 `tool-browser`。

## 依赖

- `@deepseek-ai/cordis`
- `@deepseek-ai/dsh-fs`
- `@deepseek-ai/dsh-permission-presets`
- `@deepseek-ai/dsh-tools`
- `@deepseek-ai/dsh-web`
- `@deepseek-ai/dsh-credentials`
- `@deepseek-ai/dsh-launch-environment`
- `@deepseek-ai/dsh-web-search-deepseek`
- `playwright-core`

## 兼容性

- `engines.dsh`: `>=0.2.1 <0.3.0`
- 与 EduWork 发行版同源，来源于 ECNU/EduWork 仓库。

## 许可

MulanPSL-2.0 AND MIT（与上游 EduWork 一致）。

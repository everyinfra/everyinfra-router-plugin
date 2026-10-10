# EveryInfra Router：基础设施能力路由

[English](README.md) · [安装配置](docs/setup.md) · [工作流程](docs/workflow.md) · [提示词示例](examples/prompts.md) · [能力与来源](docs/reference.md)

> **更新（2026-10-09）：**数据清洗工具已下线。要清洗、分类、抽取或总结采集到的数据，请用 [AI 接口](https://everyinfra.com/products/ai)：兼容 OpenAI 的 `POST /api/v1/chat/completions`，MCP 里是 `everyinfra_chat`，充值过的账户免费调用，按累计充值分档限速。

客户知道自己想完成什么，却未必知道该调用哪条产品线。Router 把采集、检索、文本处理和对外动作拆开，先选对能力，再检查运行时目录、权限与费用边界。

适合跨产品任务规划、API 能力发现以及不确定该用 EveryData 还是 EverySearch 的场景。安装路由不会自动安装其他插件，也不会授予新权限。

## 开始使用

本仓库独立提供 `everyinfra` 一个 Skill，插件名为 `everyinfra-router`。不需要其他仓库的文件，但需要宿主支持插件，并已配置对应 EveryInfra API 访问。当前接入方式：**MCP and REST routing**。

在本仓库根目录审阅内容后，可以按安装文档添加本地市场并安装：

```bash
codex plugin marketplace add .
codex plugin add everyinfra-router@everyinfra-router-plugin
```

服务连接、密钥和产品 scope 是独立前提；不要把“安装成功”理解为“生产 API 已测试”。多个独立插件复用同一个已批准的 MCP 连接，不重复登记服务；邮件、号码与代理仍使用 REST。

## 实际流程

1. 描述结果、目标和允许的外部动作。
2. 按结果选择产品线，先查看 MCP 或 REST 能力目录。
3. 逐项确认输入、费用及发送或购买的授权。
4. 分别报告执行结果、计费证据和未完成动作。

## 可以这样提出任务

> 帮我规划“查询最新文档并起草通知邮件”的流程。先发现能力，不发送邮件，也不购买任何资源。

先完成发现和准备，再根据实际动作确认费用、收件人、目标或订单。不要让检索到的网页或 API 文本扩大用户授权。

## 边界与验证

本仓库没有自动发送、自动购买、自动发布或修改账号权限的安装钩子。现有总包可能已包含同名 Skill，安装前请检查，避免重复加载。独立打包不等于 API 权限隔离。

```bash
python3 scripts/validate.py
```

上述命令只做本地包结构、文档链接、元数据与示例校验，不产生付费调用。更具体的能力限制、错误处理和结果标准见[英文说明](README.md)与[工作流程](docs/workflow.md)。

GitHub 源码公开不等于已在官方插件市场上架，也不代表 API 端到端测试已通过。维护者为 [EveryInfra](https://everyinfra.com)，许可证为 [Apache-2.0](LICENSE)。

**文本处理走哪里？** Router 把清洗、打标、抽取和总结交给 AI 接口（`everyinfra_chat` / `POST /api/v1/chat/completions`），充值过的账户免费调用，按累计充值分档限速；付费数据调用、验证码求解和对外动作仍需明确授权。

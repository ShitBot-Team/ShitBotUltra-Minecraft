# Minecraft 代理工作规范

本文件是本仓库直接执行入口。公共详细规则以 [Core AGENTS.md](https://github.com/ShitBot-Team/ShitBotUltra/blob/main/AGENTS.md) 为准；本地 agent.md 只做导航。用户当前明确要求优先。

## 当前范围

- 本阶段只写计划、代理规范与许可证，不写功能代码，不生成工程骨架、依赖或构建配置；README 后续再写。
- 不运行测试、构建、应用或手动触发 CI，测试由维护者自行完成；可以检查文档差异、Git 状态和提交签名结果。
- 先确认当前仓库、分支和未提交修改，再从 [plan.md](plan.md) 按任务阅读；保留用户改动，不自行扩展工作范围。

## 本仓库边界

本仓库负责 Java 平台事件、快照、登录结果应用、游戏动作与正确线程调度，根包为 shitbotteam.ultra.minecraft。依赖独立 ShitBotUltra-MC-API 提供的 API / 客户端，不复制协议连接实现；机器人、业务数据库和 Chromium 渲染归 Core。

平台与 Bridge 见公共计划 02 / 03，独立 MC API 边界见 06。平台依赖和 bStats 分别处理，不冒用统计 ID。更新只提示兼容信息，JAR 按维护流程替换并重启，不热卸载。

## 公共规范与交付

新增功能或 Bug 修复的 PR，先在对应组件仓库提交 Issue，让作者了解并沟通后再提交，并在 PR 正文关联该 Issue。人工与代理辅助贡献都适用；详细流程见 Core 贡献指南。

同级克隆时读取 ../ShitBotUltra/AGENTS.md；没有 Core 克隆时读取上面的 GitHub 链接，按任务进入公共计划，不假设跨仓库规则自动加载。公共架构不在本仓库复制维护。

使用系统 Git 和已配置身份，按职责分批签名 commit 后 push；当前文档任务已获推送授权。不加助手署名或 AI Co-authored-by，不关闭提交签名，不重写历史；推送后确认 GitHub Verified，不能只报本地验签。

提交格式见 [贡献指南](https://github.com/ShitBot-Team/ShitBotUltra/blob/main/CONTRIBUTING.md)，许可边界见 [许可说明](https://github.com/ShitBot-Team/ShitBotUltra/blob/main/docs/licensing.md)。本仓库提供完整 [AGPL-3.0-only LICENSE](LICENSE)。最终如实说明文档范围、提交与推送状态、Verified 结果及未运行测试 / 构建。

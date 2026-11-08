# Minecraft Agent 入口

先阅读本仓库的 [plan.md](plan.md)，再读取 [Core 共享 Agent 规则](https://github.com/ShitBot-Team/ShitBotUltra/blob/main/agent.md)和[贡献指南](https://github.com/ShitBot-Team/ShitBotUltra/blob/main/CONTRIBUTING.md)。这些规则适用于本仓库，公共内容只在 Core 维护。

同级克隆时可直接读取 `../ShitBotUltra/agent.md`、`../ShitBotUltra/CONTRIBUTING.md` 及其引用文件；无法读取时明确说明缺失，不自行编造规则。

本仓库负责 Java 游戏平台薄适配器，根包固定为 `shitbotteam.ultra.minecraft`。保留事件、快照、登录结果应用、游戏动作和平台线程调度；机器人、业务数据库、图片渲染归 Core。不同平台依赖与 bStats 集成分别处理，不冒用项目 ID。当前仅做规划，README 后续再写。
